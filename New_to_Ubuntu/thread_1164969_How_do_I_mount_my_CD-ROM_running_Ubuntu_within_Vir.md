---
title: "How do I mount my CD-ROM running Ubuntu within VirtualBox?"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by Richardcavell on 2009-05-20
I am running 64-bit Ubuntu 9.04 within VirtualBox.  I've selected 'Install Guest Additions', which causes it to 'mount' an .iso file that contains certain drivers.  There is no actual CD-ROM drive; it's a virtual CD-ROM drive.  Now, if I type 'ls /media' within a Terminal, it lists 'disk' but no 'cdrom'.  How do I mount it?  What does it mean when I get:   mount: error while loading shared libraries: /lib/libsepol.so.l: cannot read file data: Input/output error  TIA.

---

### Post by Dark Aspect on 2009-05-20
> **Richardcavell said:**
> I am running 64-bit Ubuntu 9.04 within VirtualBox.  I've selected 'Install Guest Additions', which causes it to 'mount' an .iso file that contains certain drivers.  There is no actual CD-ROM drive; it's a virtual CD-ROM drive.  Now, if I type 'ls /media' within a Terminal, it lists 'disk' but no 'cdrom'.  How do I mount it?  What does it mean when I get:   mount: error while loading shared libraries: /lib/libsepol.so.l: cannot read file data: Input/output error  TIA.

Can you run:

```
df -h
```

In the terminal to see if the cd-rom drive is mounted as another filesystem, If disk is in fact the virtual cd-rom, merely open it and it should mount automatically.

---

### Post by bacardiandwatermelon on 2009-05-20
Does this help at all?

[http://www.virtuatopia.com/index.php/Configuring_VirtualBox_Virtual_Machine_Settings](http://www.virtuatopia.com/index.php/Configuring_VirtualBox_Virtual_Machine_Settings)

---

### Post by Richardcavell on 2009-05-20
Okay, I worked it out.  I'll record the answer here in case anyone else gets the same problem.  The problem was that I was still in the installer.  I was logged in as ubuntu@ubuntu.  I needed to reboot (because it's a virtual machine, it was a virtual reboot).  Only after that was it able to 'know' that it had a CD drive.  (Again, a virtual CD drive).  Thanks for putting up with my noobness.  Richard

---

