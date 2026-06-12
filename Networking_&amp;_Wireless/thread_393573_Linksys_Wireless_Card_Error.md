---
title: "Linksys Wireless Card Error"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by 88tuner on 2007-03-25
I'm new to Ubuntu and linyx.  I need to get my wireless card working and I think it's close but I came across a glitch.

I just installed Feisty Faun on my computer.  I have a Linksys wmp54G wireless card.  Ubuntu sees the card and and it shows my wireless account and that it needs a wep key.  I open the connection but it won't let me enter the key.  I can't even click in the window to put the key in.  Also, I can't access the network tool.  It's just a blank screen.  Any ideas?  Do I need to install a driver?

---

### Post by JengaBlocks on 2007-03-25
I been having problems with the card also. I had WMP54G v1.0 and went out and bought a new one (version 4.1). So far, I've yet to get it to work. I really haven't seen any hard evidence that this card works at all in Linux. Currently my problem seems to be ndiswrapper and WEP - they just don't work well.

---

### Post by beauwulf on 2007-04-06
> **JengaBlocks said:**
>  ... I really haven't seen any hard evidence that this card works at all in Linux. Currently my problem seems to be ndiswrapper and WEP - they just don't work well.

Here ya go :)  a WMP54G v4.1 running under Feisty

```
steve@loki:~$ lshw
.
.
.
           *-network
                description: Wireless interface
                product: RT2561/RT61 802.11g PCI
                vendor: RaLink
                physical id: 6
                bus info: pci@02:06.0
                logical name: ra0
                version: 00
                serial: 00:18:f8:30:6b:21
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS ip=192.168.1.104 latency=32 multicast=yes wireless=RT61 Wireless
                resources: iomemory:e0000000-e0007fff irq:20
.
.
.
```

Wasn't exactly painless though. Completely removed ndiswrapper (the drivers are already present.

```
steve@loki:~$ modprobe -l | grep rt61
/lib/modules/2.6.20-14-generic/kernel/ubuntu/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.20-14-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt61/rt61.ko

```

I also had to remove Network Manager and not use the GUI network configuration tool otherwise I get freeze-ups. I manually edited the /etc/network/interfaces file to add:
```
iface ra0 inet dhcp
wireless-essid Baalrog
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx
auto ra0
```

And I have to issue ifdown ra0 and ifup ra0 after start-up to get it working. But it is working -ish

---

### Post by Pikestaff on 2007-04-07
> **JengaBlocks said:**
> I been having problems with the card also. I had WMP54G v1.0 and went out and bought a new one (version 4.1). So far, I've yet to get it to work. I really haven't seen any hard evidence that this card works at all in Linux.

This card worked 100% out of the box for me in Dapper.  But I couldn't get it to work at all in Edgy, and now I'm not so sure I want to try Feisty :-?  Beauwulf's solution sounds kind of complex... not sure if I want to try it or not :p

---

### Post by 68hc11 on 2007-04-07
I'm in a similar quandry.  The card seems to install fine under Fawn, I can even seen that the card is connected to my accesspoint and actively keeping the connection alive.

I can not establish network connections via Ubuntu, nor ping the router (192.168.0.1).

A wired Eth0 connection works fine.

I was not able to completely perform Beauwulf's as I don't know how to enable the rights to issue "ifdown" & "ifup" commands.

Any suggestions appreciated.

68hc11

---

### Post by beauwulf on 2007-04-07
> **68hc11 said:**
>  .. how to enable the rights to issue "ifdown" & "ifup" commands.

Any suggestions appreciated.

68hc11

Sorry, I wasn't clear on that. You should be able to use those commands in a terminal window using sudo to enable root rights.

```
steve@loki:~$ sudo ifdown ra0
Password:
There is already a pid file /var/run/dhclient.ra0.pid with pid 5465
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:18:f8:30:6b:21
Sending on   LPF/ra0/00:18:f8:30:6b:21
Sending on   Socket/fallback
DHCPRELEASE on ra0 to 192.168.1.1 port 67
steve@loki:~$ sudo ifup ra0
There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:18:f8:30:6b:21
Sending on   LPF/ra0/00:18:f8:30:6b:21
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.105 -- renewal in 36552 seconds.
steve@loki:~$ 

```

---

### Post by 68hc11 on 2007-04-07
Thanks for the response.  attempted follow up below.
I see I'm using 192.168.0.1 instead of 192.168.1.1 as in your example

Any suggestions appreciated.
68hc11


sam@sam-desktop:~$ ifdown ra0
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
sam@sam-desktop:~$ sudo ifdown ra0
Password:
There is already a pid file /var/run/dhclient.ra0.pid with pid 3940
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:18:f8:2e:4b:27
Sending on   LPF/ra0/00:18:f8:2e:4b:27
Sending on   Socket/fallback
DHCPRELEASE on ra0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
sam@sam-desktop:~$ sudo ifup ra0
There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:18:f8:2e:4b:27
Sending on   LPF/ra0/00:18:f8:2e:4b:27
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
sam@sam-desktop:~$

---

### Post by beauwulf on 2007-04-07
Well that part does look correct. The different address is no big deal, our routers just happen to use different addresses, the 255.255.255.255 mask on DHCPDISCOVER shows that your card should find the router no matter what it's address is.

Since you got that far, I think you can safely say the wireless card is working, it's just not finding the router, or at least not getting an address from it. 
On ifdown you get a message saying the network is unreachable so I wonder if there's an issue with signal strength, or setting the correct ESSID or WEP key (if you're using it).
A tool like Wifi-radar might be useful to find out what your card can see out there.

---

### Post by 68hc11 on 2007-04-08
After struggling with this for many hours I have hit upon something that works.  I can't explain it but perhaps it will assist someone else....

I was able to get my Linksys WMP54G V4.1 to be recognized as ra1  (I tried so many things I'm not sure what exactly hit upon this but I think this installed properly form the start?)

download wireless Assistant 0.5.5 (I think there is a newer version but this is the one in Ubuntu under Applications Add/Remove)

Run this program fromthe terminal, (not using the GUI since it doesn't have full privlidges under GUI.)

sudo wlassistant

This will bring up your GUI and from there you can revise your info and request a connection, that in my case was successful.

Note: The wireless network icon in the upper right corner will still not show connection despite Firefox and appget working well.

68hc11

---

