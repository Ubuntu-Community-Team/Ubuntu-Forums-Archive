---
title: "Size of Windows XP in VirtualBox"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by Kellemora on 2011-03-02
Hi Gang
Still in the process of converting over to 10.04.1.......
Although I do have a dual boot system, I decided to try VirtualBox for the last two Windows programs I must use....
One runs perfectly in WINE.....so that left ONE, that I'm not yet sure if it will run in VirtualBox yet either, until I solve this problem.

I installed Windows XP-Home into VirtualBox running on Ubuntu 10.04.1
The size of the Windows Window is the same size in normal mode or in Full Screen Mode, going to full screen mode merely drops the virtualbox window out from gray to black as far as border space is concerned.

If I can't get it to full screen, then it would be useless to even see if the accounting program will run in windows in virtualbox....

Any way to get the Window bigger?????

One last thing, during the virtualbox install, it asked if I wanted to use an Existing HD, but nothing showed in the box.  I assumed this meant Use my existing Install of Windows XP-Pro-MCE from when I dual boot.
Water over the dam now since I installed XP-Home in the virtualbox.
But was THAT the option they were talking about?????

TTUL
Gary

---

### Post by howefield on 2011-03-02
> **Kellemora said:**
> The size of the Windows Window is the same size in normal mode or in Full Screen Mode, going to full screen mode merely drops the virtualbox window out from gray to black as far as border space is concerned.

Have you installed Guest Additions ?

This will give you a better set of drivers for the graphics, mouse and a few other things which should allow to you to go full screen, seamless mode ect.

> One last thing, during the virtualbox install, it asked if I wanted to use an Existing HD, but nothing showed in the box.

You could use that if you already had a VM created. Perhaps you reinstall your system and need to set up Virtualbox again, you could use that to point to the VM you already had. Or to make use of downloadable VMs.

---

### Post by Kellemora on 2011-03-05
Thanks Howefield

I have not installed guest editions, but after a little playing around and tweaking I found that it was the default resolution that was causing it.

I am thoroughly AMAZED at this VirtualBox!!!!!!

Not that I like Windows, but I have some programs I can't live without that are Windows ONLY and only ONE of them would run properly in WINE.....
There are no Linux counterparts of these programs either......

It just boggles the mind that I don't have to reboot or switch to another computer.  Just switch to the Desk I have Windows open and running on.


On the other topic, my computer is triple boot, WinDoze, Ubuntu 8.04 and Ubuntu 10.04.1 and I rarely if ever booted into WinDoze.  I used another computer and a KVM switch to get to my WinDoze programs.
Heck, if things keep going they way they have been lately, I will be able to eliminate all these computers and work from just one of them!

My thought when installing VirtualBox was that since I already HAD WinDoze installed that it could just grab that one....  But not knowing for sure, I just installed another version of WinDoze since I have so many now unused copies laying around here.
Just irks me that every time I swap hard drives around, one has to re-register with Mickey$oft in order to check a file on it.
They sure do things in dumb ways!!!!!

Thank you and have a nice weekend!

TTUL
Gary

---

