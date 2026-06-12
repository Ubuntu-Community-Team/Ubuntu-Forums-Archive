---
title: "Scope of &quot;found new hardware&quot; adaptation?"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by KirbySmith on 2010-08-22
My question is: How far can Ubuntu (e.g., 9.10) go in tolerating booting up and discovering that the "malicious" operator has swapped out some part it has grown fond of?  I haven't read anything on this topic since Linspire provided a boot option for hardware discovery.

I know from my own limited actions of this type that PATA and SATA hard drives can be easily added and removed (although some ghost partitions may remain in Nautilus).  I suspect floppy drives and zip drives can come and go, and also suspect this is true of CD/DVD drives (although I haven't tested this yet).  USB hard drives seem swappable.

Another post response asserted that video cards should be swappable if the driver is removed before shutting down for the swap so I presume that to be true.  (Although for nVidia cards one might also want to revert to low res mode before the swap.)

How about swapping CPUs that are compatible with the MB?

How about entire motherboards, where Ubuntu resident on a hard drive that was installed on MB 1 with X vendor's chipset is used to attempt to boot MB 2 with Y vendor's chipset?

Thanks for any insights

kirby

---

### Post by oldsoundguy on 2010-08-22
I have swapped everything from drives and cards to migrating a hard drive with Ubuntu to a new box with EVERYTHING changed except the display at the same time and never had a major issue with  boot up other than having to re-install a couple of restricted drivers.

---

### Post by coffeecat on 2010-08-22
Linux (including Ubuntu) detects hardware on bootup and, so long as they  are compiled into the kernel or as loadable modules, appropriate  drivers are loaded into memory. Linux is very tolerant in this regard.  I've taken a hard drive out of one machine and put it into another  completely different one with different chipsets and Linux has booted up  just fine. If you search enough you'll find other people on this forum  who have done the same.

The only significant exception is if you are using a proprietary driver  for nvidia or ATI cards and try to change the card without deactivating the  proprietary video driver first.

> **KirbySmith said:**
> How far can Ubuntu (e.g., 9.10) go in tolerating booting up and discovering that the "malicious" operator has swapped out some part it has grown fond of?

Eh?

---

### Post by earthpigg on 2010-08-22
coffee cat is correct.

the only thing i would add is that his mention of proprietary drivers is true across the board, not just for video cards. wifi cards requiring ndiswrapper, for example, may also prove problematic. less so, of course, because you don't need wifi for a computer to be functional.

general outline of steps:

0) always have a solid backup on hand, of course, in case you drop a component or lightning decides to strike.

1) reduce your system to the point that you aren't reliant on proprietary components for anything.

2) do all your hardware swapping.

3) swap away.

4) boot.

---

### Post by KirbySmith on 2010-08-22
Thanks all.  I consider your information good news.  It implies that I can clone a drive and avoid having to go through replacing /home and trying to figure out what I have and haven't installed and what settings I made.

kirby

---

