---
title: "I can't connect to ADSL Router"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by SuperBo on 2008-01-01
I use PTI-845S ADSL router, In windows XP, I can connect to internet, but in Ubuntu 7.10, I can't.
I also go to terminal and type:
```
sudo pppoeconf
```
The wizard cannot find any connection, please help me. Without internet, I cannot do anything.
](*,)](*,)

---

### Post by Predator[23rd] on 2008-01-01
Isn't your router managing your connection and distributing IP addresses to your LAN? If so all you need to do is to enable DHCP in Ubuntu and not try to setup a PPPoE connection.

to simply and quickly enable DHCP go to /etc/network/interfaces and assuming only one ethernet card the line you should look for: 
[I]
auto eth0
iface eth0 inet dhcp[/I]

check this and restart your network with **sudo /etc/init.d/networking restart**

---

### Post by SuperBo on 2008-01-01
I have tried.
"check this and restart your network with sudo /etc/init.d/networking restart"

>  * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5896
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:f0:f3:36:00:c9
Sending on   LPF/eth0/00:f0:f3:36:00:c9
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:f0:f3:36:00:c9
Sending on   LPF/eth0/00:f0:f3:36:00:c9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]


This is the result. I am still unable to connect to internet, help me please!#-o#-o

---

### Post by Predator[23rd] on 2008-01-01
looks like there is no DHCP server running.

can you connect to your router (administration interface) and make sure that you have enabled the router's DHCP server?

---

### Post by SuperBo on 2008-01-01
The DHCP server is OK.
Please watch my attachment.:confused::confused:

---

### Post by Predator[23rd] on 2008-01-01
can you please try to setup a static IP for your NIC in ubuntu. if that works we have to find out why the DHCP client failed.

**/etc/network/interfaces**

[i]auto eth0
iface eth0 inet static
        address 192.168.1.10
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0
        gateway 192.168.1.1[/i]

---

### Post by SuperBo on 2008-01-01
I have try, but  I can't connect to internet.
I use network card onboard (Intel D865).
Do I install driver for it.

---

### Post by Predator[23rd] on 2008-01-01
no. you should not need to install any drivers since the OS is detecting a network card (eth0).

what puzzles me a bit is your LAN setup. you are setting up a static ip for your router and define a gate etc. I have used three different wireless lan routers and never did such a thing. I set up a subnet and left gateway configuration etc. to the router itself. i.e.
internal network subnet 192.168.2.0 and router IP (for internal network) 192.169.2.1. the router itself knows that the WAN port has to be the gateway etc.

I would have expected your setup screen to look more like a check in the "Optain an IP address automatically" and then the "Enable DHCP Server" part as you already have it.

BUT then every router software and configuration method is a bit different.

Point is: can you give a bit more information about your network topography? I am a bit lost ... :)

---

### Post by SuperBo on 2008-01-02
I only have one modem and one internet connection.
I windows, it is automatic to connect to the internet.

---

### Post by SuperBo on 2008-01-04
Please help me. I couldn't connect to my ADSL modem.

---

