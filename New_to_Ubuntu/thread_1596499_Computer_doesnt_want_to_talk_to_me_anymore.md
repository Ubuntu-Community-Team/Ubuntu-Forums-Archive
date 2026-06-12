---
title: "Computer doesnt want to talk to me anymore"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by Alienspecimen on 2010-10-14
I have a three year old Gateway laptop.
 
Last night I played a video on youtube and it froze midway, but the sound was on. This is not the first time it happened.
 
About an hour later, I went to use it again and was greeted by a dark screen. The mouse cursor was moving, but nothing else was happening. Normally, I would expect to see my screensaver.
 
Nothing helped, so I decided to rebooot. Bad idea, I see now a lot of stuff on my screen now, most notably:
 
] mount: mounting/dev on root/dev failed: No such file or directory
 
] mount: mounting/dev on root/dev failed: No such file or directory
 
there is also bunch of other stuff in between from which I remember that it has detected the battery only and it all ends with this:
 
] no init found. Try passing init=bootary
 
] Busybox v1.13.3 (Ubuntu 1:1.13.3-1Ubuntu11) built-in shell (ash)
 
] Enter 'help" for a list of built-in commands
 
] (initramfs)
 
I started entering commands from the list that "help" provided, but stopped, when one (I dont remember which went into some loop and wouldnt stop displaying letter "y" under any circumstances...so I had to reboot again.
 
Upon that, I went to the BIOS and was surprised to see that the computer has two options only when it comes to OS: XP and Vista. It is set on first now, but if I remember, it came with Vista. I guess this is the time to say that I am not doublebooting, I just have the latest Linux OS from Ubuntu installed...
 
Where do I go from here?
 
Thanks in advance
 
Boris
 
P.S. I have had Linux for the last seven months with absolutely no other problems, but the one described when on youtube the video would freeze and the whole screen will loose its colors for about ten seconds, during which you cant do anything, but the sound will be still on...happens about once or twice a week.

---

### Post by CharlesA on 2010-10-14
Try to boot into recovery mode and see what sort of errors it throws up.

---

### Post by SlugSlug on 2010-10-14
Do you have more than one hard drive..  with that grub mistery it sounds like your hard drive boot order has changed ( or SDA has been unplugged )

---

### Post by Alienspecimen on 2010-10-14
> **CharlesA said:**
> Try to boot into recovery mode and see what sort of errors it throws up.
 
Sorry for the stupid question, but this is a beginners talk forum.  How do you boot into recovery mode?
 
The first thing that I see is whatever I described above, well, after the option to go into BIOS of course.  I am guessing some sort of a key sequence?
 
Thanks
 
Boris

---

### Post by CharlesA on 2010-10-14
Before the OS starts to load, hold down shift to get the grub menu and select recovery mode from there.

---

### Post by Alienspecimen on 2010-10-14
> **SlugSlug said:**
> Do you have more than one hard drive.. with that grub mistery it sounds like your hard drive boot order has changed ( or SDA has been unplugged )
 
I dont have a second hard drive.
 
I did notice in the BIOS that the computer is setup to boot from the CD first.  I dont know if this always has been like that.  I am guessing the suggesting is to set it up to boot from the hard drive first?
 
Best
 
Boris

---

### Post by CharlesA on 2010-10-14
This should have nothing to do with the BIOS.

If you see Vista or XP, then you are probably looking at the grub menu.

---

### Post by Alienspecimen on 2010-10-14
> **CharlesA said:**
> Before the OS starts to load, hold down shift to get the grub menu and select recovery mode from there.
Thanks for the advice. I did follow, went into recovery mode and here is what I got:
 
fsck from util-linux-ng 2.17.2
/dev/sda1 contains a file system with errors, check forced
/dev/sda1: Inodes that were part of a corrupted orphan linked list found.
 
/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
mountall: fsck / [392] terminated with status 4
mountall: Filesystem has errors: /
 
 
What does this mean
 
Thanks in advance
 
Boris

---

### Post by CharlesA on 2010-10-14
Ok. You need to run fsck manually. Boot off a livecd and run this:

```
sudo fsck -Cf /dev/sda1
```

---

### Post by Alienspecimen on 2010-10-14
> **CharlesA said:**
> Ok. You need to run fsck manually. Boot off a livecd and run this:
 
```
sudo fsck -Cf /dev/sda1
```
 
 
Sorry, I am guessing you mean that I need to create an image on an USB drive and boot from there.
 
Then I will be entering the code from the terminal?
 
Thanks 
 
Boris

---

### Post by CharlesA on 2010-10-14
Yeah. I'm not sure if you can do a fsck from a root prompt or not, so it's better to just boot off a livecd/liveusb and do it from there.

---

### Post by renkinjutsu on 2010-10-15
Yes it's possible to run fsck from the rescue prompt.

As I recall (long time ago), I was able to do a manual fsck right after it told me to do a manual fsck.

---

