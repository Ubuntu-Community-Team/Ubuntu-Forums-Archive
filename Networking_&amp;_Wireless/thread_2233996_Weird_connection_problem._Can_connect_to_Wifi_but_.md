---
title: "Weird connection problem. Can connect to Wifi but can't access internet. Please help."
date: 2014-07-11
forum: Networking &amp; Wireless
---

### Post by NickDS25 on 2014-07-11
I have Ubuntu 14.04 installed alongside Windows 7 and I find myself unable to access the internet using Wifi.
 I can use ethernet perfectly fine, but as I am on a laptop that is inconvenient. When I attempt to ping Google I get 
"ping [www.google.com]("http://www.google.com")
ping: unknown host www.google.com".

I am new to Linux and Ubuntu and I don't know what to do. Can anyone help me?

I just installed Ubuntu and downloaded all the updates. I am posting from a fresh installation.

I've already tried the Broadcom guide and it didn't work.

This is my wireless adapter.

"Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)"

---

### Post by praseodym on 2014-07-12
Run these commands via LAN:

```
sudo apt-get install linux-firmware-nonfree
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*)
sudo sed -i "s/blacklist brcmsmac/#blacklist brcmsmac/g" $(egrep -lo 'blacklist brcmsmac' /etc/modprobe.d/*) 
```
Reboot.

---

### Post by NickDS25 on 2014-07-12
Thank you very much.

---

