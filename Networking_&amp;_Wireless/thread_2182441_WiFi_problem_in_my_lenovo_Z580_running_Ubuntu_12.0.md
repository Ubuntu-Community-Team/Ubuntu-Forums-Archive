---
title: "WiFi problem in my lenovo Z580 running Ubuntu 12.04"
date: 2013-10-21
forum: Networking &amp; Wireless
---

### Post by Urvik on 2013-10-21
Well I'm still a newbie in Ubuntu. I'm using UBUNTU 12.04 precise edition version. The problem is my WiFi connection. I've been working on it since far too long all by myself and now I think I have really messed it up and I need some expert help. I read many threads of this forum which were related to my problem and still it didn't work for me.

Now the situation is,even rfkill list all command shows nothing. :(

Please help!!

---

### Post by chili555 on 2013-10-21
Please give us some additional information. Please open a terminal and run and post:```
lspci -nn | grep 0280
```What have you tried so far?

---

### Post by Urvik on 2013-10-21
> **chili555 said:**
> Please give us some additional information. Please open a terminal and run and post:```
lspci -nn | grep 0280
```What have you tried so far?
 
Here it is:
```
urvik@urvik-Lenovo-Z580:~$ lspci -nn | grep 0280
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
```

And I have tried many things. I've played with modprob files. Blacklisted some of the drivers and then removed them, Tried to install Windows Wireless drivers from the Ubuntu store, tried using ndsiwrapper,but unfortunately none of this worked. :(

---

### Post by chili555 on 2013-10-21
> Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727]A very tricky device to get going properly. The exact fix depends on your exact version; there is a 12.04.1, .2 and .3. Each has a different kernel. Please let us see:```
uname -r
lsmod | grep -e ndis -e wl -e brcm
```Thanks.

---

### Post by Urvik on 2013-10-21
First of all thanks a lot for replying sir!!
> **chili555 said:**
> A very tricky device to get going properly. The exact fix depends on your exact version; there is a 12.04.1, .2 and .3. Each has a different kernel. Please let us see:```
uname -r
``` 
```
urvik@urvik-Lenovo-Z580:~$ uname -r
3.2.0-49-generic

```
> 
```
lsmod | grep -e ndis -e wl -e brcm
```
```
urvik@urvik-Lenovo-Z580:~$ lsmod | grep -e ndis -e wl -e brcm
rndis_host             13855  0 
cdc_ether              13494  1 rndis_host
usbnet                 26208  2 rndis_host,cdc_ether
compat                 20099  13 ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211,rndis_host,cdc_ether,usbnet,rfcomm,bnep,bluetooth,lib80211,bcma

```

---

### Post by chili555 on 2013-10-21
Why is ath9k, a driver for an Atheros card,  loaded for a Broadcom device? May we see:```
cat /etc/modules
cat /etc/modprobe.d/blacklist.conf
```And what about rndis_host? Is your cellular device tethered?

---

