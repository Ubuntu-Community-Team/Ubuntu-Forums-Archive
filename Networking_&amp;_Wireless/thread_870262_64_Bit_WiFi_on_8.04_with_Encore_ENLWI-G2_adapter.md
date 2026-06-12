---
title: "64 Bit WiFi on 8.04 with Encore ENLWI-G2 adapter"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by wg5o on 2008-07-25
I actually have two questions:

1.  Ubuntu 8.04 has ndiswrapper built-in (System, Administration, Windows Wireless Drivers), yet all of the guidance I find instructs the user to download and install ndiswrapper manually.  What am I missing here?

2.  The real problem:  I am running 8.04 on a generic AMD Athlon 64 PC with two hard drives, one for Windows XP and one for Linux. After months of fruitless struggle, I finally learned (via dmesg listing) that ndiswrapper won't install a 32 bit driver for a 64 bit system.  I downloaded a 64 bit driver and it installed OK:

"andy@izzy:~$ ndiswrapper -l
net8185x64 : driver installed
	device (10EC:8185) present"

But it causes the terminal to lock-up (never return to the prompt) when I try to load the driver with "sudo modprobe ndiswrapper."

Is there a way to continue?  

Andy Pickens
San Antonio, Texas

---

