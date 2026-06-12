---
title: "Lenove wireless trouble?"
date: 2013-12-19
forum: Networking &amp; Wireless
---

### Post by egboss001 on 2013-12-19
> **chili555 said:**
> Please open a terminal and run and post:```
dmesg | grep iwl
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

dmesg | grep iwl
[   13.856167] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   13.856170] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   13.856239] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.856247] iwlagn 0000:03:00.0: setting latency timer to 64
[   13.856303] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   13.877061] iwlagn 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   13.877065] iwlagn 0000:03:00.0: Device SKU: 0X9
[   13.877067] iwlagn 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   13.877086] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   13.877301] iwlagn 0000:03:00.0: irq 43 for MSI/MSI-X
[   14.012362] iwlagn 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[   14.014531] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
user@ubuntu:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by chili555 on 2013-12-19
> **egboss001 said:**
> dmesg | grep iwl
[   13.856167] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   13.856170] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   13.856239] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.856247] iwlagn 0000:03:00.0: setting latency timer to 64
[   13.856303] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   13.877061] iwlagn 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   13.877065] iwlagn 0000:03:00.0: Device SKU: 0X9
[   13.877067] iwlagn 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   13.877086] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   13.877301] iwlagn 0000:03:00.0: irq 43 for MSI/MSI-X
[   14.012362] iwlagn 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[   14.014531] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
user@ubuntu:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yesWould you mind starting your own new thread; this one is getting long and hard to decipher which reply belongs to who. I see the wireless is hard blocked; i.e. with a hardware switch. In your thread, please tell us about the switch or key combination. Does it seem to respond to key presses?

---

### Post by egboss001 on 2013-12-19
Im Sorry im not understand what do you need actually :(
i wrote in terminal && this my result :confused:
what i can do !!

---

### Post by Iowan on 2013-12-19
Moved to new thread.
I'll edit the title - if there is a more appropriate description.

---

### Post by egboss001 on 2013-12-26
by way or another 
the wireless work when i reboot
thank you for your effort and help

---

