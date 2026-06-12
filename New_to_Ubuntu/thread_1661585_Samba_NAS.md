---
title: "Samba NAS"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by outleradam on 2011-01-06
I have a NAS at 192.168.1.100.  I can get the individual shares to mount, but I cannot mount the main share of my NAS.  I can browse to the main share with smb://192.168.1.100, but not mount it.  Sub-directories will mount, just not the main share.  

Here is my /etc/fstab entry..
//192.168.1.100 /media/NAS cifs credentials=/home/adam/.smbcredentials,iocharset=utf8,uid=1000,gid=1000 0 0

when I attempt to do it manually I get this: 
```
adam@adam-desktop:~$ sudo mount -all
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
adam@adam-desktop:~$ 
```If I mount a sub directory, it works.

Why can't I mount the main share?

---

### Post by perspectoff on 2011-01-06
On my NAS, the only thing in the main directory are the subdirectories. It's made like that for security purposes. But maybe yours is different.

---

### Post by outleradam on 2011-01-07
Yes, the only thing in the main Samba directory are subdirectories.  Why can't I mount the main directory?  I can browse it, but not mount it.   I can mount the main folder under Windows 7.  I can browse it under Ubuntu 10.10, but I cannot mount the main folder under Ubuntu.   
 
Is there anything I can try?

---

