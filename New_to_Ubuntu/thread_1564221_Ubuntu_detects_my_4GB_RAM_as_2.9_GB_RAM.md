---
title: "Ubuntu detects my 4GB RAM as 2.9 GB RAM"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by ramujinius on 2010-08-30
Ubuntu lucid lynx detects my 4GB RAM as 2.9 GB RAM. Could someone tell me wats wrong? Windows 7 detect it as 4 GB

---

### Post by afroman10496 on 2010-08-30
> **ramujinius said:**
> Ubuntu lucid lynx detects my 4GB RAM as 2.9 GB RAM. Could someone tell me wats wrong? Windows 7 detect it as 4 GB

Are you sure it didn't fail?

---

### Post by LowSky on 2010-08-30
Do you have onboard video?

Did you install Ubuntu suing Wubi?

Both can effect the number you see.

---

### Post by dngfng on 2010-08-30
Even better question did you install the 64 bit version. Since the 32 bit can't recongnise more than roughly 3.2 gigs of ram the integrated graphics would eat up the rest down to the displayed value of 2.9 gigs easily.

---

### Post by howefield on 2010-08-30
> **ramujinius said:**
> Ubuntu lucid lynx detects my 4GB RAM as 2.9 GB RAM.

That's not at all unusual in a 32 bit install of Ubuntu.

---

### Post by migs73 on 2010-08-30
Mine did the same when running the 32bit kernel. 32bit can only address about 2.8-2.9 GiB.
Either change to the 64bit Ubuntu, or if you don't have a 64bit processor, check if your processor can be PAE (NX Bit) enabled (most newer ones can), and use the 32bit PAE kernel as I had to. See here for instructions;
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by dngfng on 2010-08-30
> **migs73 said:**
> Mine did the same when running the 32bit kernel. 32bit can only address about 2.8-2.9 GiB.
Either change to the 64bit Ubuntu, or if you don't have a 64bit processor, check if your processor can be PAE (NX Bit) enabled (most newer ones can), and use the 32bit PAE kernel as I had to. See here for instructions;
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Since windows can address a full 4 it must be a 64 bit compliant processor - 32 bit win can't handle more than 3.2 either.

---

### Post by migs73 on 2010-08-30
Not necessarily, IIRC Windows got so fed up with people moaning about not being able to see all their memory, that they patched it to report all the memory as seen by BIOS but it was not all addressable.

Also Windows reports in GB Ubuntu in Gib, a significant difference.

---

### Post by TNT1 on 2010-08-30
> **dngfng said:**
> Since windows can address a full 4 it must be a 64 bit compliant processor - 32 bit win can't handle more than 3.2 either.

> **migs73 said:**
> 

Also Windows reports in GB Ubuntu in Gib, a significant difference.

My pc has 64bit cpu and chipset, more than 3GB RAM, and Ubuntu 32 bit addresses it just fine.

See here for migs' statement:
[http://forums.highdefdigest.com/high-def-disc-faqs/17953-gb-vs-gib-explanation-storage-capacity.html](http://forums.highdefdigest.com/high-def-disc-faqs/17953-gb-vs-gib-explanation-storage-capacity.html)

---

### Post by migs73 on 2010-08-30
TNT1

Check to see if you are using the PAE kernel. It is supposed to download as the default kernel if your system has more than 3 GiB. For some reason it didn't with mine and I had to do it manually. Either that or its your 64bit processor.

---

### Post by howefield on 2010-08-30
> **migs73 said:**
> It is supposed to download as the default kernel if your system has more than 3 GiB. For some reason it didn't with mine and I had to do it manually.

If you don't have a working internet connection at the time of install, it won't. Perhaps that's what happened with yours ?

---

### Post by Boyohazard on 2010-08-30
I'm running Ubuntu 32bit PAE and it "sees" 3.9GiB of my 4.0.

---

### Post by migs73 on 2010-08-30
Boyo

not only does it 'see' 3.9GiB it can address it too. The only bottleneck is that the software you use will be 32bit so can only address about 3GiB at a time. But then that leaves you memory for other apps etc.

Howefield

My internet was fine. Don't have a clue why it didn't happen automatically (it missed it twice, once on an upgrade from Karmic and once on a clean install), but it is easily done manually anyway.

---

### Post by TNT1 on 2010-08-30
> **migs73 said:**
> TNT1

Check to see if you are using the PAE kernel. It is supposed to download as the default kernel if your system has more than 3 GiB. For some reason it didn't with mine and I had to do it manually. Either that or its your 64bit processor.

Yip, I use PAE kernel, that's why 32 bit Ubuntu works. I was just spinning up a 64 bit live cd to see if I'm good, and looks like that 64 bit pinguy distro I accidentally downloaded is gonna be used after all:D

---

### Post by uRock on 2010-08-30
The PAE kernel can use up to 64GB RAM for the OS, but a process can only use up to 2GB of it. That said, unless you are a developer or movie editor you should be fine with it. Just open Synaptic Package Manager and install it.

---

