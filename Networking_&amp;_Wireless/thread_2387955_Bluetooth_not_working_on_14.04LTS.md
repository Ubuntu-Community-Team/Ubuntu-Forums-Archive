---
title: "Bluetooth not working on 14.04LTS"
date: 2018-03-26
forum: Networking &amp; Wireless
---

### Post by aaubets on 2018-03-26
Hi!

I will try to connect a bluetooth device to my PC, and when I go to System > Bluetooth, it don't found any devices...

After I tryed to reinstall the BT drivers now I can't enable it: "Bluetooth is disabled".

If i check:

$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

I only have this: 2: ideapad_bluetooth: Bluetooth, before try to reinstall driver I found another bluetooth entry...

$ sudo lsmod |grep blue
bluetooth             391136  10 bnep,rfcomm

$ sudo lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 002 Device 005: ID 0bda:579a Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 007: ID 05ac:0250 Apple, Inc. Aluminium Keyboard (ISO)
Bus 002 Device 003: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 002 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I think that Bluetooth is one of the Realtek lines.

Some help? :(

---

