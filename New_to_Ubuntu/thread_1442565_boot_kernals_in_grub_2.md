---
title: "boot kernals in grub 2"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by garma on 2010-03-30
i want to remove some of the old kernals from grub and create a boot window 7 in safe mode kernal but since i am a complete nube at linux-ubuntu the wiki.ubuntu.com/Grub2 might as well be written in Latin. can someone give me a step by step so i can simplify my grub.

---

### Post by drs305 on 2010-03-30
garma,

Welcome to Ubuntu and the Ubuntu forums.

I wrote this post a few days ago on removing older kernels. The easiest way is probably to use Ubuntu-Tweak. It's a GUI app that will show you kernels not in use and allow you to choose the ones you want to remove. Many users keep at least one older one as a 'backup'.
[http://ubuntuforums.org/showthread.php?t=1441827]("http://ubuntuforums.org/showthread.php?t=1441827")

That post also references another post which discusses with a bit more detail how to remove older kernels in the section "Removing Older Kernels":
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

As far as the "safe mode kernal" and W7, I'm not sure I understand what you want to do, but I don't use Windows so someone else may have to answer that one. Do you just want to be able to access Windows, and currently cannot?

---

### Post by Bachstelze on 2010-03-30
To remove kernels from the GRUB menu, just uninstall the corresponding [font=monospace]linux-image[/font] package in your package manager. It will remove the kernel from the GRUB menu, and also free a bit of diskspace. As for the Win 7 safe mode, I don't think you can have an option for that in GRUB, you have to start the Win 7 bootloader, and then you can boot it in safe mode.

---

