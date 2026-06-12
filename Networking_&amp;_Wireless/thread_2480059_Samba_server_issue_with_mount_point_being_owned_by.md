---
title: "Samba server issue with mount point being owned by root instead of 'force user'"
date: 2022-10-18
forum: Networking &amp; Wireless
---

### Post by gyrex on 2022-10-18
I've created a samba share on an ubuntu server called teslausb with the following lines specified in smbd.conf:

```
   [teslausb]
   comment = John's home share on Ubuntu
   path = /mnt/sdb1/teslausb
   browseable = yes
   writeable = yes
   valid users = john
   write list = john
   force user = john
   force group = john
```

john:john is the owner of /mnt/sdb1/teslausb and I've set permissions as chmod -R 755:

```
john@docker:/mnt/sdb1/teslausb$ ls -al
total 1600
drwxrwxr-x 2 john john    4096 Oct 18 14:17 .
drwxrwxr-x 4 john john    4096 Oct 18 02:38 ..
-rwxrwxr-x 1 john john    4096 Oct 18 03:20 ._10.11.12.11-netconsole.log
-rwxrwxr-x 1 john john 1608971 Oct 10 14:55 10.11.12.11-netconsole.log
-rwxrwxr-x 1 john john    2653 Dec 13  2016 avrflash
-rwxrwxr-x 1 john john    4096 Oct 18 02:39 ._.DS_Store
-rwxrwxr-x 1 john john    6148 Oct 18 02:58 .DS_Store
```

When I connect to the share via Windows, there's no problems writing to the share, however, when I mount the share on an Ubuntu box ```
sudo mount -t cifs -o user=john //docker/teslausb /mnt/teslausb/
``` I can't write to the mounted share. I get a 'permission denied' error message.

For some strange reason, the mounted share also shows root as being the owner of the files in that share despite 'force user' being specified in the smbd.conf.

```
john@vm-ubuntu:/mnt/teslausb$ ls -al
total 1596
drwxr-xr-x 2 root root       0 Oct 18 14:17 .
drwxr-xr-x 6 root root    4096 Oct 18 12:25 ..
-rwxr-xr-x 1 root root    4096 Oct 18 03:20 ._10.11.12.11-netconsole.log
-rwxr-xr-x 1 root root 1608971 Oct 10 14:55 10.11.12.11-netconsole.log
-rwxr-xr-x 1 root root    2653 Dec 13  2016 avrflash
-rwxr-xr-x 1 root root    4096 Oct 18 02:39 ._.DS_Store
-rwxr-xr-x 1 root root    6148 Oct 18 02:58 .DS_Store
```

If I mount the share and specify uid and gui in the mount command ```
sudo mount -t cifs -o user=john,uid=john,gid=john //docker/teslausb /mnt/teslausb/
``` I can write to the samba share but I'm trying to avoid having to specify this in the mount command and thought that by using 'force user' this should achieve the same result.

I've also tried chmod -R 777 to the samba share but this didn't help.

I'm a little confused about how this should work. Why is this share being mounted with root as the user? Can someone please help me? Thanks in advance for any help, I really appreciate it.

---

### Post by TheFu on 2022-10-18
Samba doesn't care about Unix permissions. Samba runs as root and uses internal users to decide access.

If you are actually using a docker container, then this is a docker startup/configuration problem. The container startup needs to pass through any local shares with the username to own the external share.

I don't use docker enough to know the exact syntax, but that's what is needed.

For Ubuntu to Ubuntu network storage access, use NFS, not CIFS. NFS is the native file sharing method on Unix and will respect normal Unix permissions, users, groups, and ACLs as expected.

To have a linux container gain access to host storage areas, use the facilities of the container system, not CIFS.

---

### Post by gyrex on 2022-10-18
Thanks for your response. It's not a docker container, it's an Ubuntu server which runs docker. I'm aware of NFS but the app I'm using uses CIFS/Samba for accessing network shares so I really need to get Samba to work properly. I think I may have found a solution (I think the issue is that I'm using sudo to mount the share rather than a normal user) but before I declare the issue solved, I'll keep working on it.

---

