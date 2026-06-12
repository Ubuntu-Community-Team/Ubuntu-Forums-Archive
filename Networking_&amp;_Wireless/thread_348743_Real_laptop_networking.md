---
title: "Real laptop networking"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by ojinka on 2007-01-29
Hi
I have got laptop asus a6jc. I often take it to my girlfriend or to school. Everywhere are different network types and my ubuntu is not so flexible as windows.
At home i am using flarion <eth2> (its PCMCIA card, i put it into laptop and it looks like new ethernet adapter) I share this net through netwokr card <eth0>. On eth0 i have static IP adress 192.168.0.1
When i take my laptop to school, there ist wifi conection, i have wifi card as <eth1> and there is strange problem. Network manager connects me to that network, i recive IP adress, bud no internet or ping. I have no idea how to do that.

When i take my laptop to my friend he has got router. I recive IP adress bud no internet or network. Its look like conected but it is not. I have to restart ubuntu and than it is working.

In windows there is no problem, everithing works just perfect, but i hate windows.

Thanks you very very much.

---

### Post by moon_dog on 2007-01-29
try connecting manually through the terminal, see if that works.
type:
```

sudo iwlist eth1 scan

```

something like this should appear (in my case only one cell appeared because there aren't any other wireless networks in my area):

```
eth1      Scan completed :
          Cell 01 - Address: 00:0D:08:01:34:C5
                    ESSID:"CTC"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=76/100  Signal level=-53 dBm  
                    Extra: Last beacon: 48ms ago

```

then type this (replace the underlined words with whatever data shows up in your scan):

```
sudo iwconfig eth1 essid "_CTC_" channel _11_ key off mode managed
```

to see if you were able to connect, type ```
iwconfig
``` and compare the data with your scan.

finally, to receive an IP, type:
```
sudo dhclient
```

you should see something like this
```
There is already a pid file /var/run/dhclient.pid with pid 17340
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:00:f0:81:a4:ec
Sending on   LPF/eth0/00:00:f0:81:a4:ec
Listening on LPF/eth1/00:0e:35:2c:ab:f1
Sending on   LPF/eth1/00:0e:35:2c:ab:f1
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.100.100
bound to 192.168.100.103 -- renewal in 275400 seconds.

```

---

### Post by lavinog on 2007-02-04
try wifi-radar
it will automatically connect to wireless networks that you specify when you are in range.
it seems to work better than winxp's wireless connection manager

---

