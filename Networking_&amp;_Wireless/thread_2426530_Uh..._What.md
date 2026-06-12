---
title: "Uh... What????"
date: 2019-09-10
forum: Networking &amp; Wireless
---

### Post by brerackl on 2019-09-10
So I installed Ubuntu 18.04.3 LTS to my external SSD, easy enough, not my first time playing around but I'm still a noob to Ubuntu.

What is confusing me to no end is that somehow... Without a WiFi card... I have WiFi, I went so far as to unplug every USB device aside from my external SSD that I am very certain does not have some magic WiFi built into it... My motherboard has a m.2 slot or whatever for a WiFi card but doesn't have the card because I prefer wired connection. There is no WiFi device in windows as should be but yet here I am using Ubuntu to get WiFi magically without any WiFi card of any sort...... Even unplugged my Ethernet to make sure it wasn't somehow reading WiFi through the modem/router.

I am very very very confused. How is this even happening??? Right now I'm posting this to the internet with my mysterious WiFi capabilities without having any WiFi card or USB dongle or anything even close attached... I. AM. CONFUSED. HOW??????????????

Hardware specs are as follows.

EVGA x299 FTW K
EVGA Closed Loop Cooler 280mm
EVGA RTX 2070 XC
EVGA Supernova 1000W
EVGA DG-87
Ballistix RGB DDR4 RAM 64GB
Samsung 970 EVO nvme m.2 1TB
Western Digital 4TB HDD
Micron 480GB SSD in an External SSD enclosure connected via USB type C cable
Razer Ornata Chroma
Razer Death Adder
4 140mm fans nothing special

There is nothing else attached to the PC and the Ethernet is unplugged. This absolutely boggles my mind. How am I getting WiFi without WiFi hardware???????????????????????????

---

### Post by chili555 on 2019-09-10
Please open a terminal and run:```
lspci -nnk | grep -e 0200 -e 0280 -A3
lsusb
sudo lshw -C network
ip addr show
```Please post the results.

---

