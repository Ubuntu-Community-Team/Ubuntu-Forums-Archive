---
title: "No Wireless Connectivity"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by WishingForGoats on 2009-02-02
Hi,

I can't connect to the internet through my wireless card.
The card is:
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

The output of  sudo dmesg | grep -i b43 is:
[    4.595228] b43-pci-bridge 0000:05:02.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   16.740115] b43-phy0: Broadcom 4318 WLAN found
[   48.885952] input: b43-phy0 as /devices/virtual/input/input9
[   48.976085] firmware: requesting b43/ucode5.fw
[   49.033457] firmware: requesting b43/pcm5.fw
[   49.039821] firmware: requesting b43/b0g0initvals5.fw
[   49.070432] firmware: requesting b43/b0g0bsinitvals5.fw
[   49.200066] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   49.319927] Registered led device: b43-phy0::radio
[  421.496217] b43-pci-bridge 0000:05:02.0: PCI INT A disabled

I tried to follow along other people's threads, but it didn't work.  Thanks in advance for help.

---

### Post by Crafty Kisses on 2009-02-02
This thread should get you going: [http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177).

---

### Post by WishingForGoats on 2009-02-02
Got it thanks!

---

### Post by Crafty Kisses on 2009-02-02
Glad I could help. :)

---

