---
title: "Wireless Card Connecting to Network, But No Internet Connection"
date: 2016-04-12
forum: Networking &amp; Wireless
---

### Post by freesedevon on 2016-04-12
I'm running Ubuntu 14.04 on a Lenovo Z50-75 dual booting with Windows 10. Everything works fine on the Windows side, but when I switch to Ubuntu that's when things get weird. Wifi connects fine, I have internet access for about 10 minutes and then nothing. I can't get internet access unless I reboot again, and the cycle continues. Wireless card is a RealTek if that helps.

---

### Post by kurt18947 on 2016-04-13
Which Realtek chipset? There are quite a few and many display the behavior you describe. For starters, if it's an internal adapter run this command in a terminal and copy/paste the output:

```
lspci
```

If a USB dongle

```
lsusb
```

You should get something that looks like this:

00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880 [Radeon HD 4200]
01:05.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series]
[B]02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
[/B]

A wifi device might be called 'Network controller'. Once you know the chipset ID, you could search this forum for possible solutions.

There is also a wireless script that once run will provide much more detailed information about your adapter and network.

---

