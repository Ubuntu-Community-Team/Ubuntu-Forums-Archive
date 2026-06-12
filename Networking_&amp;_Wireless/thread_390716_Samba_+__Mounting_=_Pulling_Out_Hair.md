---
title: "Samba +  Mounting = Pulling Out Hair"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by jwhiteman on 2007-03-22
I have recently decided to try Linux (ubuntu 6.10) as I am tired of upgrading $$ all the time with Windows. I have managed to stumble around and get things working.  However, I cannot mount with samba.  Long story, but I need to mount share to use WINE.

I can smb:// successfully. I can see the shares on the windows server (2003). When I try to mount a share say //SERVER/SHARE I get an error:

mount error 1 = Operation not permitted.
Refer to the mount.cifs(8) manual page, blah blah....

I have checked the manual and all I can say is ?????

If I can smb:// to the share and I can navigate the share, why can I not mount the thing?

---

### Post by jwhiteman on 2007-03-22
Never Mind, need to set up the computer to allow the user to mount as SUDO.

Works now.!!!!!!!

---

