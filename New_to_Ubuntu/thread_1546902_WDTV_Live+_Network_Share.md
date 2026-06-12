---
title: "WDTV Live+ Network Share"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by Slow Motion on 2010-08-06
Hello,

I just got a WDTV Live+ and I need to share a folder on an NTFS drive. I used pysdm to setup my ntfs mount, so it mounts on boot, but I don't know if I set it up completely right. I also tried right clicking on my video folder on my NTFS drive and shareing it, but I get this error:

'net usershare' returned error 255: net usershare add: cannot share path /media/sda3/Videos as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = false" 
	to the [global] section of the smb.conf to allow this.

Is there something in pysdm I need to change in order for this to work? like umount?

---

### Post by cariboo on 2010-08-08
The error message tells you what you have to do.

> Ask the administrator to add the line "usershare owner only = false"
to the [global] section of the smb.conf to allow this.

smb.conf is located in /etc/samba/, to open the file for editing, press Alt-F2 and type:

> gksu gedit /etc/samba/smb.conf

then add the line:

> usershare owner only = false

to the [global] section of the file.

---

