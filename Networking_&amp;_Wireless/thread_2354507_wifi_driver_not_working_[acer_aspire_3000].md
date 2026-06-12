---
title: "wifi driver not working [acer aspire 3000]"
date: 2017-03-03
forum: Networking &amp; Wireless
---

### Post by dumble on 2017-03-03
Hej guys,

I just installed lubuntu 14.04.5 on an old acer aspire 3000. The wifi is not working. I went to additional drivers and selected the one in the screenshot
[ATTACH=CONFIG]273968[/ATTACH]
But during install I gave an error, and when I reported the bug, it said bug was already known and sent me to this page:
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1594974](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1594974)

Does anyone know how to fix this?

Here is an inxi report:
```
almu@almu-Aspire-3000:~$ inxi -Fx
System:    Host: almu-Aspire-3000 Kernel: 4.4.0-64-generic i686 (32 bit, gcc: 4.8.4) 
           Desktop: LXDE (Openbox 3.5.2) Distro: Ubuntu 14.04 trusty
Machine:   System: Acer product: Aspire 3000
           Mobo: Acer model: Lugano M Bios: Acer version: 3A32 date: 02/20/06
CPU:       Single core Mobile AMD Sempron 3100+ (-UP-) cache: 256 KB flags: (nx pae sse sse2 sse3) bmips: 1600.19 clocked at 800.00 MHz 
Graphics:  Card: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter bus-ID: 01:00.0 
           X.Org: 1.18.3 driver: vesa Resolution: 1024x768@61.0hz 
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.8, 128 bits) GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller 
           driver: snd_intel8x0 ports: 1400 1c80 bus-ID: 00:02.7 
           Sound: Advanced Linux Sound Architecture ver: k4.4.0-64-generic
Network:   Card-1: Broadcom BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller bus-ID: 00:0b.0
           IF: N/A state: N/A mac: N/A
           Card-2: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet driver: sis900 port: 1800 bus-ID: 00:04.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: 00:16:36:20:a8:f1
Drives:    HDD Total Size: 87.8GB (4.8% used) 1: id: /dev/sda model: HTS541080G9AT00 size: 80.0GB temp: 32C 
           2: USB id: /dev/sdb model: DT_Mini_Fun_G2 size: 7.8GB temp: 0C 
Partition: ID: / size: 73G used: 3.3G (5%) fs: ext4 ID: swap-1 size: 1.00GB used: 0.04GB (4%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 49.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 163 Uptime: 1:10 Memory: 427.3/935.3MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 
almu@almu-Aspire-3000:~$ 

```

---

### Post by howefield on 2017-03-03
Thread moved to the "*Networking & Wireless*" forum, probably a better fit to get help with a wireless adapter issue.

---

### Post by chili555 on 2017-03-03
> Does anyone know how to fix this?bcmwl-kernel-source is likely the wrong driver. Please check here: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by dumble on 2017-03-04
Thanks chili555, the steps in that thread worked for me! I am now connected to wifi :). After the messed up graphic drivers and wifi not working there is but 1 thing left to fix: the bluetooth is stil not working, is there also a fix for that?

---

### Post by jeremy31 on 2017-03-04
If the bluetooth is also part of the wifi card it likely needs firmware that needs to be converted from the windows driver, see [http://askubuntu.com/a/632348/300665](http://askubuntu.com/a/632348/300665)

---

