---
title: "Printing from a XP box through a ubuntu box"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by Dave B on 2007-06-20
i am trying to set it up so that i can print from an XP box through a ubuntu box to a HP 1320 printer.

I am trying to set CUPS up to do this but i am having problems with figuring out IP addresses and setting permissions.

Can someone please walk me through this

Dave.

---

### Post by mitch.c on 2007-06-21
For the IP address on your ubuntu box, type the following command and look at the output for eth0 or eth1:
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:3F:13:E5
          [COLOR="Red"]inet addr:192.168.1.250[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe3f:13e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9069604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8892654 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:3913125152 (3.6 GiB)  TX bytes:1463896502 (1.3 GiB)
          Base address:0xece0 Memory:fe3e0000-fe400000
```
I am assuming based on your post that the printer is attached to your ubuntu box, and you are able to print.

Change the Listen directive in /etc/cups/cupsd.conf so it reads:
```
# /etc/cups/cupsd.conf
Listen   *:631
```
Restart cups:
```
$ sudo /etc/init.d/cupsys restart
```
Start the Add Printer wizard on your XP machine. Select Network Printer, and type the following URL (replace ip_address and printer_name appropriately):
```
http://ip_address:631/printers/printer_name
```
Complete the Add Printer wizard steps.

Unless you have done something restrictive with permissions, that's all you should need.

One caveat: I am guessing from your post that your ubuntu box is getting a dynamic IP address. Should this address change, printing from XP will stop working. Better to use static IP address if possible. If you need help, let me know.

[[COLOR="Red"]UAResolved[/COLOR]]("http://http://ubuntuforums.org/showthread.php?t=377083")

---

