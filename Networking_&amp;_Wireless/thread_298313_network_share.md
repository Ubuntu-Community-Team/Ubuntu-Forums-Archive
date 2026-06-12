---
title: "network share"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by numbers1thru9 on 2006-11-12
I have a windows 2003 file server and i would like my ubuntu server to mount to a read only share. I have found different guides on making this work howerver if i try to use the smbmount command, it tells me that it doesnt exist. if i use the mount command, it wont mount using either the smbfs or ntfs commands. Below is the error i get with the smbfs option used

> mount: wrong fs type, bad option, bad superblock on //192.168.1.200/Music,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

Any help anyone can give me is appreciated

---

### Post by numbers1thru9 on 2006-11-12
can anyone help?

---

### Post by cloakable on 2006-11-12
What is the exact command you're using to mount the share?
```

mount -t smbfs -o guest //192.168.1.200/Music /directory/to/mount/in

```
Is what I would generally use in your situation.

---

### Post by speedman on 2006-11-12
Use cifs instead of smbfs for Win2k3.

modprobe cifs

mkdir /mnt/win2k3

mount -t cifs //192.168.1.200/Music /mnt/win2k3

You can have the cifs module load each time you boot by adding it to /etc/modules.

Hope that helps.


Regards,

SM

---

### Post by numbers1thru9 on 2006-11-13
the command that I type to try and mount is

> mount -t smbfs //192.168.1.200/Music /mnt/Music

and i still get that same error that I mentioned in my earlier post. Also when I tried the cifs type, it gave me the same error.

> mount: wrong fs type, bad option, bad superblock on //192.168.1.200/Music,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so 

> [42950337.570000] smb_fill_super: missing data argument
[43008217.150000] smb_fill_super: missing data argument
[43008780.390000] smbfs: mount_data version 1936029031 is not supported
[43008844.060000]  CIFS VFS: cifs_mount failed w/return code = -22


Those are the last message from dmesg | tail for my last 4 attempts this morning with the command i was using before. The last 2 are from the two commands that you guys asked me to try.

---

### Post by numbers1thru9 on 2006-11-13
Well the cifs thing worked, after I just decided to try and enter my usrename and pw in the options. Now i just need to try and get it to work on bootup. Thanks alot for your help :)

---

### Post by phazon. on 2006-11-25
Hi,

I am having a similar issue, except instead of trying to mount a W2K3 share, I am trying to connect to a Synology NAS. The command I am using and the resulting error is as follows;

> nick@home-desktop:~/Desktop$ sudo mount -t smbfs //192.168.0.5/MyDocs /home/nick/Desktop/mydocs-nas
mount: wrong fs type, bad option, bad superblock on //192.168.0.5/MyDocs,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Any pointers as to what this linux n00b is doing wrong would be much appreciated.

EDIT: I also get this error in dmesg after running the mount command;

> [17282330.728000] smbfs: mount_data version 1936029031 is not supported

---

### Post by travishume on 2007-05-23
That horrible error message means you need to install smbfs (probably)

sudo apt-get install smbfs

---

