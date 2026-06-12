---
title: "Ubuntu 9.04 instalation problems"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Hoxa on 2009-04-25
I've been sitting trying to instal Ubuntu 9.04 the last few days. I wanted to start off with dual boot, and then see if I could throw MS completely out of the window. The laptop is a Acer Aspire 7520g, and Ive heard that it is indeed possible to do.

I am also completely new to this, but here is what happends:

During installation, normally after the initial reboot, when the process is checking installation - it freezes. It will stay the same way for hours, or even turn off by itself. It has even affected the Vista stability, so that vista also would crash on loading. However that seems to have stopped, an Vista runs normally. I have recently format the drives. 

What I have tried:
- Ovbiously checking the CD I burned. I actually made 3 of them just to be sure, and I checked them in a program, saying they were working.
- I have tried both the 64bit and the 32bit - no change.
- I have tried all kinds of different installs. Through Windows, and from LiveCD - and on a number of different drives and partitions.
- I have tried graphic safe mode
- The last thing I did was to edit the kernes boot string in Grub, adding 
irqpoll pci=noacpi noapic nolapic acpi=off

Still - same error and nothing seems to improve.
Oh yes - it ran perfectly just testing the OS from LiveCD. WIFI, Mozilla and such all worked running from LiveCD, but it wont install. It even passes where the installation dont need the disk anymore, but it always does freeze. And not in at the same spot each time.

I have been reading through all kinds of forums these last days, and Im really sorry if I end up wasting your time. 

Thanks for any help.

---

### Post by The Cog on 2009-04-25
I don't think you should be having that kind of problem. Let's hope its not an issue with hardware.

As a last resort, I would be inclined to try the alternate installer, which is text mode only. Same questions though, so don't let the fact that it's text mode put you off. If you haven't got as far as partitioning the disk yet, I suggest that the best way to do it is to use Vista to reduce the size of its own partition, leaving some disk space unallocated. Then you can tell the Ubuntu installer just to use the available disk space and it will create the partitions it wants for itself.

---

### Post by Hoxa on 2009-04-25
All right, Ill try that. Thanks for the tip.

However, isnt the alternate version for low RAM machienes? This one has 2 gigs.
Also about the formatting. Im quite sure that the installer passes that stage, or atleast has once. I have tried installing it on a separate disk, and at same disk as windows in a different partition. I even tried the "inside windows" installation.

---

### Post by Sealbhach on 2009-04-25
Try 8.10 (Intrepid Ibex). It does work on your machine:

[http://georgia.ubuntuforums.org/search.php?searchid=58486174](http://georgia.ubuntuforums.org/search.php?searchid=58486174)

It might be something got changed on 9.04 and would need to be fixed in an update.


.

---

### Post by Hoxa on 2009-04-25
Ill download 8.10 as well. I sure hope this works.


Thanks for all the help. Cheers.

---

### Post by Hoxa on 2009-04-25
I downloaded the Ubuntu 8.10 (Intrepid Ibex) from [http://releases.ubuntu.com/8.10/](http://releases.ubuntu.com/8.10/) and burned it. I was crossing my fingers, and everything looked good for a while. Then under the last stages of install, it freeses again. Exactly same problem.

Now what ?

---

### Post by Sealbhach on 2009-04-25
Sounds like it could be some hardware issue. I would suggest try the alternate installer, then try Xubuntu, then try Linux Mint. One of them is bound to work.


.

---

### Post by Hoxa on 2009-04-25
Thanks.

Alternate iso is on the way down, and Im getting some more discs to burn.

Would there be major differnences between Ubuntu, Xubuntu (Guess its only a graphical differnence) and Linux Mint?

---

### Post by arashiko28 on 2009-04-25
Have you checked your RAMs? looks like there might be something. Also, the alternate installation looks like your best chance, if it happens again, which I doubt, you will get to see the real problem since it's text based, you'll get a message.

It actually looks like there's a problem with your laptop, I had it once with my old desktop.

---

### Post by Sealbhach on 2009-04-25
> **Hoxa said:**
> Thanks.

Alternate iso is on the way down, and Im getting some more discs to burn.

Would there be major differnences between Ubuntu, Xubuntu (Guess its only a graphical differnence) and Linux Mint?

Xbuntu is just Ubuntu with a different desktop environment - it uses Xfce rather than Gnome and Thunar file manager instead of Nautilus. Linux Mint is based on Ubuntu, and I only suggest it because it installed on a friend's computer although Ubuntu didn't.

.

---

### Post by The Cog on 2009-04-25
The alternate installer is for when you don't want to run the graphical GUI, for any reason. This could be due to a small amount of RAM, or due to compatibility issues between the graphical installer and the machine hardware. 

As someone else suggested, it may be worth running the memory test off the CD for a while, to eliminate memory as a suspect.

---

### Post by Didius Falco on 2009-04-25
I had this same problem with 8.10 and Beta versions of 9.04.  It about drove me nuts. It'd get to 97-98% done, then either just freeze or quit back to the Live CD desktop. If that's what is happening to you, this may very well be the answer.

Boot into the Live Cd using the "Make no changes to the PC" option.

Open a Terminal window (Applications/Accessories/Terminal) and in the Terminal window type ```
ubiquity --no-migration-assistant  
```Note the space between ubiquity and the two dashes. That'll start the installer, and you'll proceed as normally, except it won't offer to migrate your settings, and it should complete the install successfully.

One word of advice -  take a close look at your options when the install gets to the partitioning. 9.04 is much nicer about warning you, but if you just let the installer use the first selection, it'll wipe your Windows out and use the whole drive.

I hope this solves your problem.

---

### Post by Hoxa on 2009-04-26
I tried the alternate version, only to discover that that did not work either.
Good thing is though, I think Ive located the problem. As some have suggested, I think there is a hardware issue with my laptop, the issue being my RAM.

For some reason, both the Ubuntu disk checker, and the Vista tool freezes at 17%. However, this only effects the Ubuntu install, and does not disturb my Vista. Not noticable, anyway.

So, is there a way to fix these kind of RAM issues, or do I need to get some new ones ? If Vista will continue to work, I think Ill save the money, and keep Ubuntu on my other computer.

Thanks for the time and interest.

---

