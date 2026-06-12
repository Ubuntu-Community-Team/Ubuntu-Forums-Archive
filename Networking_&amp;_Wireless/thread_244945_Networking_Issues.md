---
title: "Networking Issues"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by metricben on 2006-08-27
hi all,

i have installed samba and smbfs, and can "connect to server" to a WinXP box, and a Win98SE one.  This was sufficient, but to run many applications i need permanantly mounted shares under /media/*** so i can access my pics from picasa, etc.  I can do this with the XP box using:
```
//192.168.68.100/Music    /media/dell1music smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0
```
in /etc/fstab, but when i try this with the 98 box i get:
```
ben@benspc:~$ sudo mount -a
7427: session request to 192.168.68.107 failed (Called name not present)
7427: session request to 192 failed (Called name not present)
7427: session request to *SMBSERVER failed (Called name not present)
SMB connection failed
ben@benspc:~$

```
I gather there is a difference between "Connect to server" and using fstab, and the 98 pc might be setup slightly wrong

Any help appreciated...
thx

---

