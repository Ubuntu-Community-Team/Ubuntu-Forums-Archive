---
title: "Wireless internet not working still  :("
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by bluzepher on 2008-07-04
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



 *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:23:13:4b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-15-generic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:79:3c:a0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.4 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s


bluzepher@bluzepher-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

bluzepher@bluzepher-laptop:~$ 



So, went back to 7.10 Ubuntu.  I still can not connect to the internet.
I have spent the last 2 days trying to get this thing up and running as a wireless laptop.  
Does anyone out there have any ideas ?  

I did go thru Kevdog's post,   I dont see a wlan0 on my lshw listing.

thanks in advance for your help and ideas >

---

### Post by bluzepher on 2008-07-04
So, went back to 7.10 Ubuntu. I still can not connect to the internet.
I have spent the last 2 days trying to get this thing up and running as a wireless laptop. 

Does anyone out there have any ideas ?

I did go thru Kevdog's post, I dont see a wlan0 on my lshw listing.

thanks in advance for your help and ideas >

---

### Post by superprash2003 on 2008-07-05
are you able to see the wifi networks when you click on the network symbol in the top right part of the screen?

---

### Post by Kevbert on 2008-07-05
Looking at your output it looks like the firmware hasn't been installed.  Do you have the Broadcom wireless enabled in the restricted drivers list ?  Firmware is saved in the /lib/firmware directory. If you look there you should have a file something like bcm43xx...fw

---

### Post by bluzepher on 2008-07-05
Yes, broadcom is enabled in the drivers.
I am using wifi-radar and I can see several wireless connections, no I dont see any other connections when I click on the network symbol.









Ubuntu 7.10
HP Pavilion Laptop

---

