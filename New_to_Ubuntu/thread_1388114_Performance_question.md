---
title: "Performance question"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by pankirk on 2010-01-22
I have tried to install Ubuntu many times over the years and I have found that none of the installs go well at all. They all seem to lag!

I have contemplated this issue for hours on end and I would love to find a solution because my hate for windows is beginning to take over.

I believe that my video card (nVidia 8800gt 512MB). This card was produced about two to three years ago so I would say probably in 2007 or 2008.

Each and every time I install Ubuntu (distros 7.10 to 9.10) I install all of the correct drivers and all of the updates. For the video drivers I tried all sets. New drivers, beta drivers, patched drivers, everything.

The rest of my computer hardware is as follows:
AMD athlon 6000+ dual core 3.0ghz,
4gb OCZ ram,
raptor hard drive 10,000RPM,
and an asus crosshair mobo.

As you can see, running Linux on this machine really shouldn't be a problem.

I have used versions of windows XP filled to the brim with crap ware, spy ware, bloatware, and any kind of "ware" you can think of and it still ran better then Ubuntu.

Some things that bothered me in Ubuntu are:
Slow firefox start up,
desktop lagging,
and a LOT of Window shuttering.

Like I said before, this really shouldn't be happening on my machine. I know it's a little old, but she should still be able to run such a light OS.

Can anyone think of a solution to this extreme lag and my 8800gt video card?

Thanks a lot,
-P

---

### Post by pankirk on 2010-01-22
Just bumping to make sure I can get a reply just like everyone else.

---

### Post by reclinerspud on 2010-01-22
Have you tried  Envyng it is in senaptic  it wil install the proper video driver an set it up for you.

---

### Post by Sylslay on 2010-01-22
About Intel Video performance 845GV chipset on Ubuntu from 8.04-9.10 and boot time.

8.04 youtube play ok,
9.04 youtube play ok on small window.
9.10 youtube play ok but system very offten is not switched on witch Xorg, no grahic mode.

Now about new driver "mode"
EXA,slow
UXA, better quality , but longer boot.

[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#Problem:%20%20Huge%20performance%20drop%20with%20UXA%20due%20to%20tiled%20rendering%20disabled](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#Problem:%20%20Huge%20performance%20drop%20with%20UXA%20due%20to%20tiled%20rendering%20disabled)

I am most happy with this setings in xorg.conf file : (switched from EXA to UXA mode)

Section "Device"
Identifier "Configured Video Device"
Driver "intel"
BusID "PCI:0:2:0"
Option "XvMC" "true"
Option "AccelMethod" "uxa"
Option "Tiling" "true"
VideoRam 131072


[http://tuxradar.com/content/modify-xorgconf-better-performance](http://tuxradar.com/content/modify-xorgconf-better-performance)

ready for tune?

---

### Post by pankirk on 2010-01-22
Hi reclinerspud, thanks for the reply!
I have actually tried the envy method. I have also tried to install the drievers directly from nvidia. I feel installing the drivers from nvidia is the best way, but when you go to update your kernel they crap out on you!

Sylslay, I have no clue what you just said... Sorry

---

### Post by warfacegod on 2010-01-22
You should use the drivers from nVidia only if the Ubuntu's recommended driver isn't working properly. The newest manufacturer drivers generally aren't tested very well yet and don't always have good compatibility.

In  my experience, Firefox has always been sluggish at opening in Linux and Windows, especially with add-ons. Try Swiftfox. It's Firefox with the settings tweaked for performance.

By the way, are you running 32 0r 64 Bit Ubuntu?

---

### Post by pankirk on 2010-01-22
Hi, warfacegod.

I haven't tried swiftfox yet. I will most definetly try that once I install Ubuntu. My current version of Ubuntu that I have downloaded is 32 bits. I know my CPU does in fact support 64 bits, but I have read all online that some programs don't work in Ubuntu 64bit linux.

Thanks!

---

### Post by warfacegod on 2010-01-22
You might want to give it a try. 64 Bit support is very good now and your computer will almost certainly be faster. It may take a day or two though. It's allot like breaking in a new car, it can take a while.

---

