---
title: "Netgear AC600 Dual Band Wireless AC Adapter"
date: 2016-02-07
forum: Networking &amp; Wireless
---

### Post by josh165 on 2016-02-07
Hi All,

First let me preface I am extremely new to Linux. I basically know sudo apt-get update and sudo apt-get install.

I just bought a Netgear Wireless AC adapter AC600 dual band because linux does not recognize the original Wireless card inside my PC (the infamous Qualcom-atheros device).  So this was suppose to be my work around. and now of course more problems.

I even installed Wine and Playonlinux and to install the drivers and software that way. It fails with an error message.

I have followed many many forums and instructions from many different threads and nothing works. Here is one such example that didn't work ([http://askubuntu.com/questions/568056/usb-wireless-netgear-adapter](http://askubuntu.com/questions/568056/usb-wireless-netgear-adapter))

My computer is a Lenovo G50-45 running on AMD A8 with 4gb ram.

I am really new to linux if its easier for someone to connect to my computer I may consider that. I am at a total dead end here please put any directions and steps in very basic step by step commands. Thanks in Advance

---

### Post by Geoffrey_Arndt on 2016-02-08
Yes  no need to say you're new to Linux . . . ;)

The atheros chipsets are generally very Linux friendly - - some are actually open source and are plug and play.   But of course, we would need to know "which" atheros chipset your adaptor is using.   One way to find out is to install the program "inxi".   After install, open the terminal and run this:
  
  inxi -Fx 

