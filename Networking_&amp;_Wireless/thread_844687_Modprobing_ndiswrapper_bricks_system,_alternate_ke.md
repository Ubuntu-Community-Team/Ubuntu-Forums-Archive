---
title: "Modprobing ndiswrapper bricks system, alternate kernel's recover console fixed it."
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by m994301009 on 2008-06-29
So, I was getting ndiswrapper up and running, and I get to the modprobe stage, which I do, and it proceeds without any errors. I use dmesg to check that it modprobed properly and see that everything went fine. I then close my terminal, and proceed to check if my internet is working.
Its not, an neither does opening a Terminal, opening Synaptic, or even opening nautilus! Which, as you can imagine, is very, very bad. I try using the recovery console for the current kernel that I have, however, it notice that it loads the ndiswrapper module, and it doesn't work either (all commands hang)
I then boot into the recovery console for the older version of the kernel and it works fine, I modprobe -r the module, and then restart. Everything is now working perfectly.
Help Please!!!!

---

### Post by wabbalee on 2008-06-29
what kind of wireless chip do you have? see my post about conflicting native and proprietary drivers. [http://ubuntuforums.org/showthread.php?t=814117](http://ubuntuforums.org/showthread.php?t=814117) in case your chip is broadcom bcm43xx one

---

### Post by m994301009 on 2008-06-30
I can't actually determine the chip-set anymore, because ndiswrapper has decided that it will modprobe its-self every time in insert the USB. However, I know that the Chip-set is made my RealTek, and that it is a TEW-424UB version 3.1R. I found a tutorial that seemed to be for my chip-set, and it told me a certain driver to blacklist, but that didn't work, so i'm guessing that it wasn't actually my chip-set. You know anyway that I could stop ndiswrapper from automatically modprobing its-self when ever I insert the card so that I can tell you more helpful information?

---

### Post by wabbalee on 2008-07-19
I don't have experience with usb wireless cards but realtek is a very commonly used brand, may be there is somebody else with more experience who can say a few useful things here. i am still on the steep path of learning linux, i do try to stick with hardware that is likely to work with linux just to make things easier. sorry for not responding any sooner, i will have to change the way this forum notifies me.

---

