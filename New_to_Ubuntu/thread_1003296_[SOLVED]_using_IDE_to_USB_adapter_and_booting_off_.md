---
title: "[SOLVED] using IDE to USB adapter and booting off linux?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by aimpau on 2008-12-05
Is it possible for me to use an IDE-xubuntu with an IDE to USB adaptor and have it boot up on a DELL laptop?

---

### Post by ddixonr on 2008-12-05
I would be curious to see that work. I own one of these and I love it. Best troubleshooting device I've ever purchased.

I wish I could help, but can't spare a hard drive to test it out.

---

### Post by Shazaam on 2008-12-06
It should show up as a removable device on a normal boot. If you want it to boot first the Dell has to be able to boot from USB (check your bios).

---

### Post by aimpau on 2008-12-06
The reason why I'm doing this is that my friend's dell is running on XP and whenever we try to switch to an LCD projector, it doesn't work and no matter what I do to tinker it and it's nvidia control panel, no luck. Then, I made a xubuntu persistent USB, installed all needed graphics driver and worked....imagine that...

But it's just 2gb and besides, it is really dragging (obviously since it's USB), thus I want my HD xubuntu to boot up to her laptop instead.

*sigh* Where would windows be if it weren't for linux?


edit:
Yup, it's already up in the bios but should I put in usb-zip or usb-hdd?

edit 2:
oh and just to mention...i had compiz installed in the usb persistent too..:)

---

### Post by anewguy on 2008-12-06
Is there room on the lasptop disk to shrink the XP partition and install Ubuntu?  If so, you could dual-boot, using XP when you need to and using Ubuntu when you want to.

Post back if you have any questions on doing all of it.

Dave ;)

---

### Post by barbedsaber on 2008-12-06
It would be USB hdd probably, but this would not fix your speed problem. The install would only be as fast as the slowest part. The slowest part would be the USB (I don't know the exact speed, but assuming its USB 2.0, a hell of a lot slower than an installed HDD) also, not all portable hard drives like being booted from.
never the less, I wish you luck.

---

### Post by anewguy on 2008-12-06
Yes, but since he'd like it on her laptop, the internal drive wouldn't be USB, and if there's room on it why not just dual-boot Windows XP and Ubuntu?  A small Linux installation won't take up that much room and you'd get the speed gain from the internal bus and wouldn't have to worry about forgetting some USB device at a time when they want to use the projector.

Dave ;)

---

### Post by aimpau on 2008-12-06
1. i have a desktop running on dual boot with 2 hdd, one xp, one xubuntu so yep, I know the speed difference.

2. barbedsaber: that's what I was also thinking but probably since it's a parallel IDE to a USB, it wouldnt be that slow? I'll try it out anyway. :)


edit:
3. can't do the repartitioning. owner is very "strict" if you know what I mean. :D

---

### Post by barbedsaber on 2008-12-06
> **aimpau said:**
> 
3. can't do the repartitioning. owner is very "strict" if you know what I mean. :D

far to well I am afraid. (you want to do what!?!?!,
install flash so you can watch youtube videos.
Sounds like a virus, no, I can live without youtube.
:rolleyes

---

### Post by aimpau on 2008-12-06
she went all crazy when she saw the command prompt instead of a WinXP loading...:D

---

### Post by barbedsaber on 2008-12-06
> **aimpau said:**
> she went all crazy when she saw the command prompt instead of a WinXP loading...:D

i feel your pain.

---

