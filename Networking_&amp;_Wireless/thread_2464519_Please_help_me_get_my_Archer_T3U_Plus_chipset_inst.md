---
title: "Please help me get my Archer T3U Plus chipset installed on 21.04"
date: 2021-07-04
forum: Networking &amp; Wireless
---

### Post by xziggyx on 2021-07-04
hello im sorry if its been posted before but iv tryed dowloading a few different drivers for my tp link ac1300 but no luck. im having trouble with downlaoding and extracting files since i dont know the terminal commands well enough. anyways specs Tp-Link Ac1300 Archer T3U Plus. Ubuntu 21.04

ziggy@ziggy-desktop:~$ lsusb 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 002: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 001 Device 007: ID 0c45:7603 Microdia USB Keyboard 
Bus 001 Device 006: ID 093a:2530 Pixart Imaging, Inc. Gaming Mouse 
Bus 001 Device 005: ID 0bda:5411 Realtek Semiconductor Corp. RTS5411 Hub 
Bus 001 Device 004: ID 0bda:5411 Realtek Semiconductor Corp. RTS5411 Hub 
Bus 001 Device 003: ID 2357:0138 TP-Link 802.11ac NIC 
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
ziggy@ziggy-desktop:~$ 

please help me its giving me a headache. thank

---

### Post by coffeecat on 2021-07-04
*Thread moved to **Networkng & Wireless** sub-forum.*

---

### Post by chili555 on 2021-07-04
First get a temporary internet connection by ethernet, tethering or whatever means possible. Next, open a terminal and do:

```
sudo apt update
sudo apt install git dkms build-essential linux-headers-generic
```

If some of these prerequisites are already installed, that’s fine, just move on to the next package.


```
git clone https://github.com/morrownr/88x2bu.git
cd 88x2bu
sudo ./install-driver.sh
```

Reboot and your wireless should be working.

---

