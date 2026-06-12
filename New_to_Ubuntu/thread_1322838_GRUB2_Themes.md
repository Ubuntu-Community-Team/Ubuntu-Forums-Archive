---
title: "GRUB2 Themes"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by mbr78 on 2009-11-11
How do I install/enable graphical themes like these, [http://grub.gibibit.com/Themes](http://grub.gibibit.com/Themes), for GRUB2 in Ubuntu 9.10? I have read that Ubuntu 9.10 turns off the GRUB2 graphical menu by default.

---

### Post by kansasnoob on 2009-11-11
Check out section #8 of this tutorial:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by glennric on 2009-11-11
kansasnoob:  #8 in the Grub2 Basics tutorial will only show how to change the splash image.  The Grub2 themes that mbr78 is referencing are much more than just a splash image.  Notice the scroll bars, and icons for items in the boot menu, etc.  To get those things you will have to compile the source that is on that page.  There is also a good chance the grub-pc package in the Ubuntu repositories is not compiled to handle those themes, so you might have to rebuild that with some modifications as well.

To put this briefly, the grub2 themes are not ready yet.

---

### Post by glennric on 2009-11-11
I found a tutorial for Arch-Linux on how to set these themes up.  It is [http://bbs.archlinux.org/viewtopic.php?id=56576]("http://bbs.archlinux.org/viewtopic.php?id=56576")

On that page the following is stated:
> For those of you on Ubuntu, to answer your question: no, Ubuntu's grub2 does not have gfxmenu capabilities yet.
Although, I am not sure if that is still relevant to Karmic.

---

### Post by mbr78 on 2009-11-11
GRUB2 does support themes. This page, [http://grub.enbug.org/ThemeFormat](http://grub.enbug.org/ThemeFormat), tells how to make themes for GRUB2 but it doesn't explain how to install them.

---

### Post by kansasnoob on 2009-11-11
> **glennric said:**
> kansasnoob:  #8 in the Grub2 Basics tutorial will only show how to change the splash image.  The Grub2 themes that mbr78 is referencing are much more than just a splash image.  Notice the scroll bars, and icons for items in the boot menu, etc.  To get those things you will have to compile the source that is on that page.  There is also a good chance the grub-pc package in the Ubuntu repositories is not compiled to handle those themes, so you might have to rebuild that with some modifications as well.

To put this briefly, the grub2 themes are not ready yet.

My bad! I didn't actually check out the OP's link.

---

### Post by emeraldgirl08 on 2009-11-11
When you go to the link for the OPs first link and click on download. It shows several links. For one of the downloads there is an ISO file. I wonder if this will automatically install the themes for you?

Another question is security. I know Linux is on the low-level for viruses etc but still. Better to be safe than sorry!

---

### Post by emeraldgirl08 on 2009-11-15
Anyone get this one working? The GRUB themes sure seem nice so am curious.

---

### Post by lordskid on 2009-12-17
I got this working. It is outdated though. check my site on [http://www.karmic-koala.totalh.com](http://www.karmic-koala.totalh.com) I put the steps I did to compile the grub from grub.gibibit.com

The latest news though is that it is now being implemented on the grub2-experimental branch if you want to try. add the following lines to your software sources:

deb [http://ppa.launchpad.net/fzielcke/grub-ppa/ubuntu](http://ppa.launchpad.net/fzielcke/grub-ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/fzielcke/grub-ppa/ubuntu](http://ppa.launchpad.net/fzielcke/grub-ppa/ubuntu) karmic main

This works for Ubuntu karmic-koala, if you are using a different version go to [www.launchpad.net](www.launchpad.net) and search for ppa fzielcke

after which you will have to download the overlay tarball from grub.gibibit.com

Hope this helps. I am still trying to do this right then I will update my website.

Good luck. 

Note: do keep a Live CD or Live USB handy to prevent being stuck-up

---

