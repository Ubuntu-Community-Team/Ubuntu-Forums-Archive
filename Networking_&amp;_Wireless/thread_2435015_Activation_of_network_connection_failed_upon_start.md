---
title: "Activation of network connection failed upon startup"
date: 2020-01-15
forum: Networking &amp; Wireless
---

### Post by mash1408 on 2020-01-15
I have been facing issues with my built-in Wifi Adapter so i disabled it and now i use a usb wifi adapter.
Details of usb card are DWA-131.
Every time i boot i get a message "Activation of network connection failed".
It however disappears if i remove  and insert it back in and everything works fine.
Could someone suggest a fix?
Here are details of[FONT=arial black] ifconfig for my adapter[/FONT]

**wlx542aa25b3a8f**: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.31.60  netmask 255.255.255.0  broadcast 192.168.31.255
        inet6 fe80::6446:2eb2:d70:a1a  prefixlen 64  scopeid 0x20<link>
        ether 54:2a:a2:5b:3a:8f  txqueuelen 1000  (Ethernet)
        RX packets 147  bytes 31411 (31.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 262  bytes 50218 (50.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

---

### Post by slickymaster on 2020-01-15
Thread moved to **Networking & Wireless**

Please have a read at this [sticky]("https://ubuntuforums.org/showthread.php?t=370108") and proceed accordingly

---

### Post by CelticWarrior on 2020-01-15
The problem is likely unrelated to the WiFi stick itself so neither the information you already provided nor the data that could be gathered by the suggestion above won't be of any use.

This likely has to do with the way your system initializes USB devices. Some BIOS/UEFI settings may or may not not influence it and, of course, a BIOS/UEFI update may (or may not) improve it.

Perhaps better to troubleshoot your internal WiFi card. If not defective then it's very likely that all it needs is drivers.

---

