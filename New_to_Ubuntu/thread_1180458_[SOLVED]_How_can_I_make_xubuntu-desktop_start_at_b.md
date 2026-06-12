---
title: "[SOLVED] How can I make xubuntu-desktop start at bootup?"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by j-g-faustus on 2009-06-06
Hi,

have a home server running Ubuntu Server 9.04, followed this guide [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)
to install xubuntu-desktop.

I have two questions:
* When calling startxfce4 (a command I found somewhere, presumably how you start the desktop), it actually seems to be starting gdm rather than xubuntu. Where can I change that?
* How can I make xubuntu start automatically when I start the computer?

---

### Post by Hund on 2009-06-06
> gksudo gdmsetup

And under the tab "Security" enable automatic login. :)

---

### Post by aysiu on 2009-06-06
If you want Xfce to automatically start, it really helps to have GDM do it.

```
sudo /etc/init.d/gdm start
``` should do the trick, along with an autologin, as Hund has given instructions for.

Otherwise, you're going to have to start it manually each time... or work on some complicated hacks to get it started without GDM or KDM.

---

### Post by j-g-faustus on 2009-06-06
OK, got that working. Thanks to both of you :)

---

