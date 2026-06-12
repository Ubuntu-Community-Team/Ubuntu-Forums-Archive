---
title: "Latitude XT cannot connect to wireless"
date: 2015-03-07
forum: Networking &amp; Wireless
---

### Post by Mike_Pruner on 2015-03-07
I have installed Ubuntu 14.04 LTS on my DEll Latitude XT from 2007. Everything is great except I have no wireless.
Please help.

Mike

---

### Post by Mike_Pruner on 2015-03-07
this is my report:

########## wireless info START ##########

Report from: 06 Mar 2015 23:37 PST -0800

Booted last: 06 Mar 2015 23:24 PST -0800

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID: Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:        14.04
Codename:       trusty

##### kernel ############################

Linux 3.16.0-31-generic #41~14.04.1-Ubuntu SMP Wed Feb 11 19:30:43 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory
Could not be determined.

##### lspci #############################

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5756ME Gigabit Ethernet PCI Express [14e4:1674]
        Subsystem: Dell Device [1028:0204]
        Kernel driver in use: tg3

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
        Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
        Kernel driver in use: wl

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
                                                                                                                    1,0-1         Top

---

### Post by gordintoronto on 2015-03-07
This is a bit long, but it should help you solve your problem:
[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

---

### Post by jeremy31 on 2015-03-07
I think you should ```
sudo apt-get purge bcmwl-kernel-source
``````
sudo apt-get install firmware-b43-installer
``` Reboot

---

