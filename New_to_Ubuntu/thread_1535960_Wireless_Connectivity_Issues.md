---
title: "Wireless Connectivity Issues"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by invisibleink214 on 2010-07-21
I'm new to Ubuntu and I installed Ubuntu 10.04 Desktop today. I've read a couple of guides and they all say one thing or another and they end up confusing me. After reading all the guides I still have not managed to connect to my wireless. Would really appreciate it if somebody helped me.

---

### Post by nothingspecial on 2010-07-21
Open a terminal (in your menu accessories > terminal)

copy and paste into it

```
sudo lshw -C network
```

Then copy and paste the output here.

You will have to type your password which you won`t see as you type it.

---

### Post by invisibleink214 on 2010-07-21
lamont@lamont-desktop:~$ sudo lshw -C network 
[sudo] password for lamont:  
  *-network                
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 9 
       bus info: pci@0000:01:09.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=32 
       resources: irq:17 memory:fd9fe000-fd9fffff 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:1e:8c:02:10:42 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
lamont@lamont-desktop:~$

---

### Post by nothingspecial on 2010-07-21
Try ```
sudo apt-get install b43-fwcutter

```

Then reboot.

If that doesn`t work, the guide you need to follow is this one

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Any problems, post back:D

---

### Post by invisibleink214 on 2010-07-21
I have followed the guide and have got all the way to the configuring the wireless network settings. In the previous steps it said that my wireless driver was installed. When I go to "Open the Networking Admin tool (System | Administration | Networking), select the Wireless connection and click Properties, ensure the Enable roaming mode checkbox is ticked" I can not find the networking that the guide is talking about.

Thank You.

---

### Post by techningeer on 2010-07-21
I have had similar problems in Xubuntu 9.04 and Ubuntu 9.10. I installed "gnome-network-admin", and then set my wireless router to non-encrypted.

---

### Post by porchrat on 2010-07-21
I have the exact same wifi module as you and I used to struggle with it a few years ago. Nowadays though Canonical really have made it a lot easier.

The easiest way to install the correct driver is to just use the "Hardware Drivers" program.

What you do is when you first intall Ubuntu use an ethernet connection to get it nice and up to date. Then go to the menus in the top left corner of the screen and navigate through: System --> Administration --> Hardware Drivers.

The Hardware Drivers app will scan for available proprietary drivers for your hardware and when it's done it should display the driver for your wireless driver. Then all you do is click "activate" and it should install. Simple and not a single command line input required. Not a bad way to go for someone new to the OS.

---

### Post by invisibleink214 on 2010-07-21
When I try and do the method from the Hardware Drivers. It always says that the installation of the driver failed and to look in the log files or something.

---

