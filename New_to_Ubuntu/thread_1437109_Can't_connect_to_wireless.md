---
title: "Can't connect to wireless"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by adamleslie15@hotmail.com on 2010-03-23
Hey everyone, I have installed Ubuntu onto my sisters laptop and can not for the life of me figure out how to get the wireless to work. Even directly connecting it to the router via cable wont work.

Here are the specs:
Acer Aspire 3680
Intel Celeron M CPU 410 @ 1.46GHz
500mb of RAM

Ubuntu
Release 8.04 (hardy)
Kernal Linux 2.6.24-23-generic
GNOME 2.22.3

Please help,
Thanks,
Adam

---

### Post by anewguy on 2010-03-23
Well, in cases where the wireless doesn't work after installing Linux, keep in mind that you need a driver for it, much the same as Windows needed a driver for it.

In order to direct you further, there are a couple of things to do and post the results back here for first:

- open a terminal window (applicatons/accessories/terminal)

- type:

lspci <press enter> 

This command lists the known PCI hardware devices on the system.  Keep in mind that just because they are "known" as hardware doesn't mean they have a driver and can function.  Look for a line that says it's a wireless or ethernet controller - post the entire line for ALL entries like that back here.

lsusb <press enter>

This command lists the know USB hardware devices on the system.  As with lspci, it doesn't mean the devices work.  Normally this is only used with desktops if the wireless adapter plugs into a USB port, but for laptops the internal wireless adaptor can be connected to internal USB, so it should always be run for laptops.  Just copy and paste all the output from that back here.

These results will help us identify the adaptor hardware, which then points us in a direction to get a working driver.

Dave ;)

---

### Post by adamleslie15@hotmail.com on 2010-04-03
0a:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01) 
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller 
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) 
krissy@krissy-laptop:~$ lsusb 
Bus 005 Device 001: ID 0000:0000   
Bus 004 Device 001: ID 0000:0000   
Bus 003 Device 001: ID 0000:0000   
Bus 002 Device 001: ID 0000:0000   
Bus 001 Device 001: ID 0000:0000   
krissy@krissy-laptop:~$

---

