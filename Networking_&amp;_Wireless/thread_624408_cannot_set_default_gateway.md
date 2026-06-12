---
title: "cannot set default gateway"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by MyKal on 2007-11-26
ok i have an averatec laptop with the via vt6102 (rhine II) ethernet controller and ralink rt2500 802.11g cardbus/minipci (rev01) wireless network controller 

however from what i can see neither of them are being seen by the networking tools in kubuntu gutsy 

when i do lspci they are both present and accounted for but as far as the network manager in kde is concerned there just not there 

i could have sworn that i saw them both listed on the network tools page when i first finished installing kubuntu but as soon as i tryed to get onto the net it said that i had no connection so i went to investigate and found that my default gateway was 0.0.0.0. and i apeared to have no networking hardware set up 

i am not big on networking its just not where my talents lye so please if anyone can be of any service i would REALLY apreciate it if anymore information is needed just ask and i will be happy to provide anything you need

also it may be worth noting that i know for a fact that my networking hardware on the computer has to be working because i did this install from the mini install cd wich only starts off the installation process from the disk but downloads all of the software from the internet (i prefere it to having to do a bunch of updates after the live installer finishes)

---

### Post by elctb on 2007-11-27
lspci only shows what devices are connected to the pci bus.

You need to install the drivers for those devices to use them. Type "ifconfig -a" and post what you get. Depending on the output of ifconfig you need to install/load the drivers or configure the interfaces.

---

### Post by kevdog on 2007-11-27
Here is how to set the default gateway

sudo route add default gw 192.168.99.254

Again the 192.168.99.254 value may have to be changed depending on your setup

---

### Post by MyKal on 2007-11-27
ok 

the output of ifconfig -a is as follows:

eth0      Link encap:Ethernet  HWaddr 00:40:45:19:1F:2C
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xd800

eth0:avah Link encap:Ethernet  HWaddr 00:40:45:19:1F:2C
          inet addr:169.254.2.110  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          Interrupt:11 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:26468 (25.8 KB)  TX bytes:26468 (25.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0C:76:CA:C5:60
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:0C:76:CA:C5:60
          inet addr:169.254.8.75  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-0C-76-CA-C5-60-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by elctb on 2007-11-27
The drivers for both the wired and wireless network devices are loaded.

Try the following:

```
sudo ifconfig eth0 down
sudo dhclient eth0
```

Post any error you get, if any.

---

### Post by MyKal on 2007-11-27
ok tryed that and still a no go,  heres what i got:

Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:40:45:19:1f:2c
Sending on   LPF/eth0/00:40:45:19:1f:2c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by elctb on 2007-11-27
> **MyKal said:**
> 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

This means the dhcp server never replied to the request for an ip address sent on eth0.

Do this:

tail -f /var/log/messages

Then physically unplug the eth0 ethernet cable. You should see something like "eth0: link is down". Then plug back in the ethernet cable. You should see something like "eth0: link is up at 100 Mbps"

If you see these messages, it might be that the router doesn't have a dhcp server running. Do you have a different machine or windows that successfully connects to the router ? If so, post the configuration they are using.

---

### Post by MyKal on 2007-11-27
ok i ran the command and i unplugged my ethernet and then replugged it and got absalutely nothing when i click on the network icon in the system tray it tells me that i have no devices specified could this be the problem and if so how do i get it to recognise my devices (since i obviously do have the drivers and they are tested and working) 

i am including a screenshot in case that might help

---

### Post by elctb on 2007-11-27
I had all sort of problems using the network manager. I ended up removing it completely and manually editing the config files.

Have you tried using a static ip address ? For that you need to know what subnet the router is using (something like 192.168.1.0). If you have another computer connected to the router, you can find out by looking at the configuration it's using.

Also, check if you have tcpdump installed in your ubuntu machine. You can use tcpdump to dump all ip packets sent/received on eth0. To see if it's installed, just type "sudo tcpdump -i eth0".

---

