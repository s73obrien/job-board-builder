To build builder image:
```
docker build -f job-board-builder .
```

To run builder image:
```
docker run -t -d --name jbb -v $JB_ROOT:/root/Debian-Live-config/webconverger/chroot s73obrien/job-board-builder
```
where JB_ROOT points to the local repository containing the directory tree for the Job Board client (cloned from [here](https://github.com/s73obrien/webc))

Once docker container is launched, to build the client image
```
docker exec -w /root/Debian-Live-config/webconverger jbb make
```

To get image out of container:
```
docker cp jbb:/root/Debian-Live-config/webconverger/live-image-i386.hybrid.iso ./job-board-client.iso
```

To stop builder container:
```
docker stop jbb
```
