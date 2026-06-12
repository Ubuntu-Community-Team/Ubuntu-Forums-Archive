---
title: "inotify_add_watch boot ERROR"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by Oathanvil on 2011-02-21
OK been in Google for the better part of a week musing over this DOS screen error at startup, just after you type in the Ubuntu login password and just before you see the desktop load.

I managed to get the whole line of error code and wrote it down.


[PHP]udevd-work[130]: inotify_add_watch(6, /dev/dm -1, 10) failed:No such file or directory
[/PHP]Now up front I use two 1T or terabyte drives in a RAID0 configuration. this of course equals 1T even.

My chip-set is off the new ASUS Crosshair Extreme Motherboard, chipset is [FONT=arial][SIZE=2]890FX[/SIZE][/FONT] and I use an Nvidia GTX 470 GPU. The CPU is a Phenom II 6 core and RAM is 8 Gig of Corsair 1600 MHz can go 2000 MHz ;)

Ubuntu installed the chipset and audio and all other hardware devices at point of install with no issues at all.

Later after installing all software updates is when I first noticed this ERROR message at startup.

I also have Ubuntu as the second OS on this computer on its own 200 gig partition.

Windows7  was the first install and maintains the rest of the hard drive space.

My Ubuntu install is on \ root 200 gig of space with a 16 gig swap file that's x2 my hardware RAM size of 8 gig and the remaining disk space is on the \home directory.

I have read many articles this week on the error and one ubuntu forum poster described installing "Cryptsetup" to resolve the issue. I suppose the premise is that it writes some new HD handling software that resolves the text error at startup.

I installed "cryptsetup" from the Synaptic Package Manager however upon restarting the computer the inotify_add_watch error remains it did not remove it or mask the issue.

It was mentioned in the post by another as not a solution!

Any ideas on this would be greatly appreciated of course I am a noob to Linux so you will have to give a step by step instruction on any fix thank you.

---

### Post by Oathanvil on 2011-02-21
Sorry to bump I still have the issue! Anyone have an idea?
 
signed mad as a hatter and no alice to pilfer for sanity.:rolleyes:

---

### Post by Oathanvil on 2011-02-22
Still wondering if anyone else is having this issue?

---

### Post by mutt|ey on 2011-02-23
I don't why ...and i don't know if a good things...

...but if install cryptsetup fix the problem ([http://ubuntuforums.org/showthread.php?t=1500937](http://ubuntuforums.org/showthread.php?t=1500937))

---

### Post by skrieder on 2011-11-01
What commands did you use to install cryptsetup?

And did you write blocks to your entire hard drive or just install it?

---

