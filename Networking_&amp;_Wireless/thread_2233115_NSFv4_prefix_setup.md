---
title: "NSFv4 prefix setup"
date: 2014-07-06
forum: Networking &amp; Wireless
---

### Post by krichter722 on 2014-07-06
Hi together,
I'm having trouble setting up an NFSv4 export on Synology's DiskStationManager (DSM) 5.0 and Ubuntu 14.04. The problem is the error message 
```
mount.nfs4: mounting 192.168.178.76:/volume1/bup_backup/ failed, reason given by server: No such file or directory
```. I can't mount with NFSv4 like I mounted with version 3, e.g. ```
sudo mount -t nfs 192.168.178.76:/volume1/bup_backup/ /mnt/bup_backup
```. The explanation on [http://askubuntu.com/a/40210/173287](http://askubuntu.com/a/40210/173287) points out a partly working solution. Partly because ```
sudo mount -t nfs 192.168.178.76:/ /mnt/bup_backup
``` mounts the shared folder "data_extension", but I don't see a way to mount any other! What does / refer to in this case? The other proposed solution to invoke ```
mount -t nfs4 -o proto=tcp,port=2049 192.168.178.76:/<shared folder>/ ./test
``` doesn't work (fails with above error message). The relevant part of ```
/etc/exports
``` on the server: ```
/volume1/bup_backup 192.168.178.62(rw,async,no_wdelay,insecure,no_root_squash,sec=sys,anonuid=1025,anongid=100,fsid=1,nohide)
/volume1/data_extension 192.168.178.62(rw,async,no_wdelay,insecure,no_root_squash,sec=sys,anonuid=1025,anongid=100,fsid=0,nohide)
```
and ```

[General]
Verbosity = 1
Pipefs-Directory = /run/rpc_pipefs
# set your own domain here, if id differs from FQDN minus hostname
Domain = example.com
[Mapping]
Nobody-User = nobody
Nobody-Group = nogroup
[Static]
user@example.com = user

```
The NFSv4 domain on the server is set to example.com.

---

