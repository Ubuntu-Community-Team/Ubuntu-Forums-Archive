---
title: "Install didn't find Belkin G Wireless card"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by steveliz on 2007-03-01
I have installed Ubuntu 5.10 from CD on a 500mhz PII PC with 30gb HDD and 196 mb RAM. 
Install went great except it couldn't find the Belkin (PCI) Wireless G Desktop card (ver. 7000). Install found the built in Ethernet card, but not the wireless. I installed ndiswrapper from the CD and loaded the WIN XP .inf file from the XP install disk. I ran ndiswrapper again and it showed "driver present   hardware present". I ran lspci and it recognized the Ethernet port but on the Belkin line it reads "Belkin unknown device 700f (dev 20)" . I ran ifconfig eth0 up and ifconfig eth1 up, then ran ifconfig. Still says device not found or no such device. I ran ifconfig wlan0 up and still device not found. Can anyone help me find the wireless card? I think I can get it configured once the system see it.

---

### Post by kcmohan on 2007-03-07
> **steveliz said:**
> I have installed Ubuntu 5.10 from CD on a 500mhz PII PC with 30gb HDD and 196 mb RAM. 
Install went great except it couldn't find the Belkin (PCI) Wireless G Desktop card (ver. 7000). Install found the built in Ethernet card, but not the wireless. I installed ndiswrapper from the CD and loaded the WIN XP .inf file from the XP install disk. I ran ndiswrapper again and it showed "driver present   hardware present". I ran lspci and it recognized the Ethernet port but on the Belkin line it reads "Belkin unknown device 700f (dev 20)" . I ran ifconfig eth0 up and ifconfig eth1 up, then ran ifconfig. Still says device not found or no such device. I ran ifconfig wlan0 up and still device not found. Can anyone help me find the wireless card? I think I can get it configured once the system see it.

I have the same problem and same responses for the Belkin card (ver.7000). I edited the /etc/iftab file and entered the mac address for the G card and also entered the ip address for the  g card in /etc/network/interfaces file. I still get the same response when I try to configure the wlan0 through ifconfig wlan0 command.

I noticed that the G card has RTL8185L chip on it and found an experimental driver on the net   at [http://sourceforge.net/project/downloading.php?group_id=114161&use_mirror=superb-east&filename=rtl8180-0.21.tar.gz&23523643](http://sourceforge.net/project/downloading.php?group_id=114161&use_mirror=superb-east&filename=rtl8180-0.21.tar.gz&23523643)
but am not sure if it will resolve my "unknown device" problem.

Can some Ubuntu Guru help?

---

