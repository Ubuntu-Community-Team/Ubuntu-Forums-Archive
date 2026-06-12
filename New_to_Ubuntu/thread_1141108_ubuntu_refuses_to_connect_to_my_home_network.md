---
title: "ubuntu refuses to connect to my home network"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-28
everytime i try to connect to my home network, i have problems. i am sitting 10 feet away from the router with the following setup:

SSID: the internet
Security: none
no "exclusive access list" - meaning everyone should be able to connect
netgear router wireless g. 

ath9k wireless drivers 

any ideas?

---

### Post by billgoldberg on 2009-04-28
Try going to System -> Administration -> Hardware drivers and see if anything related to your wifi is listed there.

Or else try out ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by PriceChild on 2009-04-28
Are you not using the network manager to connect to your wireless network? (next to the clock, top right) You shouldn't have to enter things like the ssid..

Depending on your answer, it might be useful to find out the wireless chipset..
```
lsusb
lspci
```

---

### Post by abn91c on 2009-04-28
In case you are not aware you wireless router will transmit a signal very far from you house, your neighbors can easily access it and change the settings/password plus use your network. you need to setup a security key and router password. you can always make your ssid hidden from others. use the router web-based utility it may be something like [http://192.168.0.1](http://192.168.0.1) for you router

---

### Post by asuastrophysics on 2009-04-28
> **abn91c said:**
> In case you are not aware you wireless router will transmit a signal very far from you house, your neighbors can easily access it and change the settings/password plus use your network. you need to setup a security key and router password. you can always make your ssid hidden from others. use the router web-based utility it may be something like [http://192.168.0.1](http://192.168.0.1) for you router

yeah i figured as such, but for some reason the ath9k drivers have trouble connecting to any secured network...but maybe i'm just configuring it wrong?
idk im just a novice what can i say. :rolleyes:
i do however, have the router configuration address (routerlogin.net) locked with a username and password. ;)

if you can help me with that problem, i'll gladly give you:
A) the type of password protection i set up (EG WEP, TKIP, ETC)
B) my wireless configuration on the laptop. 

it would be nice to get a secure wifi going...whenever it tries to connect to a secure network, it attempts to connect, and then fails, and tries again, even if i provide it with the correct password. (weird...)

---

### Post by asuastrophysics on 2009-04-28
output of lsusb:
```
girdy@girdy-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

output of lspci:    (sorry i know this is gonna be a long output, so i skipped to the important parts)
```
lspci
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

```
hope that helps!

also, the wireless works PERFECTLY for the first few page loads after connecting, but after about the 3rd web page loaded, things seem to slow down dramatically.   strange....

---

### Post by PriceChild on 2009-04-29
It looks like a lot of people with the 'AR242x' card have been having seemingly identical problems. Some have had better success with the madwifi drivers.

---

