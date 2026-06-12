---
title: "can't get dhcp to assign IP to eth0 or eht1"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by speed32219 on 2007-04-19
I am trying to setup a workstation that has a WiFi MA101 (net gear 802.11b) USB interface to act as a gateway for an Xbox to access the Internet.  

I have set the Xbox for DHCP IP attached to a 5 port switch.  I then have a cat5e to my workstation (Ubuntu) that is working with a Net Gear MA101 USB attached wireless interface (Using HDCP from the DL-524 DSL Gateway to get my IP).  I am posting this message using the Ubuntu wireless setup and there is no problem. I have it setup for  two subnets, Wireless DHCP to Gateway  192.168.0.XXX while the wired is 192.168.1.XXX

I have configured the two nics in the Ubuntu box using DHCP also.  I downloaded and isntalled DHCP using apt-get as well as firefox.  I can use Static IP's and the Xbox works great with the Ubuntu as a SMB attached Video Server (Without GW access through the Ubuntu which is why I am trying a different approach) , but I can not get DHCP to work.  Below are some outputs from some commands.  I have also installed BUM (Boot Up Manger) and I had to go into it and Start the DHCP, but I do not think it is running since I do not get the light bulb, I instead get the ?  and it always has start as an option, while the other processes only have de-activate or stop. (Start is not the third option)  I have tried multiple configs in Firestarter,  Networking and Networking tools to no avail.    Need some assistance or guidance please.  Thanks in advance.

 **sudo dhclient eth0**
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:92:21:24:8b
Sending on   LPF/eth0/00:1a:92:21:24:8b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


** sudo ifconfig eth0**
eth0      Link encap:Ethernet  HWaddr 00:1A:92:21:24:8B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 

 **sudo ethtool eth0**
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: Unknown! (65535)
        Duplex: Unknown! (255)
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x00000037 (55)
        Link detected: no

** sudo lshw -C network **
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@01:0b.0
       logical name: eth1
       version: 10
       serial: 00:06:4f:3f:24:e9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:e800-e8ff iomemory:fbfffc00-fbfffcff irq:201
  *-network:1
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: d
       bus info: pci@01:0d.0
       logical name: eth0
       version: 13
       serial: 00:1a:92:21:24:8b
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=skge driverversion=1.5 firmware=N/A link=no multicast=yes port=twisted pair
       resources: iomemory:fbff8000-fbffbfff ioport:e400-e4ff irq:193
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:09:5b:30:cc:9d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76c503 driverversion=v0.12beta23-fw_dwl firmware=1.101.2-84 ip=192.168.0.105 wireless=IEEE 802.11-DS

---

### Post by speed32219 on 2007-04-19
OK looks like I did not have the right DHCP server installed.  I removed and installed dhcp3 server with clients and stuff.  Now I need to modify DHCPD.conf in the etc directory.  My 2 separate networks are 192.168.0.xxx Wireless) and 192.168.1.xxx for the wired that I want to to get across.  Any of you out there have a sample dhcpd.conf for similar network you could share.

I hope, I Hope, I Hope. :D

---