Other methods to ID hardware:


 [http://www.binarytides.com/linux-commands-hardware-info/](http://www.binarytides.com/linux-commands-hardware-info/) 

.....................................................................................................................................................

Now, if you want the simplest alternative - a true plug and play adaptor that works well on Ubuntu & most other Linux flavors - - see:

[http://http://www.pandawireless.com/](http://http://www.pandawireless.com/)

For laptops, I prefer the nano size Panda Ultra 150 b/g/n dongle

The Panda Ultra 150 device costs about $10.00 on Amazon or similar sites such as EggHead, etc.    Well worth it.

---

### Post by howefield on 2016-02-08
Thread moved to the "*Networking & Wireless*" for better support.

---

### Post by josh165 on 2016-02-08
If I could get the Qualcom wireless network adapter to work that would be ideal. The netgear one is not ideal for HD movie streamings.


System:    Host: joe-Lenovo-G50-45 Kernel: 3.19.0-50-generic x86_64 (64 bit, gcc: 4.8.2) 
           Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: LENOVO product: 80E3 version: Lenovo G50-45
           Mobo: LENOVO model: Lancer 5B2 version: 31900058 WIN Bios: LENOVO version: A2CN34WW(V2.02) date: 02/28/2015
CPU:       Quad core AMD A8-6410 APU with AMD Radeon R5 Graphics (-MCP-) cache: 8192 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 15970.6 
           Clock Speeds: 1: 2000.00 MHz 2: 2000.00 MHz 3: 2000.00 MHz 4: 2000.00 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Mullins [Radeon R4/R5 Graphics] bus-ID: 00:01.0 
           X.Org: 1.16.0 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1366x768@60.0hz 
           GLX Renderer: Gallium 0.4 on AMD MULLINS GLX Version: 3.0 Mesa 10.3.2 Direct Rendering: Yes
Audio:     Card-1: Advanced Micro Devices [AMD] FCH Azalia Controller driver: snd_hda_intel bus-ID: 00:14.2 
           Card-2: Advanced Micro Devices [AMD/ATI] Kabini HDMI/DP Audio driver: snd_hda_intel bus-ID: 00:01.1 
           Sound: Advanced Linux Sound Architecture ver: k3.19.0-50-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
           driver: r8169 ver: 2.3LK-NAPI port: 2000 bus-ID: 02:00.0
           IF: eth0 state: down mac: 68:f7:28:c8:58:16
           Card-2: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter bus-ID: 01:00.0
           IF: N/A state: N/A mac: N/A
           Card-3: Atheros usb-ID: 004-004
           IF: N/A state: N/A speed: N/A duplex: N/A mac: N/A
           Card-4:  NetGear A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU] driver: rtl8812au usb-ID: 001-002
           IF: wlan0 state: up mac: dc:ef:09:d2:d9:14
Drives:    HDD Total Size: 500.1GB (4.4% used) 1: id: /dev/sda model: ST500LT012 size: 500.1GB temp: 29C 
Partition: ID: / size: 455G used: 21G (5%) fs: ext4 ID: swap-1 size: 3.72GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 40.2C mobo: N/A gpu: 40.0 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 215 Uptime: 19 min Memory: 702.8/3344.9MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17

---

### Post by Geoffrey_Arndt on 2016-02-08
It's been a about 5 or 6 years since I've built a realtek driver, but the process is mostly the same (just updated drivers).  

For the non-techie, compiling software is a bit more challenging than doing debian apt-get installs (or using the Ubuntu Software Center).

But here's a website that's got good info on how to build & install the driver:

[https://sites.google.com/site/easylinuxtipsproject/reserve-7](https://sites.google.com/site/easylinuxtipsproject/reserve-7)

Note:    you probably should not refer to these drivers by labeling them "Qualcom" . . . . but rather "Realtek".   Be aware you may have to repeat these steps upon updating the kernel.

Note2:   you want the Realtek 8812AU driver

............................

These days, I just much prefer the convenience of installing the Panda devices.   Makes it a no-brainer (and no reinstalls needed).

---

### Post by Geoffrey_Arndt on 2016-02-09
Josh . . . regarding the Atheros driver . . . . apparently the patch is in the newest kernel - - what version of Ubuntu are you running?   You may have to bump up to 16.04 Xenial.   This driver has been an issue on several distros inluding Ubuntu, Fedora, Suse, etc.
...........................................................................
Besides the Panda 150 Ultra . . . which works great on all my Linux boxes (5) . . . I have a list of another 1/2 dozen adaptors that I've personally tested and work with Ubuntu - - most cost between 10 & 25 usd max.   Let me know if interested.

---

### Post by jeremy31 on 2016-02-09
Josh, does the Atheros show up in ```
lspci -nnk | grep -iA2 net
```
as ```
[COLOR=#000000]03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
```

I do have a fix for that chipset, it has been confirmed here, on askubuntu.com and the bug report.  But it might not work on a UEFI install based on comments on the bug report.  It is a dkms deb package that will work with 3.19 kernels[/COLOR]

---

### Post by josh165 on 2016-02-09
@ Jeremy31 see below output

joe@joe-Lenovo-G50-45:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3812]
    Kernel driver in use: r8169




joe@joe-Lenovo-G50-45:~$ uname -a
Linux joe-Lenovo-G50-45 3.19.0-50-generic #56~14.04.1-Ubuntu SMP Thu Feb 4 11:25:43 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux




The USB driver works so I cant complain but ideally the built-in one should work better.


@Geoffrey_Arndt
joe@joe-Lenovo-G50-45:~$  lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty







joe@joe-Lenovo-G50-45:~$ uname -a
Linux joe-Lenovo-G50-45 3.19.0-50-generic #56~14.04.1-Ubuntu SMP Thu Feb 4 11:25:43 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux



Thanks both you sorry for the quick response I am cooking dinner.

---

### Post by Geoffrey_Arndt on 2016-02-10
Josh . . 

Responding and cooking dinner at the same time?   You're doing pretty good!!!    (ps:   what were you making? . . . . please don't tell me it was "homemade Lasagna" . . . :D)

---

### Post by jeremy31 on 2016-02-10
[http://askubuntu.com/questions/678145/my-wifi-qualcomm-atheros-device-168c0041-rev-20-doesnt-show-up-and-work-in/678244#678244](http://askubuntu.com/questions/678145/my-wifi-qualcomm-atheros-device-168c0041-rev-20-doesnt-show-up-and-work-in/678244#678244)

The dkms package should get the internal wireless working but it won't allow any other wifi to work until it is uninstalled.

There is a work around if you need other wifi to work, install the dkms then ```
sudo chattr +i /lib/firmware/ath10k/QCA6174/hw2.1/
```
Then uninstall the dkms deb package and the chattr command will prevent the correct firmware from getting removed then you could install backports to support all wifi with
```
[COLOR=#111111][FONT=Consolas]wget [/FONT][/COLOR][https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz]("https://www.kernel.org/pub/linux/kernel/projects/backports/2015/09/03/backports-20150903.tar.gz")
tar -zxvf backports-20151120.tar.gz
cd backports-20151120
make defconfig-wifi
make
sudo make install
```

---

### Post by josh165 on 2016-02-16
@Jeremy31 thanks I'll give it a try tonight and see if I hit any snags. I'm backing up now just in case I mess it up.

---

### Post by josh165 on 2016-02-16
@Jeremy31  MANY MANY THANKS :D! Works beautifully!

---

