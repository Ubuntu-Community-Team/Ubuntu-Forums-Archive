---
title: "No wlan0 on ubuntu 15.04"
date: 2015-09-08
forum: Networking &amp; Wireless
---

### Post by victorgd-7 on 2015-09-08
Hi, I installed Ubuntu 15.04 alongside Windows 8.1 but I cant connect to my wifi network and when I type iwconfig it doesnt show my wlan0

```
iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.
```

```
rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

Any ideas?

---

### Post by chili555 on 2015-09-09
Please post the information outlined here in order for us to diagnose the issue: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by victorgd-7 on 2015-09-09
Here's the wireless-info.txt, I already did the sudo apt-get update and the sudo apt-get dist-upgrade

---

### Post by chili555 on 2015-09-09
> Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [[COLOR="#FF0000"]14e4:43b1[/COLOR]]Now, please check here for instructions: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by victorgd-7 on 2015-09-09
Thx a lot man, sorry I didn't see that

---

### Post by chili555 on 2015-09-09
No worries. Post back if you get stuck.

---

