---
title: "Cannot Connect to Wireless N Only Network"
date: 2014-03-03
forum: Networking &amp; Wireless
---

### Post by GreenRaccoon on 2014-03-03
I dual boot Windows 7 and Ubuntu 13.10 (64 bit on both) on an ASUS k53e laptop. I have two routers at my house, and both of my OS's have been able to connect to both routers.

Today, I changed the setting for one of the routers from transmitting a a "Mixed (b/g/n)" signal to a "Wireless N only" signal. Now I CAN connect to this router on Windows 7, but not on Ubuntu.

Anyone have an idea? I found [this thread]("http://ubuntuforums.org/showthread.php?t=1592846"), but it's outdated and my kernel is using a different module. (I have the default kernel that Ubuntu updates, by the way). The guy in the link was using the iwlagn module, but I'm using the iwlwifi module.

I'll give you Linux geniuses some info about my system:

```
~$ lsmod
iwlwifi               165636  1 iwldvm

```

Connection to the working router, which is using "Mixed (b/g/n)" mode.
```
~$ iwconfigeth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"MakoLifestream"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: ...
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:682  Invalid misc:138   Missed beacon:0

```

I think this is from the /var/log/kern.log file.
```
~$ dmesg | grep -i iwl
[    6.802332] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    6.803252] iwlwifi 0000:02:00.0: irq 45 for MSI/MSI-X
[    6.827103] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    6.928765] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    6.928766] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    6.928767] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    6.928768] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[    6.928769] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[    6.928820] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[    6.967199] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   10.300835] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   10.307540] iwlwifi 0000:02:00.0: Radio type=0x2-0x2-0x1
[   10.373776] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   10.382115] iwlwifi 0000:02:00.0: Radio type=0x2-0x2-0x1

```

Anyone have any ideas? I can connect under Windows but not Linux.

---

### Post by Vladlenin5000 on 2014-03-03
I suppose you already already removed the network's profile and tried to connect again, password and all...

---

### Post by wildmanne39 on 2014-03-04
The driver you are using is problematic with N speed, most of the time N speed has to be disable for the driver to connect, so the best thing that you can do is change your setting back, sometimes it will help to update the driver or firmware but not in many cases. N speed alone gives your device nothing to fall back on if it can not make an N speed connection which is most of the time with that driver.

Their are some routers that the driver will connect at N speed with but not many and from what I have read not always.

---

### Post by GreenRaccoon on 2014-07-04
Good to know. I changed the router settings back. Thanks!

---

