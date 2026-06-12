---
title: "Mounting a NAS works but returns error"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by jonnybarnes on 2011-02-20
I have added this to my fstab file to mount the networked NAS in my house:

```
# mount the NAS
//192.168.2.12/jonnys_mac /media/nas cifs credentials=/root/smb/credentials,rw,iocharset=utf8,uid=1000,gid=1000 0 0
```

This appears to work, theres an icon on my desktop called nas, and /media/nas is a directory I can write to. However, dmesg throws up this error everytime I boot up:

```
jonny@jonny-ubuntu:~$ dmesg | grep CIFS
[    4.011902] CIFS VFS: Error connecting to socket. Aborting operation
[    4.011957] CIFS VFS: cifs_mount failed w/return code = -101
```

Anyone know what's going on?

Cheers,
Jonny

---

### Post by Hedgehog1 on 2011-02-20
It looks for all the world like the network connection not yet active when fstab file is executed.

This link: [http://www.linuxquestions.org/questions/linux-general-1/delay-fstab-mount-of-smbfs-during-boot-31184/]("http://www.linuxquestions.org/questions/linux-general-1/delay-fstab-mount-of-smbfs-during-boot-31184/") show others have hit it before, too.

The network is supposed to be loaded by this time, but they gave the other user this solution:

*well you can always convert the fstab line to a mount command in /etc/rc.local*

Hope this helps a bit...

---

### Post by jonnybarnes on 2011-02-21
Hey, cheers for the reply, putting the mount command in the rc.local file has worked.

---

### Post by Hedgehog1 on 2011-02-21
Excellent!  We both learned something on this one.
 
If you would, please mark the thread as SOLVED so others will know what to do when they have the same issue.
 
:KS

---

