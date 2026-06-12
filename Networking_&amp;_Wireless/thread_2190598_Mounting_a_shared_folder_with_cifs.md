---
title: "Mounting a shared folder with cifs"
date: 2013-11-28
forum: Networking &amp; Wireless
---

### Post by abizmo on 2013-11-28
I'm trying to mount a shared folder from windows 7 to Ubuntu 12.04 using cifs.
I execute the next command:
```
mount -t cifs //srv/bck /mnt/bck -o nouser,rw,nofail,noexec,sec=ntlm,credentials=/etc/.cifspw
```
and it returns:
```
mount error(5): Input/output error
```
In my windows event viewer appears
```
28/11/2013 7:54:51 - Special privileges assigned to new logon. id 4672
28/11/2013 7:54:51 - An account was successfully logged on. id 4624
28/11/2013 7:54:51 - An account was logged off. id 4634
```
i have no idea why it is logged off...

Thank you,

---

