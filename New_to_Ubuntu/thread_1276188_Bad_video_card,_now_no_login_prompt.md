---
title: "Bad video card, now no login prompt"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by rm06 on 2009-09-26
I attempted to install a dual video monitor on my 9.04 64bit machine without success - I have reverted to my old video card as the upgrade didn't work on either of my dual-boot environments. 

Now I still get the GRUB menu and Ubuntu splash screen, then the screen flips a couple of times with some grainy ubuntu logos and either stalls or doesn't display the login prompt. I am dual booting with Vista which I'm able to get logged in with no problems.

In any case, I'm stuck right now without a way into my Ubuntu. Any help is appreciated. Thanks!

---

### Post by jerrrys on 2009-09-27
boot into grub by pressing **Esc** durning grub menu in safe mode try to fix X option

---

### Post by sandyd on 2009-09-27
```

sudo dpkg-reconfigure xserver-xorg

```
That will reset your xorg config. Then you can install the drivers for the new card.

---

### Post by anewguy on 2009-09-27
What you have is the X server still using the driver for the new video card you tried an removed.  You will need to reinstall the driver for your old card.  Did you make a copy of xorg.conf before you started messing with your new card?  Either way, you don't actually have to boot to recovery mode most of the time - once you get the weird screen just hold down CTRL/ALT and press F1.  This should bring up a terminal window.  Now you can start to recover xorg.conf.  If you made a backup before you started, you can just copy it back (as su of course).

dave :)

---

### Post by rm06 on 2009-09-27
Excellent, thanks for your help everyone.

---

