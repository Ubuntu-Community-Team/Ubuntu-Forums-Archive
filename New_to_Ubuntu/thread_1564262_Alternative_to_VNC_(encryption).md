---
title: "Alternative to VNC (encryption)"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by B34ST1Y on 2010-08-30
Hey all,


I manage a small to medium sized network where PCI/DSS standards are in effect. We have a few Linux servers (some Ubuntu, some RHEL) and need a safer alternative to VNC. Does anyone know of a way that we can get remote desktop to the machine *without* turning on ssh to each and every one and simply tunneling? Is there a program that supports encryption inherently?

---

### Post by gradinaruvasile on 2010-08-30
Servers with x server...?

There is Teamviewer. I you trust them.

PS: What is so bad in ssh tunneling with x11vnc?

---

### Post by krunge on 2010-08-30
vinagre, vino, x11vnc, and others support VeNCrypt (which switches to SSL during the VNC handshake.) I think tigervnc will support VeNCrypt in its next release.

x11vnc also supports regular SSL tunnelling (like vncs:// would be thinking of what https:// is) and comes with an SSL enabled java viewer applet.

---

### Post by B34ST1Y on 2010-08-30
does x11vnc support ssl encryption without using the web applet? Am I able to achieve encryption using a viewer standalone?

---

### Post by gradinaruvasile on 2010-08-30
Try Remmina.

---

### Post by krunge on 2010-08-30
> **B34ST1Y said:**
> does x11vnc support ssl encryption without using the web applet? Am I able to achieve encryption using a viewer standalone?
Yes, you can use any viewer supporting VeNCrypt to achieve SSL encryption.

x11vnc also has a somewhat kludgey viewer project called ssvnc that supports both VeNCrypt and normal SSL (i.e. vncs:// tunnelling.)

---

