---
title: "networking - samba - etc"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by windowsfree on 2008-11-24
I have a network with 2 windows computers and 2 ubuntu 8.10 computers.
If I try to connect to the windows workgroup, nothing shows.  Windows can see the linux computers.  I want to have the linux computers be part of the WORKGROUP that the windows machines are in.

I am not sure about editing the FSTAB and whatever else I need to do.  Being new to UBUNTU, I don't understand how to edit using root privelages.

Any help will be appreciated.  My windows machine has many music files I want to access.

Thanks

---

### Post by cariboo on 2008-11-24
IF your windows computers can see the Ubuntu computers, then you have Samba installed already. To change the workgroup you have to edit /etc/samba/smb.conf. To edit the file you can open it in your favorite text editor. If you don't have a favorite text editor use gedit press Alt-F2 and type:

```
gksu gedit /etc/samba/smb.conf
```

I resource I always when sealing with samba is this:

[www.samba.org/samba/docs/Samba3-ByExample.pdf](www.samba.org/samba/docs/Samba3-ByExample.pdf)

It walks you through setting up small networks to large networks, and everything in between.

Jim

---

### Post by Iowan on 2008-11-25
[Here]("http://ubuntuforums.org/showthread.php?t=288534") is a wonderful How-To on setting up CIFS shares.  Save it for later (ie. first things first). After you get the workgroup fixed, you might:
> **superprash2003 said:**
> try typing smb://x.x.x.x where x.x.x.x is the ip of the windows machine.. it hopefully should open the shared folders.. [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by windowsfree on 2008-11-25
Thank you!

---

