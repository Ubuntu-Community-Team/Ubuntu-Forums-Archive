---
title: "So close..."
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by Yume on 2007-11-29
So I have a dell latitude D520 and I just installed Ubuntu 7.10 and at first I couldn't get any network connection, be it wired or wireless. After following some advice from people on mIRC I can now get a wired connection but now there is no longer even the option in my network manager for wireless. Any help is greatly appreciated, it's very frustrating to be so close to being fully connected... 

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:19:B9:71:C2:35  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2637819 (2.5 MB)  TX bytes:352812 (344.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



sudo lshw -C network


 *-network UNCLAIMED     
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:71:c2:35
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.0.4 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s


If you need any other information just let me know.  Thank you in advance and I apologize for being such a newbie.

---

### Post by hardyn on 2007-11-29
do you remember what you did with the advice of the IRC people?

---

### Post by Yume on 2007-11-30
umm...not exactly. I was trying to install ndiswrapper using the terminal. I seem to remember going onto my windows partition, since I dual booted, and going to the Dell website and downloading a driver, think it was ndiswrapper and then installing it from windows. Now a couple of minutes ago I tried following the sticky thread above about the broadcom card, since that's what I have. I followed the install instructions and here's what I got  

*Retrieving bcmw 15 driver...done
tar:Error is not recoverable: exiting now
le or directory
*Retrieving newest ndiswrapper source code... tar :ndiswrapper-newest.tar.gz:
Cannot open: No such file or directory 
tar: Error is not recoverable: exiting now
done
*Installing the necessary compilation libraries... Package 'build=essential' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files
and dpkg  --contents (= dpkg-deb --contents) to list their contents
linux-headers-2.6.22-14 generic is already installed... dpkg-preconfigure: unable to re-open stdin:
done
*removing old ndiswrapper module...


and here is where it seems to have stopped.

---

