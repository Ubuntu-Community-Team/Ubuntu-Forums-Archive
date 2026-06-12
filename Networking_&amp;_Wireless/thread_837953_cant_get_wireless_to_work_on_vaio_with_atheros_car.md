---
title: "cant get wireless to work on vaio with atheros card"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by cti on 2008-06-23
SOLVED

all i had to do was follow the insturctions here
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)



running 8 (hardy?) on a sony vaio vgnn320e. wired internet and everything else works great but i cant seem to get the wifi up and running. it appears in system/networks but if i unplug my wired connection i cant do anything. 

i can see the card

 > $ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:13:a9:c8:63:23
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.13.16 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:7e:3f:25:e3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g


it says its called wifi0

but in system > administration > networks
the wireless is bound to ath0

sudo iwlist ath0 scanning shows me a list of networks, including my own, 

>  sudo iwconfig wifi0 essid MYNETWORK
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wifi0 ; Invalid argument.


fair enough


so i tried it with sudo iwconfig essid ath0 mynetwork

gives me new command prompt

i type "sudo iwconfig key [mykey]
output : "invalid argument [mykey]"

(i skip that step when i try with the encryption turned off, which is a pain to keep turning on and off, since every time i change it it kicks my gf offline on the other computer.)


i try to get an ip

it tells me this (after i unplug my wired connection)

> $ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 23326
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:19:7e:3f:25:e3
Sending on   LPF/ath0/00:19:7e:3f:25:e3
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/eth0/00:13:a9:c8:63:23
Sending on   LPF/eth0/00:13:a9:c8:63:23
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPREQUEST of 192.168.13.16 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPREQUEST of 192.168.13.16 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


also, not sure if this is related but if i go 
> cti@vaio:/$ sudo iwlist wpakeys
lo        no wpa key information.

wifi0     no wpa key information.

ath0      3 key sizes : 40, 104, 128bits
          4 keys available :
		[1]: off
		[2]: off
		[3]: off
		[4]: off
          Current Transmit Key: [1]


eth0      no wpa key information.


should there be somehting in there? how could i enter my key in there, will that even help?

also tried a static ip through gui, no luck ther eeither. 

any ideas as to what might be going on?

im pretty confused. and a total n00b. any help would be appriciated.

---

### Post by cti on 2008-06-23
ive tried joining other networks too btw, same deal.

---

### Post by Pjotr123 on 2008-06-23
You should use only Network Manager for connecting in this case, I think. Click on the "double terminal" icon in the upper right of your screen.

First check if you've got the right driver:
[http://ubuntutip.googlepages.com/nointernetconnection](http://ubuntutip.googlepages.com/nointernetconnection)

---

