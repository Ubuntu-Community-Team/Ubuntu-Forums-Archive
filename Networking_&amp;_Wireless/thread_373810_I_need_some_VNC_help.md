---
title: "I need some VNC help"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by bradford72 on 2007-03-01
I'm not sure if this is the correct forum for this question, but here it is.  I have a windows machine in addition to my Ubuntu machine, and would like to set them up so that the windows machine is running a VNC server, and I can control it through a virtual client on my Linux machine.  Before you ask "why I would want to do such a thing?!" I will tell you I want to do such a thing to save space on my very small desktop.  I've got both machines connected to a netgear router, and think it would be the bee's knees if I didn't have to connect anything but a power cord and an ethernet cord to my windows machine, but could still control and view it from Linux.  I've looked at a few VNC software packages, and TightVNC looks okay to me, but the software for Linux is for RedHat, and is compressed as a RPM.  Any good ideas here would be greatly appreciated!  Is there a VNC package that is supported by windows on the server side, and ubuntu on the client side?  Thanks in advance, ubuntuforums rock!

---

### Post by m0bilitee on 2007-03-01
Which version of Windows?  If it's XP Pro, I'd enable remote desktop on it and use the Ubuntu Terminal Services Client (rdesktop).  That's what I do to control my Windows boxes from Ubuntu.

---

### Post by jfinkels on 2007-03-01
If you really need to, you can convert .rpm packages to .deb packages using the command
```
alien -d *packagename*.rpm
```
However, Ubuntu comes with a "Terminal Server Client" (similar to Windows Remote Desktop Connection); it's in the menu under Applications > Internet > Terminal Server Client, I think. You can use that to connect to your Windows computer.

---

### Post by bradford72 on 2007-03-01
> **m0bilitee said:**
> Which version of Windows? If it's XP Pro, I'd enable remote desktop on it and use the Ubuntu Terminal Services Client (rdesktop). That's what I do to control my Windows boxes from Ubuntu.
It's windows 2000, so I'll look see if it has remote desktop capability, and use Terminal Client...otherwise many thanks j for reminding me about alien!

---

### Post by Mr. C. on 2007-03-01
UltraVNC or RealVNC will work just fine.

---

