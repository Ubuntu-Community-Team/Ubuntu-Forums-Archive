---
title: "Intermittent wi-fi connection problems"
date: 2017-08-15
forum: Networking &amp; Wireless
---

### Post by JdeP on 2017-08-15
I wonder if some kind soul would be willing to walk me through diagnostics for identifying a frustrating wifi problem? (I am not a complete newbie, but nor am I expert). 

My wi-fi connection is erratic: sometimes it's fine for hours or days, sometimes it breaks for no apparent reason. Sometimes a reboot helps, often it doesn't. Maybe I've messed-up a setting somewhere (I've tried various solutions offered in other threads), or maybe it's a hardware problem. My phone and Chromebook experience no problems with wifi, so I know it's not a problem with my internet service or router.

Here are some basic data:

System: Ubuntu 16.10, 64-bit

USB wireless adaptor: TP-Link TL-WN722N 150 Mbps

sudo lshw -C network :
>   *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@2:1.5
       logical name: wlx98ded01a4aaf
       serial: 98:de:d0:1a:4a:af
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=4.8.0-59-generic firmware=1.4 ip=192.168.0.2 link=yes multicast=yes wireless=IEEE 802.11

lsusb :
> Bus 002 Device 004: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Let me know what other info you need. Thanks in advance :-)

---

### Post by jeremy31 on 2017-08-15
*Thread moved to **Networking & Wireless**.*

See the wireless script link in my signature and post your results

---

### Post by JdeP on 2017-08-15
MANY thanks. Here is the pastebin address:

[http://paste.ubuntu.com/25318313/](http://paste.ubuntu.com/25318313/)

---

### Post by jeremy31 on 2017-08-15
I would replace 16.10 with 16.04.1 as 16.10 is no longer supported.  Ubuntu 17.04 causes a new issue with USB wifi devices with MAC randomization and Ubuntu 16.04 is supported until 2021

---

### Post by JdeP on 2017-08-15
Thanks again for the quick response.
Just to be clear, and to be sure you didn't make a typo: you suggest I *down*grade from 16.10 to 16.04?
If so, am I right in thinking this means re-installing 16.04 from scratch?

---

### Post by jeremy31 on 2017-08-15
Yes, install 16.04.1 as it is supported until 2021 and it should have the Ubuntu 4.4.0 kernel that is also supported until 2021

Using Wicd and Network Manager is not recommended

---

### Post by JdeP on 2017-08-15
Many thanks -- I **do** appreciate your help and advice.

---

### Post by praseodym on 2017-08-15
Using the same driver here. Using less current and deactivating hardware encryption works without any disconnects here (however, using Wicd instead of the network-manager):
```

echo 'KERNEL=="wlx98ded01a4aaf*", ACTION=="add", RUN+="/sbin/iwconfig wlx98ded01a4aaf txpower 16"' | sudo tee /etc/udev/rules.d/10-wlan-stick.rules
echo "options ath9k_htc nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9khtc.conf
```
Reboot. "wlx98ded01a4aaf*" is the name of the interface, will be "wlan*" in 16.04

---

