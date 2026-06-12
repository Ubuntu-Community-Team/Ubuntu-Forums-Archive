---
title: "broadcom bcmwl5 problem"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by fasterthanjesus on 2008-05-08
*-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth1
       version: 02
       serial: 00:16:ce:55:cf:79
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,12/22/2004, 3.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


hi and help!

im running heron with kde 3 and have not managed to get wireless connectivity.  i have now been banging my head for a week and i can see networks, but cant connect to "sky broadband" using ndiswrapper bcmwl5.

bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)

i won the battle in gutsy by blacklisting the previous alternate driver.  ive now got ssb???  and its not playing ball.  i can see a 169 ip address and an avahi reported, and it should be a 192 address.

ive read things, installed things, removed things, hit things, argued with the wife, hit the bottle, started smoking again and even contemplated going back to o/s bill.

All help gratefully received.

ftj

---

### Post by chrisubuntu on 2008-05-08
I endured similar pain with my BCM4318 ... I did all kinds of funky things, with ndiswrapper/blacklisting and the like. At one point it would easily connect to WEP based routers, but not WPA .. 


And then, I saw the light.... I clicked on the little icon in the task bar that said 'click here to enable restricted driver' (paraphrasing) 
I followed it's instructions and voila! all good! Nothing more to do. I was shocked.


I know that's not terribly specific, at potentially unhelpful, but I don't have access to the machine right now...

---

### Post by Ayuthia on 2008-05-08
Can you post the results for 
```
lsmod|grep -i -e b43 -e b44 -e ssb -e ndiswrapper
lspci -nnd 14e4:*
```
We need to see if the b44 module is going to be a factor.  For this session you can try:
If b44 does not show up:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe ndiswrapper
```
If b44 does show up:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
```

The b43 and b44 modules need to have the ssb module.  However, the ssb module needs to be loaded after ndiswrapper if it is needed.

---

### Post by fasterthanjesus on 2008-05-08
i dont seem to have the little icon.

my restricted driver only displays modem, not wireless.

can you email me the little icon?   :)

---

### Post by fasterthanjesus on 2008-05-08
b44                    28432  0 
ssb                    32260  1 b44
ndiswrapper           192920  0 
mii                     6400  2 b44,sis900
usbcore               146028  4 ndiswrapper,ehci_hcd,ohci_hcd


00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)


:)

---

### Post by Ayuthia on 2008-05-08
> **fasterthanjesus said:**
> i dont seem to have the little icon.

my restricted driver only displays modem, not wireless.

can you email me the little icon?   :)Sorry, the commands that I provided are for using in the Terminal.  As far as I know, there is no icon version.  :(

---

### Post by Ayuthia on 2008-05-08
> **fasterthanjesus said:**
> b44                    28432  0 
ssb                    32260  1 b44
ndiswrapper           192920  0 
mii                     6400  2 b44,sis900
usbcore               146028  4 ndiswrapper,ehci_hcd,ohci_hcd


00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)


:)

I am going to assume that the b44 module came from a guide that you used because there is no Broadcom ethernet card (wired).

Anyway, have you tried connecting your wireless through the Terminal?  If so, what happens when you use dhclient?

---

### Post by fasterthanjesus on 2008-05-08
with the utp out.

There is already a pid file /var/run/dhclient.pid with pid 6775
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:16:ce:55:cf:79
Sending on   LPF/eth1/00:16:ce:55:cf:79
Listening on LPF/eth0/00:16:36:59:30:7c
Sending on   LPF/eth0/00:16:36:59:30:7c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPREQUEST of 192.168.0.2 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPREQUEST of 192.168.0.2 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Ayuthia on 2008-05-08
> **fasterthanjesus said:**
> with the utp out.

There is already a pid file /var/run/dhclient.pid with pid 6775
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:16:ce:55:cf:79
Sending on   LPF/eth1/00:16:ce:55:cf:79
Listening on LPF/eth0/00:16:36:59:30:7c
Sending on   LPF/eth0/00:16:36:59:30:7c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPREQUEST of 192.168.0.2 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPREQUEST of 192.168.0.2 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I'll take it that you can see wireless access points through sudo iwlist scan.  If you are using encryption, take it out for now and see if you can connect.  You might even change the channel on your router.

---

### Post by fasterthanjesus on 2008-05-09
bingo. :KS

changed driver to one from attached list.

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

re-added network manager through synaptic.

changed to wep.  and dropped the channel number down.

will try wpa psk at a later date.

many thanks to ayuthia

---

