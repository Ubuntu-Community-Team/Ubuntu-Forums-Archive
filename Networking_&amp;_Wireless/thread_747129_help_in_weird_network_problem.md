---
title: "help in weird network problem"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by ori_ab on 2008-04-06
Hi All,

I have a zd1201 based wireless USB dongle, and recently upgraded my hardware to c2d+p35 mobo (ich9).

I had gutsy installed and working without any problems. since i installed my new hardware i have a problem with activating the zd1201 - gutsy will soft lock when trying to access the network or run something, for example if i run ifconfig it will just sit there doing nothing and any other issued command after it will lock , i can do alt+f1 and alt+ctrl+del and system will shutdown as normal but i cant do anything else. sometimes i can get another terminal while a command is freezing but top shows nothing special, dmesg is normal, lsmod & lspci list the module (usb_uhci in lsmod), nothing in logs etc...when i try to manually unload/load the module i get the lockup during modprobe zd1201.
plugging & unplugging the dongle does not help, only message i get sometimes from dmesg is "rx urb failed: -84" after unplugging.

I tried reinstalling and installing hardy beta - best i could get is a working system in about 1/10 tries and even then i would hang after an arbitrary amount of time.

Since the card worked on my previous hardware i suspect it has something to do with bios settings or the ich9 controller on my mobo.

any ideas?

---

### Post by devurandom77 on 2008-04-15
I've encountered numerous buggy USB setups on different boards, including the ICH9 chipset...

Two random things to try are 1) disabling USB2.0 and 2) disabling firewire.

The latter doesn't make much sense, but I ran into that before with my old mobo.

---

