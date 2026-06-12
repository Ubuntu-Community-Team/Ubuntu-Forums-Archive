---
title: "Editing Grub Menu.lst on Ubuntu 9.10 64 Bit, Dell Studio 1555"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by darshshinde on 2009-10-31
Hi, I am having a dell studio 1555 with Intel core 2 duo 6500, 4 GB ram and 320 Gig HDD. it came with Vista home premium 64 bit. I installed ubuntu 9.10 64 alongside it with dual boot. The system works great. Wifi, bluetooth everything working out of box in ubuntu. the only problem is then i am not able to edit the menu.lst file to make the Vista as default os. (i am no vista lover but those at home require to boot into vista). When ever i try "gksu gedit /mnt/boot/grub/menu.lst" command,the file does open up, but does not show anything inside !!
I have edited this file several times before on my desktop, which had ubuntu 9.04 32 bit. however, its strange that i am not able to see anything now. Interestinggly, though grub menu.lst is empty, it shows up the boot options on booting up the computer, and i am able to successfully boot into vista as well. 
Please help me !!

---

### Post by ssalman on 2009-10-31
hi,

Ubuntu 9.10 uses a new GRUB release which have new features and introduces a new way of doing things, I was searching myself for an answer and found it in the below link, hope this helps.

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by trulan on 2009-10-31
Ubuntu 9.10 has moved on from Grub legacy to Grub2 (or grub-pc as the package is called).

Editing menu.lst is a thing of the past.  Grub2 uses grub.cfg which is automatically generated from scripts, so if you edit it, it gets overwritten frequently.

See the link posted above for more info on how to make grub2 do what you want.

---

### Post by ranch hand on 2009-10-31
Your default OS to boot to is edited in /etc/default/grub.

See link in sig for info and links to much more.

---

### Post by greg_ory on 2010-01-17
Hi there,

I found this documentation quite helpful.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

-Gregor

---

