---
title: "Network P4 Ubuntu Hardy box with 486DX2 66 DOS via parallel port cable"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by MusicallyInspired on 2008-08-23
I've done some searching but can't really find what I need. I'm a little confused about what all needs to be done. I know it's possible to connect a linux box to a DOS machine with something called "plip" but I don't know how to get plip working on my Ubuntu machine. Everywhere I look says that the module packages are for Debian and says not to use them in Ubuntu.

Here's the story. Basically my 486 computer is running DOS and I don't have an ethernet card (ISA only board). I do have a parallel cable, however, that I used to use to connect my old Win98 machine to my old DOS laptop via the parallel printer port. I used both interlnk.exe and the direct cable connection application. I want to do that now with my Ubuntu machine and my DOS/Win95 machine. There's no other way to get files from my 486 to my Ubuntu machine except for disks and CDRs. Sadly I don't have any CDRs and I wouldn't want to waste them for simple file transfers anyway. I understand it involves recompiling the kernel for plip support. How do I do that? Or how do I find out if my kernel is already compiled with this capability?

Help is appreciated.

---

### Post by prshah on 2008-08-23
> **MusicallyInspired said:**
> 
 I know it's possible to connect a linux box to a DOS machine with something called "plip" but I don't know how to get plip working on my Ubuntu machine. Everywhere I look says that the module packages are for Debian and says not to use them in Ubuntu.


Ubuntu and Debian share a common root, so, unless specifically warned, Debian packages should work fine in Ubuntu.

plip is available as a module; you do not need to recompile the kernel; the following command will load it for you```
sudo modprobe plip
``` Beyond this, you're on your own, sorry, I didn't know anything about plip before this.

---

### Post by MusicallyInspired on 2008-08-23
Thanks very much. That's a start. Will I need to reboot after doing that?

And about the package, it did actually say that it was Debian specific and warned against using it on a Ubuntu system. But if it's already in there then that's great.

---

