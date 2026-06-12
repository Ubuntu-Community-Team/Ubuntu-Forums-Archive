---
title: "Wifi Card issues"
date: 2015-04-08
forum: Networking &amp; Wireless
---

### Post by soul1771 on 2015-04-08
Hello everyone ive had this Dwa 160 b2 card for a while now.
I have tried countless google searching on and off for a few months but i can't find anything that will resolve my issues.

Here is the output from lsusb
```
 ~$ lsusb
Bus 002 Device 005: ID 2001:3c1a D-Link Corp. DWA-160 802.11abgn Xtreme N Dual Band Adapter(rev.B2) [Ralink RT5572]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. AES2810
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
My ubuntu version
```

Description:    Ubuntu 14.04.2 LTS
Release:    14.04

```

On my labtop it has a built in wifi driver and it is working. But as soon as i plug in my wifi card it freezes the connection.

If someone could please help it would be much appreciated, im sure it would be a quick fix for some.

I'm sorry for the inconvenience i have tried countless google searching with no avail

---

### Post by praseodym on 2015-04-08
Hi,

try this driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/13/16/4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz
sudo tar xvf 4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5370sta -v 2.5.0.3
sudo dkms build -m Ralink_5370sta -v 2.5.0.3
sudo dkms install -m Ralink_5370sta -v 2.5.0.3 
sudo mkdir -p /etc/Wireless/RT2870STA
sudo cp /usr/src/Ralink_5370sta-2.5.0.3/src/RT2870STA.dat /etc/Wireless/RT2870STA
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by 42dorian2 on 2015-08-21
Hi... Umm... Will this solution work on 12.04 as well?  Because I just tried it, and, I can't get it to work.

---

### Post by praseodym on 2015-08-22
Is it the same stick?
```

lsusb
```

---

