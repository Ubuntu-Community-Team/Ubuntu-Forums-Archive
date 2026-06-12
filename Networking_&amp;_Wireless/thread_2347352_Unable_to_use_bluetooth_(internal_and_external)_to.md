---
title: "Unable to use bluetooth (internal and external) to map controllers"
date: 2016-12-23
forum: Networking &amp; Wireless
---

### Post by darkwolfx2 on 2016-12-23
Hello everyone, I just installed a fresh Ubuntu 16.04 version on an HP laptop. It comes with a wireless/bluetooth internal adapter but I also have an external one which I was looking to use if the internal one didn't work.

I'm looking forward to pair some bluetooth controllers, which are supposed to be paired with a game called SportsFriends and its pairing tool.

Issue: I cannot get to recognize either my internal bluetooth adapter or the external one.
I have tried searching for help, assistance in google and this forum but have had no luck at all.

I believe the closest troubleshooting steps I've seen, have been this thread which unfortunately didn't help me:
[https://ubuntuforums.org/showthread.php?t=2262775&page=1]("https://ubuntuforums.org/showthread.php?t=2262775&page=2")

The op had the same problem and the mod who assisted got it solved.

This is what I have tried:
[LIST]
[*]hciconfig, hciconfig -a, hciconfig dev : All these options gave me a blank of results 
[*]Bluetooth manager was there, but I don't see it anymore 
[*][https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup) 
[*][https://ubuntuforums.org/showthread.php?t=2262775&page=1](https://ubuntuforums.org/showthread.php?t=2262775&page=1) 
[/LIST]

Maybe I should also share some of those details that the mod who assisted op requested, to see if someone could please help me.

lsusb gives:
```

darkwolf@6930-ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

uname -a gives:
```
Linux 6930-ubuntu 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

rfkill list gives:
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hp-gps: GPS
    Soft blocked: yes
    Hard blocked: yes

```

Please let me know any other tests you want me to try. One thing is for certain, I was never able to see adapters "hciconfig".
Thanks in advance, any help is hugely appreciated.

---

