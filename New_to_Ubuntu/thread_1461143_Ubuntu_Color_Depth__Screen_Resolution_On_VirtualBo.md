---
title: "Ubuntu Color Depth / Screen Resolution On VirtualBox"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by SKhan on 2010-04-23
hello all.
i just installed ubuntu 9.10 as guest OS on virtualbox. (Windows 7 being Host OS)
There are only 2 screen resolutions available. maximum is 800x600. This is keeping me from going fullscreen.
also if i open Terminal and type:
sudo gedit /etc/X11/xorg.conf&#8206;
i only see a blank file.
i doubt if color-depth has something to do with screen resolution.
on ubuntu start up, virtualbox reports that your guest OS is set to 16-bit.
any solution?
Note: i am somewhat expert in windows, and 1st day beginner in case of ubuntu.

---

### Post by A_M_S on 2010-04-23
Try to install the Virtual Box guest additions (Device->Install Guest Additions )

---

### Post by SKhan on 2010-04-24
> **A_M_S said:**
> Try to install the Virtual Box guest additions (Device->Install Guest Additions )
when i go to devices > install guest additions, a ubuntu detects a newly inserted CD. So what to do after that? there are some exe, run, sys files inside it. and also some read-me files which didn't help me.
can someone please tell me its installation in detail?
my host OS is windows 7 installed in C drive, and guest OS ubuntu 9.10 installed in G drive.

---

### Post by SKhan on 2010-04-25
no one to help me out?

---

### Post by steveneddy on 2010-04-25
VirtualBox documentation online:

[http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)

and the Guest Additions section:

[http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)

Hope that helps.

---

