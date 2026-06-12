---
title: "Network card issues in Ubuntu 16.04.1 and 16.10"
date: 2017-02-22
forum: Networking &amp; Wireless
---

### Post by ibazulic on 2017-02-22
Hi guys,

I have a serious issue that I hope you'll help me resolve. I have a 990x-gaming-sli motherboard and it works like a charm in Windows. All functions are doing what they should be doing. I yesterday decided to install Linux as my secondary operating system due to work requirements and found issues I can't resolve. The NIC on the motherboard is Intel I211 Gbit ethernet adapter which is recognized inside Linux but does not want to pick up an IP. It seems that the kernel is constantly resetting the adapter. I'll copy/paste the log:
```
Feb 22 09:03:02 mail kernel: [ 321.608099] Tx Queue <6>
Feb 22 09:03:02 mail kernel: [ 321.608099] TDH <23>
Feb 22 09:03:02 mail kernel: [ 321.608099] TDT <23>
Feb 22 09:03:02 mail kernel: [ 321.608099] next_to_use <25>
Feb 22 09:03:02 mail kernel: [ 321.608099] next_to_clean <23>
Feb 22 09:03:02 mail kernel: [ 321.608099] buffer_info[next_to_clean]
Feb 22 09:03:02 mail kernel: [ 321.608099] time_stamp <1000012af>
Feb 22 09:03:02 mail kernel: [ 321.608099] next_to_watch
Feb 22 09:03:02 mail kernel: [ 321.608099] jiffies <100001531>
Feb 22 09:03:02 mail kernel: [ 321.608099] desc.status <120200>
Feb 22 09:03:04 mail kernel: [ 323.607349] igb 0000:02:00.0: Detected Tx Unit Hang
Feb 22 09:03:04 mail kernel: [ 323.607349] Tx Queue <6>
Feb 22 09:03:04 mail kernel: [ 323.607349] TDH <23>
Feb 22 09:03:04 mail kernel: [ 323.607349] TDT <23>
Feb 22 09:03:04 mail kernel: [ 323.607349] next_to_use <25>
Feb 22 09:03:04 mail kernel: [ 323.607349] next_to_clean <23>
Feb 22 09:03:04 mail kernel: [ 323.607349] buffer_info[next_to_clean]
Feb 22 09:03:04 mail kernel: [ 323.607349] time_stamp <1000012af>
Feb 22 09:03:04 mail kernel: [ 323.607349] next_to_watch
Feb 22 09:03:04 mail kernel: [ 323.607349] jiffies <100001725>
Feb 22 09:03:04 mail kernel: [ 323.607349] desc.status <120200>
Feb 22 09:03:06 mail kernel: [ 325.606602] igb 0000:02:00.0: Detected Tx Unit Hang
Feb 22 09:03:06 mail kernel: [ 325.606602] Tx Queue <6>
Feb 22 09:03:06 mail kernel: [ 325.606602] TDH <23>
Feb 22 09:03:06 mail kernel: [ 325.606602] TDT <23>
Feb 22 09:03:06 mail kernel: [ 325.606602] next_to_use <25>
Feb 22 09:03:06 mail kernel: [ 325.606602] next_to_clean <23>
Feb 22 09:03:06 mail kernel: [ 325.606602] buffer_info[next_to_clean]
Feb 22 09:03:06 mail kernel: [ 325.606602] time_stamp <1000012af>
Feb 22 09:03:06 mail kernel: [ 325.606602] next_to_watch
Feb 22 09:03:06 mail kernel: [ 325.606602] jiffies <100001919>
Feb 22 09:03:06 mail kernel: [ 325.606602] desc.status <120200>
```
After this, one message keeps repeating in the log:
```
igb 0000:02:00.0 eth0: igb: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
```
This happens on both the kernel's stock driver and on the newest Intel driver. I found a work-around on Launchpad for Utopic ([here]("https://bugs.launchpad.net/ubuntu/+source/linux-lts-utopic/+bug/1492146")). The suggestion was to run:
```
ethtool -K eth0 tso off gso off gro off sg off
```
but this didn't help on my system. In Windows 7 everything works, both the wireless and the NIC work perfectly, no connection issues. I have tried three distributions (Debian Jessie, Ubuntu 16.04 and 16.10) along with 4 different kernels (from 3.16.0 in Jessie to 4.8.0 in Ubuntu 16.10), both with stock kernel drivers and with recompiled drivers and I can't get the thing to work.

The second issue is related to my RTL8188ce WiFi adapter. The card is detected in the system, firmware is installed and running but I can't find any wireless networks in range (in Windows 7 I usually find 2-5 networks, depending on signal). I have tried using FreedomBen's custom drivers from his GIT repo and recompiled those but the issue remains. Power management is off for this card. The only internet connection I can now get on my home computer is through tethering on my LG G4 mobile phone. Even that does not work properly since NetworkManager keeps resetting the USB link every 30 seconds (Ubuntu immediately after starting says "System problems detected" and NetworkManager is always the culprit) so I have to stop it through "service network-manager stop" and then get interfaces up one by one to get USB connection working.

This all happens on a *newly* installed system. Does anyone have any idea what can be done? I need Ubuntu to be installed since I need OpenStack and LXD containers. 

Thanks!

---

### Post by jkolo on 2017-06-05
I had the same problem. I resolved problem with add ```
iommu=soft
``` or ```
iommu=pt iommu=1 amd_iommu_fullflush
``` to kernel parameters.

---

