---
title: "Laptop install a disappointment"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by fixerman on 2009-10-10
After a very successful experience on an old desktop pc I was encouraged to install Ubuntu on an Acer Aspire laptop that had been very happy running Vista Home Premium and indeed the evaluation version of Windows 7. I did a clean install using the full hard drive. Everything appeared to go according to plan but the result is very poor. 

The laptop is just so slow to respond to any command and frequently just hangs. It shows a good (84%) signal strength on my wireless network and connects to the internet but takes forever to load a page. It has failed to update any of the operating system or any of the repository updates.

Was I expecting too much?

As I write I am doing a full reinstall to see if it makes any difference.

Intel Centrino Duo T5500 1.6ghz.
Nvidea GeForce Go 7600 with 128 Mb dedicated RAM.
2gb DDR2 RAM

160Gb HDD

---

### Post by Jazzy_Jeff on 2009-10-10
It sounds like something is not running right. Make sure you enable the graphics driver for your video card. I also use an Acer Aspire and everything worked on first install.

Let us know what happens after the new reinstall.

Another thing, the new release of Ubuntu will be out towards the end of this month. You can install the beta if you want to try it out.

---

### Post by LewRockwell on 2009-10-10
you probably used the 32 bit version with your old machine

you aren't attempting to use that same version with your new machine by chance?

just a thought...

.

---

### Post by freak42 on 2009-10-10
try to activate the nvidia driver in system->administration-> hardware

try to deactivate visual effects in system-> preferences ->appearance->visual effects

if this doesn't help, can you provide us with more hardware infos, e.g. the exact laptop model?

---

### Post by sandyd on 2009-10-10
> **fixerman said:**
> After a very successful experience on an old desktop pc I was encouraged to install Ubuntu on an Acer Aspire laptop that had been very happy running Vista Home Premium and indeed the evaluation version of Windows 7. I did a clean install using the full hard drive. Everything appeared to go according to plan but the result is very poor. 

The laptop is just so slow to respond to any command and frequently just hangs. It shows a good (84%) signal strength on my wireless network and connects to the internet but takes forever to load a page. It has failed to update any of the operating system or any of the repository updates.

Was I expecting too much?

As I write I am doing a full reinstall to see if it makes any difference.

Intel Centrino Duo T5500 1.6ghz.
Nvidea GeForce Go 7600 with 128 Mb dedicated RAM.
2gb DDR2 RAM

160Gb HDD
see if nlowering the wireless bitrate works - ubuntu runs it at the highest bitrate possible, which causes problems sometimes.

---

### Post by fixerman on 2009-10-10
Thanks guys for your advice.

The reinstall made little difference. I connected to my network by ethernet cable and I got all the updates straight away including a video driver which made a big difference. I have gone back to wireless which is still terrible. Most time it will not connect to a site. The laptop is used in a location where no cable connection is available.

In answer to Lew Rockwell I have used the same cd that I used on the old desktop pc. What is the problem there?

It is an Acer Aspire 5680.

---

### Post by ibuclaw on 2009-10-10
What type of Wireless does the laptop have?

Can you post the output of:
```
lspci
```
and
```
iwconfig
```

Regards
Iain

---

### Post by fixerman on 2009-10-10
fixerman@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
fixerman@ubuntu:~$

---

### Post by fixerman on 2009-10-10
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"John"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:DF:7D:7A:65   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=92/100  Signal level:-39 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by ibuclaw on 2009-10-10
> 05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

You are using an Intel Wireless 3945 by the looks of it. You should be receiving no issues whatsoever with that card.

How far away is the wireless router?

These are the notable things in your iwconfig:
```

Bit Rate=1 Mb/s
Retry min limit:7

```
The Bit Rate is slow, very slow (should be 27Mbps+, depending on how many people are connected to the AP)

you could try:
```
sudo iwconfig wlan0 retry 63
```
and that may improve the aggressiveness of the connection.

Regards
Iain

You could try:
[CODE]sudo iwconfig wlan0 retry

---

### Post by fixerman on 2009-10-10
> **tinivole said:**
> You are using an Intel Wireless 3945 by the looks of it. You should be receiving no issues whatsoever with that card.

How far away is the wireless router?

These are the notable things in your iwconfig:
```

Bit Rate=1 Mb/s
Retry min limit:7

```
The Bit Rate is slow, very slow (should be 27Mbps+, depending on how many people are connected to the AP)

you could try:
```
sudo iwconfig wlan0 retry 63
```
and that may improve the aggressiveness of the connection.

Regards
Iain

You could try:
[CODE]sudo iwconfig wlan0 retry

For the purposes of this installation the router is just 6 feet away.

The signal strength is now 95%

When I disconnect the cable and try to launch firefox it connects and loads the first page but after it just will not connect to the internet or the local network.

---

