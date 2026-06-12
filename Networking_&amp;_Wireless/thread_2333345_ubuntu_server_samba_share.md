---
title: "ubuntu server samba share"
date: 2016-08-09
forum: Networking &amp; Wireless
---

### Post by shura30 on 2016-08-09
while setting up my shares from ubuntu server 16 I got into this situation:

I mount 2 partition coming off different disks, this is my fstab:

```
UUID=8cedecd9-1c22-4ebf-86fa-c1ab653e8f33 /home/storage ext4 defaults 0 0
UUID=8f190af3-ec23-43e2-9391-abfee82620ae /home/downloads ext4 defaults 0 0
```

I have rw access from CLI, these are permissions from ls:

```
drwxr-xr-x  3 microserver microserver  4096 Aug  8 23:12 storage
drwxr-xr-x  3 microserver microserver  4096 Aug  8 23:09 downloads
```

samba shares:

```
[microserver_share]
        path = /home/microserver/microserver_share
        browseable = yes
        writeable = yes
        valid users = microserver
        create mask = 0777
        directory mask = 0777

[downloads]
       copy = microserver_share
       path = /home/downloads

[storage]
       copy = microserver_share
       path = /home/storage


```

I log in from windows the user "microserver"
RW to 'microserver_share' but only read permissions to 'downloads' e 'storage'

If I change approach and mkdir sub-folders, one each partition and share them as:

```
[downloads]
       copy = microserver_share
       path = /home/downloads/downloads

[storage]
       copy = microserver_share
       path = /home/storage/storage

```

RW without issues
to my knowledge there is no functionality impact beside longer path but I can't undertand the scenario
is it mount or permission related?

---

