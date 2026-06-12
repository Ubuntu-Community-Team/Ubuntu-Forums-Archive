---
title: "[SOLVED] Belkin wireless dongle disappeared"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by LakesideLoafer on 2008-05-23
I have had Hardy Heron installed for around one month. When I first installed it automatically detected my Belkin F5D7050B usb wireless g dongle and would automatically detect and log on to my broadband wireless connection. However, I found that internet connection extremely slow (70kbps or thereabouts) and so decided to install the windows driver through ndsiwrapper. 
As soon as I did this, the network connection disappeared and has never returned. I have removed ndsiwrapper with no impact. I reinstalled it and still no change. I have the appropriate rt73 driver installed in ndsiwrapper.

I get the following:
martin@martin-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:fc:86:80:c9
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair

and

martin@martin-desktop:~$ sudo lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 0781:5406 SanDisk Corp. Cruzer Micro 4GB Flash Drive
Bus 001 Device 005: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 004: ID 050d:705a Belkin Components 
Bus 001 Device 001: ID 0000:0000 

How can I get the connection back? Any help gratefully appreciated.

Thanks.

---

### Post by pytheas22 on 2008-05-23
First, blacklist the ndiswrapper module to ensure that it won't interfere with the native driver:
```

sudo echo "blacklist ndiswrapper" >> /etc/modprobe.d/blacklist
```

Then see if the card works at least as well as it did before you installed ndiswrapper.  If it doesn't, please post the output of:
```

iwconfig
ifconfig
```

I've also had bad luck with the rt73 driver that ships with Ubuntu--in my case it would crash a lot at arbitrary times.  The drivers from [http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page) (another set of native Linux drivers for Ralink devices) worked much better.  You might want to try using them if you're not satisfied with the performance of the default Ubuntu drivers.  If you can't figure out how to install them (not hard, but not easy if you're new to Linux), post here.

---

### Post by LakesideLoafer on 2008-05-26
Thanks for your tip - unfortunately it didn't work! When I put in the command I get a message saying pemission denied. Any other thoughts?

---

### Post by pytheas22 on 2008-05-26
Sounds like a problem with sudo.  The command above should have worked, but to be sure, try typing "sudo -s" and then try the command again.

---

### Post by LakesideLoafer on 2008-07-01
Thanks for all your help. In the end I reinstalled Ubuntu from scratch. Internet is working again but still slow - maxes out at about 80kbps. Will put up with it for the time being.

---

