---
title: "ubuntu 9.10 install problem on Acer Aspire One"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by spearfish on 2009-12-27
I made a bootable USB flash drive with the Ubuntu 9.10 disk image on it and I am having problems with the system locking up during install.  No mouse and no keyboard at the graphics-based "Welcome" screen.

The system allows me to initially select install flags, (like noapic, nolapic, acpi=off) and the system goes into it's graphics-based install mode.  

Then it shows a text screen with "SQUASHFS errors" having to do with page faults and it goes to the graphics-based "Welcome Screen" where it asks the user to select a language.  At this point, the keyboard and mouse-pad have locked up, and I am not able to select anything or continue.

I have tried several boot options including:
irqpoll
noapic
nolapic
acpi=off

safe graphics mode makes the screen look all garbled and scrambled!  haha

I'm guessing there is some command line option that I'm missing.  Anybody else have problems installing Ubuntu on an Acer Aspire One?

thanks

---

### Post by rottentree on 2009-12-27
I have a similar problem on my Asus 1005ha-h but for me it gets stuck when it should load up the live environment(after the ubuntu symbol) and the only thing I can do is to press the shutdown button on my netbook and that's when the "SQUASHFS errors" come up and it hangs there and I have to take out the battery to 'shutdown':(

---

### Post by 5BallJuggler on 2009-12-27
I know it's the long-winded solution but try installing Jaunty and then doing the OS upgrade to Karmic.

I had the same problem with the mouse pad, it was related to the kernel image of linux, do you know which one you are trying to install. -the current one is Linux 2.6.31-17-Generic and is OK, the one you have downloaded maybe from an earlier build.

Also, try pressing Fn & F7, this enables/disables the mousepad (I think)

Phil

---

