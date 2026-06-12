---
title: "Grub Boot Question?"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by iGuitar on 2010-04-07
I recently updated my Ubuntu 9.10 with some updates that were available. When I start up and the grub menu shows up it gives me two different pairs of ubuntu to select. I can use the newly updated ubuntu or the older one. for example if the older one was ubuntu 9.10.l0 and the newer one was 9.10.20 it would give me both ubuntu's. Is this normal? And can i change it to display only the must current update of ubuntu?

---

### Post by Six_Digits on 2010-04-07
I would assume it's normal, I have a total of 3 Ubuntu and 1 Windows startup. I came on in search of removing the two distros I don't use without harming my main Ubuntu OS and Win gaming partition. Someone will let us know whats up.

---

### Post by drs305 on 2010-04-07
It is normal. As new kernels are introduced, older ones are moved down the menu but not removed. Over time, the list will continue to grow unless the user takes steps to change it.

Two options are to tweak the Grub 2 scripts or remove the older kernels from your system. 

The following post tells you how to remove older kernels - keeping at least one older kernel is recommended so you have a known "working" backup if the new kernel fails. Included in the section on "Removing Older Kernels" is a discussion of Ubuntu Tweak, a great GUI app for finding and removing older kernels.
[HOWTO: StartUp Manager & Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

If you really want to play with the Grub 2 scripts, you can alter them so only the latest two are displayed. How to do it is detailed in the following thread, however the older kernels in this case will remain on your system and take up a little space.
[ Grub 2 Title Tweaks Thread ]("http://ubuntuforums.org/showthread.php?t=1287602")

---

