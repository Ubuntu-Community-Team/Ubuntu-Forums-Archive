---
title: "Downloading a Kernel and Need Help"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by lanetherif on 2010-05-21
Hi, 
due to a problem [http://ubuntuforums.org/showthread.php?t=1488011](http://ubuntuforums.org/showthread.php?t=1488011) at the moment I have no internet connection other than through live CD.
Anyway, not that I think I will be able to solve the problem on my own, still I want to give it a shot. May be the problem is really due to the kernel.
There seems to be two types of file available to download in kernel.org which are tar.bz2 and in kernel-ppa/mainline with .deb extensions.
I just downloaded latest kernel version from kernel.org and planning to download 2.6.32.13.4 from ubuntu ppa. 
What should I do next, I mean do I need any compiling (with bz2 it feels like I have to) and is there a sequence for the image file and headers file for the one I am downloading from ppa?

Any help will be appreciated.

---

### Post by -humanaut- on 2010-05-21
I don't know how well Ubuntu will run under an unsupported Kernel you'd have to built your options and everything into as well What exactly are you trying to do with it?

---

### Post by sgosnell on 2010-05-21
Get the .deb file.  It will install easily with gdebi.  You don't want to get into compiling your own kernel at this stage.  You can also get newer kernels [here](http://kernel.ubuntu.com/~kernel-ppa/mainline/).  You only need the linux image for your architecture, either i386 or 64-bit.

---

### Post by lanetherif on 2010-05-22
> **sgosnell said:**
> Get the .deb file.  It will install easily with gdebi.  You don't want to get into compiling your own kernel at this stage.  You can also get newer kernels [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/").  You only need the linux image for your architecture, either i386 or 64-bit.

I used deb file. While booting just before loading Ubuntu, some non-graphical errors has shown up (Something looking like in hexadecimal, I am not sure) still it was able to load Ubuntu.

---

