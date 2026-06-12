---
title: "wifi is like 3 times slower than in Windows on my laptop"
date: 2016-09-03
forum: Networking &amp; Wireless
---

### Post by innn on 2016-09-03
Hi there,
I will begin saying the laptop is about 5 years old it's an Asus X54C. It actually came with Ubuntu back.
a lspci gives this as wlan card: Ralink corp. RT5390
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)

```
I had for a while arch linux  dual booting with windows. thinking I must have messed with networking configuration of sort I decided to try some other distro. I tested Manjaro then and posted on their forum as well and someone there encouraged me to have a look to something like Mint "as they package good drivers even with newer kernels." And ranking the mirrors and that did get the speed doubled and so within only a third reach of the windows speed. Now I've decided myself again for Ubuntu. But a speedtest got me where I left 3 times slower.
The only improvement compared to recent time on arch  is that does not disconnect itself. 
What can I do to have comparable to windows speeds with this wlan card?  Thanks.

---

### Post by innn on 2016-09-03
I think I got it now. After doing more research I stumbled upon this answer here [http://askubuntu.com/questions/815891/16-04-wifi-ethernet-issues-after-updating-from-14-04](http://askubuntu.com/questions/815891/16-04-wifi-ethernet-issues-after-updating-from-14-04)
where user Jeremy31 offered a config .service for systemd  that disables the power management for the wifi card. Don't know exactly if power management off is desirable but a speedtest got me almost where I get from Windows. Nice. Don't know still if it's solved, think I will wait a while and revisit the post. Cheers, Ubuntu is so much polished. I wish Asus made my laptop from aluminium instead of plastic and charged not a fortune.

---

### Post by innn on 2016-09-03
Sorry but Ubuntu does not behave as expected on my laptop. First the temps were always higher than in WIndows. 65-70 were the norm with browser open and terminal. 50-55 right after login nothing yet open. Having psensor as indicator in the panel was a bad idea eating 50% cpu. got rid of it. only using sensors in terminal now. I have  installed thermald, added intel pstate as boot parameter. situation slightly better. Now it boots 40 degrees C for the cores, 35 for temp1.  Yet in under 1 min it raises again 10 degrees. What could be? Had not opened anything yet. What I observed is that the wifi disconnects and searches itself again and that leads to increasing in temperature. 
Have I really a linux unfriendly wifi card in my laptop or can someone help me with the power management and systemd? I want it completely turned off if that's responsible for the constant search in wifi signal.
Also the speeds are again down. The indicator shows a 2-3 lines wifi strength and when disconnected my network barely makes the list of networks. Strange.

---

### Post by chili555 on 2016-09-03
Is your driver rt2800pci? Check:```
lsmod | grep rt2
```If so, may we see the result of:```
dmesg | grep rt2
```

---

### Post by 1200n on 2016-09-03
Same problem with a dell Inspiron 1545 (Broadcom). Wired = fast. Wireless = painfully slow

---

### Post by chili555 on 2016-09-03
> **1200n said:**
> Same problem with a dell Inspiron 1545 (Broadcom). Wired = fast. Wireless = painfully slowYou have a completely different device. Please ask a completely different question.

---

