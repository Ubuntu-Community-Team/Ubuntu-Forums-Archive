---
title: "Broadcom BCM4313: Notebook connected to wifi but no access to internet"
date: 2015-02-07
forum: Networking &amp; Wireless
---

### Post by Sarhad on 2015-02-07
Hello, 

I have a acer TravelMate P253-e and I have recently installed ubuntu on it alongside windows 7. I am connected to wifi but there is no connection to internet. Can you please help me in this ? I am new to ubuntu.

---

### Post by carl4926 on 2015-02-07
Open a terminal and do
ping 8.8.8.8

Tell us what happens

Are you connecting to a wifi in a University or such?

---

### Post by Sarhad on 2015-02-07
it says destination host unreachable. It's my home wifi, and I also tried to connect with a wired connection but unsuccessful.

---

### Post by carl4926 on 2015-02-07
Please post the result of

```
[COLOR=#000000][FONT=Sans Serif]lspci -nnk | grep -iA2 net[/FONT][/COLOR]

```

---

### Post by Sarhad on 2015-02-07
Here is is
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)	Subsystem: Acer Incorporated [ALI] Device [1025:0647]
	Kernel driver in use: tg3
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e042]
	Kernel driver in use: wl

---

### Post by Rob Sayer on 2015-02-07
I have that wireless adapter (BCM4313 with PCI ID 14e4:4727) on my netbook.  It is indeed pesky but the situation has improved over the last few versions.

Unfortunately, with these sort of things you have to know which release version you're running.  For example what worked for 12.04 won't work for later versions.

And I don't see the ubuntu release you're using anywhere in this thread.

One thing I would suggest is *not* installing the proprietary driver for the time being.

---

### Post by monkeybrain20122 on 2015-02-07
> [COLOR=#000000]I have that wireless adapter (BCM4313 with PCI ID 14e4:4727) on my netbook. It is indeed pesky but the situation has improved over the last few ver[/COLOR][COLOR=#000000]sions.[/COLOR]

Hi, I have exactly the same chip, it works perfectly out of the box with the built in open source brcmsmac driver (tested with Ubuntu 12.04, 14.04 , 14.10, Fedora 19, 20 and 21, strangely only time it doesn't work is Debian) You shouldn't have to install anything.  If you have installed bcmwl or other broadcom driver following some tutorials (or they may get installed when you install the OS if you check "install third party and proprietary software"), please remove them all and reboot.

---

