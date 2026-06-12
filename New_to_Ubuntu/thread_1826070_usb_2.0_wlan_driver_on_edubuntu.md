---
title: "usb 2.0 wlan driver on edubuntu"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by callmebadger on 2011-08-16
hi all,
i am an absolute beginner.  :confused:
recently i installed edubuntu 10.04
i now want to move it to the kids room, but i was wanting to use a  wireless usb stick that was given to me, without any drivers, all information i have found on this old stick  below

[http://www.lambda-tek.com/componentshop/index.pl?prodID=B103543&viewSpec=y#productTop](http://www.lambda-tek.com/componentshop/index.pl?prodID=B103543&viewSpec=y#productTop)  similar
*** [http://www.bestrico.com.tw/images/WU61S.pdf](http://www.bestrico.com.tw/images/WU61S.pdf)  **** looks same
[http://www.ebay.co.uk/itm/NET-LYNX-WIRELESS-USB-2-0-ADAPTER-NETWORK-/190520670457#vi-desc](http://www.ebay.co.uk/itm/NET-LYNX-WIRELESS-USB-2-0-ADAPTER-NETWORK-/190520670457#vi-desc)  looks similar but mine does not have net-lynx on it.
although my stick only has this written on it.
on the back:-
WU61S
FCC ID:RXZ-WU61S
S/N GWU195
0641E000407
00064F43136F
on the front:-
WLAN USB2.0 54bps Adapter
LINK (near the led)

I have used this on xp and had to find drivers to use this the drivers were a nightmare to find. the bestrico website looks identical to mine.

also i found a list of drivers
[http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers)

my question is how do i tie in the information i have with the linuxwireless drivers list in order to identify the correct driver? 
or if there is a better way let me know.

also when i have this downloaded to my os how do i go about installing this in order to use this usb wlan?
please bare in mind i only just found TERMINAL yesterday by following some instructions for other users and ubuntu's help.

i am also interested to hear if people suggest not to bother with this usb wlan it wont work and if this is true what item of ebay or other websites a like would they suggest. thankyou


ps

 sudo lshw -C network
*-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:11:09:d7:e2:68
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:23 ioport:e700(size=256) memory:ee011000-ee0110ff
  
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0457:0163 Silicon Integrated Systems Corp. 802.11 Wireless LAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
  
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:09:d7:e2:68  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fed7:e268/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:665931 (665.9 KB)  TX bytes:145158 (145.1 KB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7088 (7.0 KB)  TX bytes:7088 (7.0 KB)
does this help?

---

### Post by callmebadger on 2011-08-16
job done
[http://www.linuxforums.org/forum/ubuntu-linux/181792-wireless-drivers-wu61s-edubuntu.html](http://www.linuxforums.org/forum/ubuntu-linux/181792-wireless-drivers-wu61s-edubuntu.html)
jayd512 answered the question for me.

he directed me to 
[https://help.ubuntu.com/community/WifiDocs/Device/Pentagram_Hornet_USB_Lite](https://help.ubuntu.com/community/WifiDocs/Device/Pentagram_Hornet_USB_Lite)

begining to love ubuntu

---

