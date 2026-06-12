---
title: "Freezing problem"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by ryansanchez88 on 2011-02-21
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)

product: GT5674
vendor: Gateway
version: Unknow
serial: xxxxxxxxxx
width: 32 bits
capabilities:
    SMBIOS version 2.4,
    DMI version 2.4,
    SMP specification v1.4,
    Symmetric Multi-Processing
configuration:
    boot: normal
    chassis: desktop
    cpus: 4

-------------------------------------------
I'm having a lot of freezing issues, mainly when browsing quickly or watching a video through a browser. When it freezes audio usually continues to play but mouse and all input is gone. The time is not updated on the monitor either. I always have to do a hard reset. I'm thinking it's some hardware issue because I ran Windows Vista before installing ubuntu and it had some blue screen errors.

I will gladly respond with var/log/ information but I need to know what to respond with.

Thanks for reading!

BTW I'm a total noobie and this freezing issue is a real pain!

---

### Post by ajgreeny on 2011-02-21
It could also be a ram problem, so use the memtest86+ from grub, letting it run for several hours or overnight, and check if any errors are shown in the readouts at the bottom.  If you don't normally see grub, which you may not if ubuntu is the only OS on the computer, hold shift at boot up, andd the menu should appear.

If that is all clear, I would agree that it may be related to the graphics card/driver combination

---

### Post by Keiran230 on 2011-02-22
> **ryansanchez88 said:**
> ...mainly when browsing quickly or watching a video through a browser....

This sounds like a power supply issue to me, but you should still test your RAM first. The parts in a power supply die with age, and cause symptoms like this when performing more stressful functions on the hardware ,such as watching a video

---

