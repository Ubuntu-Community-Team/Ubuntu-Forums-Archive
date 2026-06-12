---
title: "HELP - Trying to install a network driver."
date: 2015-09-02
forum: Networking &amp; Wireless
---

### Post by phoenixfire2 on 2015-09-02
Okay, so I'm trying to install the drivers for my new AWUS051NH network card, however when I do so it comes up with this [http://pastebin.com/G2mHzHfd](http://pastebin.com/G2mHzHfd)  So yeah I have no idea what I'm doing or what it's done or what the problem is... Whenever I look for help I see solutions like "Yeah just Tar backflip atom to the scale of square, export the vkjkxj file to the root en NASA ching ching" which basically, I have no idea what they're saying...  - An annoyed Linux user, I even got Ubuntu so It was 'user friendly'

---

### Post by ian-weisser on 2015-09-02
Trying to compile your own drivers is not a user-friendly activity.
Rather like trying to play a violin - it takes time for you to learn the skill sets before you can actually make music (non-cat-screeching) on the thing.
There is no 'user-friendly' way to make the hardware work if the manufacturer hasn't done their minimum job of contributing the driver to the Linux kernel.

You have three options:
1) Return the item, or exchange it for a similar product that is actually Linux-compatible. Vendor claims that compiling your own drivers means 'Linux-compatible' was acceptable in 1995, but not today. Any such vendor is shady and should not be trusted with your money.

2) Put the item in a drawer and wait a few months or years until the hardware is picked up by the Linux kernel in a future release of Ubuntu..

3) Spend time learning the skills so you understand how to Tar backflip atom to the scale of square. We can help you a bit with this, but there is no three-step process that covers all the contingencies (like your compilation failure). There will be a bit of back-and-forth helping you figure this out. And you will need to re-compile *all over again* each time you update to a new kernel...which may be a minimum of twice each year.

Which option do you wish to pursue?

---

### Post by mörgæs on 2015-09-03
> **ian-weisser said:**
> 
2) Put the item in a drawer and wait a few months or years until the hardware is picked up by the Linux kernel in a future release of Ubuntu..


Actually it's not that new after all. @Original poster, how did you conclude that the drivers are not already there in a standard install?

---

### Post by chili555 on 2015-09-04
> [COLOR="#FF0000"]2010[/COLOR]_0709_RT2870_Linux_STA_v2.4.0.1This file is far to old to compile on any recent Ubuntu version. As well, the 2870 suite of drivers is included by default.

Let's start by identifying your device. Please open a terminal Ctrl+Alt+t and run and post:```
lsusb
```Feel free to omit everything besides the wireless adapter.> "Yeah just Tar backflip atom to the scale of square, export the vkjkxj file to the root en NASA ching ching" :lolflag:

---

