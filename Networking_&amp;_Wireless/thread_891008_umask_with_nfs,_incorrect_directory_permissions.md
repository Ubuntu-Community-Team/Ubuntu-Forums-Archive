---
title: "umask with nfs, incorrect directory permissions"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by jeffk on 2008-08-15
I have a problem with an Ubuntu 8.04 Desktop NFS client creating directories on a server share with incorrect permissions. The folders are inaccessible even to the owner (user2). The folders are intended to be permission 777, the contained files 666.

**Example**

The following is an example of an incorrectly created folder. I am diagnosing the problem as user1 on server:

```
user1@server:/path/to/share$ ls -al ./FOLDER
ls: cannot access ./FOLDER/FOLDER.txt: Permission denied
ls: cannot access ./FOLDER/.: Permission denied
ls: cannot access ./FOLDER/..: Permission denied
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
-????????? ? ? ? ?                ? FOLDER.txt
```

```
user1@server:/path/to/share$ sudo ls -al ./FOLDER
total 136
drwxr--r--    2 user2 user2   4096 2008-08-15 12:56 .
drwxrwxrwx 1750 user2 user2 126976 2008-08-15 12:54 ..
-rw-rw-rw-    1 user2 user2    121 2008-08-15 12:56 FOLDER.txt
```

I add full permissions to FOLDER:

```
user1@server:/path/to/share$ sudo chmod a+rwx FOLDER
```

And note that the contained file is fine:

```
user1@server:/path/to/share$ ls -al ./FOLDER
total 136
drwxrwxrwx    2 user2 user2   4096 2008-08-15 12:56 .
drwxrwxrwx 1750 user2 user2 126976 2008-08-15 12:54 ..
-rw-rw-rw-    1 user2 user2    121 2008-08-15 12:56 FOLDER.txt
```

I can reliably find the problem folders with the following commands:
```

user1@server:/path/to/share$ sudo find . -type f ! -perm 0666
user1@server:/path/to/share$ sudo find . -type d ! -perm 0777
./FOLDER
```

**umask**

The system-wide umasks are 000 as follows:

```
user1@server:~$ grep umask /etc/profile
umask 000
```

```
user2@client:~$ grep umask /etc/profile
umask 000
```

```
user2@client:~$ grep umask /home/user2/.profile
# the default umask is set in /etc/profile
#umask 022
```

**uid:gid**

The user2 uid:gid is the same on client and server:

```
user1@server:~$ grep user2 /etc/passwd /etc/group
/etc/passwd:user2:x:1003:1003::/home/user2:/bin/sh
/etc/group:user2:x:1003:
```

```
user2@client:~$ grep user2 /etc/passwd /etc/group
/etc/passwd:user2:x:1003:1003:User2,,,:/home/user2:/bin/bash
/etc/group:adm:x:4:user2
/etc/group:dialout:x:20:user2
/etc/group:cdrom:x:24:user2
/etc/group:floppy:x:25:user2
/etc/group:audio:x:29:pulse,user2
/etc/group:dip:x:30:user2
/etc/group:video:x:44:user2
/etc/group:plugdev:x:46:user2
/etc/group:fuse:x:107:user2
/etc/group:lpadmin:x:109:user2
/etc/group:admin:x:115:user2
/etc/group:user2:x:1003:
/etc/group:sambashare:x:125:user2
```

**nfs exports**

The nfsv2/3 exports are as follows:

```
user1@server:~$ cat /etc/exports
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
/path/to/share         192.168.10.1/24(rw,sync,subtree_check)
```

**client mounts**

The client mounts are as follows:

```
user2@client:~$ cat /etc/fstab
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=aad0ba6f-99ee-4c64-b47a-703504073581 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=65659dbc-8115-4212-99ae-c9c867f2c08b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
server:/path/to/share	/media/share	nfs	rsize=8192,wsize=8192,timeo=14,intr
```

Does anyone have any suggestions here? Thanks.

---

### Post by jeffk on 2008-08-19
Following up, there do not seem to be any easy configuration-level solutions (I'd love to be wrong on that point).

I'm using a [script]("http://ubuntuforums.org/showthread.php?p=5622577") called by cron to manually fix up these directories:
```
$ sudo find . -type d ! -perm 0777 ! -path "*.Trash*" | sudo xargs -n 1 chmod a+rwx
```

---

