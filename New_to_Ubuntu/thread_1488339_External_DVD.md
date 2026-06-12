---
title: "External DVD?"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by dell49 on 2010-05-20
This may be misdirected, and if so, apologies in advance.  I am running regular (not netbook) 10.4 on an Asus eeePC 1000.  

I wanted to be able to play music CD's, movies on DVD, pdf files on CD-ROM and so on.  I bought a Toshiba External SuperMulti Drive,  because it said it worked for Linux/Ubuntu.  When connected, the system recognizes and reads the Install CD.  But when I try to install the included software, the Package Installer gives an error message: "wrong architecture 'lpla'"  

Is this a problem I should take up with Toshiba?  Or is there software somewhere else I can get that would let me use this device?  Or do I even need the driver that the CD seems to be wanting to install?  Or is there some other external CD/DVD that works better with Ubuntu and a netbook?  Or do I need to replace the netbook with a computer that has an internal CD/DVD drive, and then install Ubuntu on that?  Or...?

---

### Post by -humanaut- on 2010-05-20
As far as I know the External DVD drive should be plug-in-play try shutting down your computer plug it in and reboot and see if that mounts the drive for you. You might need to add an entry into fstab for it when its plugged in open a terminal and type: lsusb

and post back here.

---

### Post by Hobgoblin on 2010-05-20
If you can read the install CD using the external drive then it doesn't seem like it needs any drivers.

I don't know what software it is trying to install but I would try just using it without.

Any USB DVD drive should work with Ubuntu with no need to install anything.

---

### Post by wilee-nilee on 2010-05-20
Both posts are correct the cd driver loader or drivers are .exe for windows eh.

---

### Post by dell49 on 2010-05-20
Thanks all; I should learn to trust Ubuntu. Y'all have it far more fixed up than I realize.

---

