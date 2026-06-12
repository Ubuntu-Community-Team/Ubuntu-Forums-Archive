---
title: "xubuntu mount"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by gishaust on 2008-01-24
Hi everyone

I have just installed xubuntu on  a laptop with low ram and I am trying to mount a share from the ubuntu server that I have in another room. I works fine I have been using the server with samba on the windows clients but  I am not sure what to do here. I don't want to use nfs. I have read that smb will work fine between linux boxes. I think I might have to add xubuntu to the work group do I do that in the host files.

Below is what i have tried and it did not work  can anyone see any issues

laptop:~$ sudo smbmount //File/group  /home/gishaust/fileshare -o username=gish,password=12345,uid=gish,gid=gish
sudo: smbmount: command not found


gishaust

---

### Post by GV1pJTHl on 2008-02-06
Try
```
user@machine~> sudo aptitude install smbfs
```
and let me know if it works then

---

