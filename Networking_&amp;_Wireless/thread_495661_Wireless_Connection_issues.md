---
title: "Wireless Connection issues"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by okkiedokki on 2007-07-08
Ok, I've read through about 4 long posts on installing my wireless network drivers and I believe I've been successful.  I am using a Compa Presario R3000 laptop with Broadcom BCM4306.  I've installed ndiswrapper correctly and the drivers are correctly installed too.  

I then went into my network settings to enable the wireless connection and add the ESSID and WEP encryption key, it goes through it's "Changing Network Configuration" deal and if I go into "properties" it's detecting the signal strength of my wireless router but it won't connect at all.  Even if I disable the wired connection.  Also, if I single click on the network manager in the upper right of the screen it gives me the option for wired network and manual configuration.   What am I doing wrong?

---

### Post by fredj on 2007-07-09
Open a terminal. Type 'sudo ndiswrapper -v' (without the quote marks). Post the result here.
Also type 'lshw -class network' and post the result.

---

### Post by okkiedokki on 2007-07-09
utils Error: no version specified!
driver modinfo: could not open ndiswrapper: No such device



 *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 03
       serial: 00:90:4b:59:61:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.47+Broadcom,10/28/2003, 3.40.2 latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:e8204000-e8205fff irq:19
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:01:b9:5c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.64 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:e8208800-e82088ff irq:18

---

### Post by fredj on 2007-07-10
Looks like you have the version of ndiswrapper from the standard repository and I think this is flawed.
It may install some drivers but others do not work. I spend ages trying to get it to work.
In the end I downloaded the latest source code from the ndiswrapper site and installed the
build-essential package and compiled the latest version of ndiswrapper. This worked with no problems.
Of course you need a network connection to do all that. Or you can download the ubuntu DVD. It has
the build-essential package on it.

---

### Post by okkiedokki on 2007-07-10
Ok, I will try that.  I do have my wired connection working.  Various things wouldn't work like dvd playback, wireless connection, and a few others.  I surfed around the wiki pages and got everything working except the wireless connection.  I'll let you know how it goes.

---

### Post by Carleton91 on 2007-07-10
i am actually at that same stage in my wireless endeavors, so if you reinstall ndiswrapper with the good version and still have the same issue you can check my thread called "ndiswrapper trouble - SAVE ME!" where kevdog is helping me a bunch.

---

