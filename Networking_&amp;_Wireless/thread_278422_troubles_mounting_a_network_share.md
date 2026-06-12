---
title: "troubles mounting a network share"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by SC2Sick on 2006-10-16
I'm trying to mount a network share locally using the following command

anthony@2buntu:~$ sudo mount //192.168.0.1/share /media/share/ -o username=username,password=password,dmask=777,fmask=777

obviously the actual values are filled in.... but, i'm getting the following error


mount: wrong fs type, bad option, bad superblock on //192.168.0.1/share,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This is on a network domain (windows) and i've changed the workgroup(domain) in /etc/samba/smb.conf (that path may be wrong, but it's close).  I've set this up before... I just can't figure out why it won't work now.  btw it's a windows share if that matters.

---

### Post by Iowan on 2006-10-16
Do you need to specify the filesystem type (smbfs or cifs)?
[http://www.ubuntuforums.org/showthread.php?t=271259]("http://www.ubuntuforums.org/showthread.php?t=271259")
Check the last few posts in this thread.

---

### Post by SC2Sick on 2006-10-16
Followed the last post exactly, no luck.

---

