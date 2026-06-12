---
title: "How to install a video driver"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by donescamillo on 2009-09-18
Hi,

I have an Sis6326 video card. I found a Linux driver for it as tgz file. The picture attached shows the file extracted (various folders are created). How do I install now XFCom_Sis (which presumably is the driver)?

Thank you

---

### Post by nhasian on 2009-09-18
this might be a silly question, but is your video card not already supported by the linux kernel?

---

### Post by sandyd on 2009-09-18
first: sis cards suck. your better off getting a nvidia or ati card
second: the driver is extremely outdated and meant for red hat based distros. ubuntu is a debian based distro.
third: it ain't that easy compiling the driver


now that youve read through my rant, theirs a README file inside if i remember correctly. That should provide you with all the info you need

p.s. sorry for discouraging you at the start, i just didn't want you to waste your time.

---

### Post by donescamillo on 2009-09-18
Hi,

Thank you for your replies. The PC is an old one, used for experiments, not worth upgrading this is why it has an old Sis card.
Ubuntu does have a driver, but when I set 1280x960 the view area is very small, if I adjust from the monitor's buttons I will have to readjust when I boot Windows. I am currently using 1280x768.
There is a README, but at a glance it looks too complicated to me. I will probably keep on using 1024x768

regards,
donescamillo

---

### Post by nhasian on 2009-09-20
this happens if the screen's refresh rate is changed.  find out what refresh rate is on your CRT monitor by pressing the info or menu button.  it may be 60, 75, 100hz, etc.  then just set the same refresh rate in windows, and resize the display with the monitor buttons to suit your monitor.  then you will not have to adjust the monitor anymore when switching between operating systems.

> **donescamillo said:**
> Ubuntu does have a driver, but when I set 1280x960 the view area is very small, if I adjust from the monitor's buttons I will have to readjust when I boot Windows. I am currently using 1280x768.

---

