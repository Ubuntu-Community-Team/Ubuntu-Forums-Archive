---
title: "Lubuntu 18.04 can't connect to wi-fi"
date: 2020-02-06
forum: Networking &amp; Wireless
---

### Post by bonnifa on 2020-02-06
Hi all
I got my old netbook with pretty modest hardware and decided to install Lubnuntu 18.04. During installation I have connected to my wi-fi network. But after installation I don't have any connection, though laptop sees network. 
Wireless adapter is Atheros 9285.
What I have done: edited blacklist.conf, added ath_pci to /etc/modules - but nothing helped.
```
rfkill list -all 
```shows empty results 
and ```
sudo lshw -class network 
``` shows my wi-fi adapter is UNCLAIMED.

Any thoughts on how to fix it? Cause I need this laptop tomorrow morning and if nothing works - will have to install another distro (wi-fi worked on mint, but it dramatically slowed down performance).

---

### Post by jeremy31 on 2020-02-09
Moved to Networking and Wireless

I think you may have had an issue with a kernel update during the install that left you without the kernel modules for your wifi.  In terminal do
```
dpkg -l | grep linux
```
I would suspect the linux-modules-extra that matches the newest kernel version is not installed

---

