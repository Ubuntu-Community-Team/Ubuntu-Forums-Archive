---
title: "Optimization?"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by Pizack on 2010-07-12
Is there something like an optimization guide out there?  I'd like info on stuff like how big is optimal for a swap file, what graphic effects use the most resources, the best way to make file transfers between drives or partitions go quickly and smoothly. Just some general pointers so that I can have some productive fun tweaking around with some settings without blindly stumbling and creating problems for myself.  Thanks!

---

### Post by cbowman57 on 2010-07-12
Google vm.swappiness and blockdev, use rcconf to turn off unneeded services, check your autostart options for things you don't use.

My system uses 2Gb of RAM so I don't even have a swap partition.  In the event that it needs one I use one of the swap file daemons that just creates one as needed.

As far as effects go, just like Windows, the more you use the more system resources are used.

That's a start.

---

### Post by Pizack on 2010-07-12
Thanks much. Ubuntu is simple to use, and problems are simple to fix;  but as far as minor problems that are fairly unnoticeable but cause slowness in computing or booting, or just general optimization (as I'm going for) its kinda hard to figure out where to start.  Any websites that focus on the subject matter would be great to have links to as well.

As far as the swap issue, I've got 4GB of RAM, and a 500GB hard drive.  Figured throwing 2GB away as an investment in a swap partition would be harmless, and could only help.  Plus the installation guide I was using suggested doing that if you had another OS already, which, at the time, I did.

---

### Post by marshmallow1304 on 2010-07-12
If you want to be able to use Hibernate (suspend to disk), you'll need
swap partition >= RAM

Otherwise, 2 GB swap should be fine for 4 GB RAM.

---

### Post by Paqman on 2010-07-12
With 4GB RAM I would definitely wind your swappiness way down, probably to 0. Once you've done that you're highly unlikely to ever use swap, so you could shrink or remove it if you wanted.

Installing preload is an excellent optimisation, too. I don't really know why it's not installed by default.

---

### Post by libssd on 2010-07-12
"It depends"; you're likely to get thousands of different (often conflicting) opinions. I run Ubuntu on a netbook, and turning off desktop effects speeds things up noticeably:

Appearance > Visual Effects > None

There are many guides to tuning solid state drives.

---

### Post by mike555 on 2010-07-12
You could turn off unneeded things in : System > Preferences > startup apps ............. like bluetooth, file sharing, etc.

---

### Post by Pizack on 2010-07-12
I was wrong, removed

---

### Post by TheForumTroll on 2010-07-12
Guides to speed up Ubuntu is easy to find on Google but as another poster said you are going to find lots of opinions - most not worth following unless you meet the same criteria as the guide writer. Like running Ubuntu on a notebook, using an integrated gfx card, etc. If you do find some guides to follow I would recommend you to first get a baseline to compare with. If you don't know how fast your system is now it will be hard after a few tweaks to see what works and what does not.


An easy one to start with is getting you boot time down as [BootChart]("https://wiki.ubuntu.com/BootCharting") will show you the difference on a nice chart.

Some of the tweaks I have done to my own system is disabling swap and [mounting the /tmp dir as tmpfs]("http://megabytemorsels.blogspot.com/2009/05/using-tmpfs-for-tmp-with-ssd-in-ubuntu.html") so it is completely in RAM as no matter what I do Ubuntu can't use all my RAM anyways. Other uses could be creating a ramdisk for an app you use a lot eg. [Firefox]("http://wiki.archlinux.org/index.php/Speed-up_Firefox_using_tmpfs").

---

### Post by oldos2er on 2010-07-12
Have you looked in the Tips & Tutorials subforum here? I seem to recall some optimization info there, but I haven't looked in there for awhile. FWIW, make a note of the date of any tips you intend to try out; lots of things have changed in Ubuntu over the last 4 - 5 releases.

---

### Post by ov3rcl0ck on 2010-07-12
> **Pizack said:**
> Is there something like an optimization guide out there?  I'd like info on stuff like how big is optimal for a swap file, what graphic effects use the most resources, the best way to make file transfers between drives or partitions go quickly and smoothly. Just some general pointers so that I can have some productive fun tweaking around with some settings without blindly stumbling and creating problems for myself.  Thanks!

If you're looking for optimization, then you're looking at NO graphical effects, probably logging into a shell/command prompt, tinkering and benchmarking harddrive configurations, disabling splash screen for ubuntu, and basically just cutting out all these pretty little effects and tuning the kernel and such to your hardware.

---

### Post by Paqman on 2010-07-12
> **TheForumTroll said:**
> 
Some of the tweaks I have done to my own system is disabling swap and [mounting the /tmp dir as tmpfs]("http://megabytemorsels.blogspot.com/2009/05/using-tmpfs-for-tmp-with-ssd-in-ubuntu.html") so it is completely in RAM as no matter what I do Ubuntu can't use all my RAM anyways. Other uses could be creating a ramdisk for an app you use a lot eg. [Firefox]("http://wiki.archlinux.org/index.php/Speed-up_Firefox_using_tmpfs").

+1 to all this. Since /tmp is wiped every boot, there's no reason to have it on a drive IMO. If you've got the RAM, stick it there.

---

### Post by Pizack on 2010-07-12
Original bootchart benchmark ~37 seconds.
After swappiness from 60 to 5 = ~35 seconds.
After tmpfs = ~26 seconds.

Jolly good show ladies and gentlemen.

I saw fsck in both of them. I know it usually scans every 30 boots or every 30 days, but does it start to check that anyway or am I seeing a scan in here?

---

