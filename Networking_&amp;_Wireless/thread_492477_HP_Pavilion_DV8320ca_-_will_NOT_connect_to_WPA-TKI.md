---
title: "HP Pavilion DV8320ca - will NOT connect to WPA-TKIP network"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by Steel Frog on 2007-07-04
Hi guys,
I've never really used Ubuntu before but I'm hoping to slowly introduce myself to it. Anyhow, I'm having a problem connecting to my WPA TKIP network.

It finds the network and prompts me to enter my key. Once I enter and hit connect, it says "Waiting for network key" and basically just stops after several minutes.

I'm not sure what to try or do and would really appreciate any help!
The network card is an Intel 3925.

Thanks guys!

> 06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by Steel Frog on 2007-07-04
I'm not sure if this info can help, but it's better than nothing.

> eth1      Scan completed :
          Cell 01 - Address: 00:14:6C:79:5D:DA
                    ESSID:"Steel Frog Media"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=90/100  Signal level=-41 dBm  Noise level=-41 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 20ms ago


---

### Post by Steel Frog on 2007-07-04
Some more info. This is what happens when it tries to connect.

> Listening on LPF/eth1/00:13:02:5b:c0:77
Sending on   LPF/eth1/00:13:02:5b:c0:77
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:d4:31:7b:b9
Sending on   LPF/eth0/00:16:d4:31:7b:b9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.4 -- renewal in 42230 seconds.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:5b:c0:77
Sending on   LPF/eth1/00:13:02:5b:c0:77
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


---

### Post by Steel Frog on 2007-07-05
Still haven't resolved this issue. :(

---

### Post by Steel Frog on 2007-07-16
I still haven't figured out the cause of this issue. It'd be really nice being able to use wireless instead of having that big blue cable dragging around the floor.

---

### Post by fredj on 2007-07-17
Open a terminal and type
'sudo lshw -class network' and post the output here.
In a terminal type 'cd /etc/network'
then type' sudo gedit interfaces' and post the contents of this file here.

---

### Post by Steel Frog on 2007-07-17
lshw:
```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:5b:c0:77
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=no multicast=yes wireless=unassociated
       resources: iomemory:54000000-54000fff irq:18
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@08:08.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:31:7b:b9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.5 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:d2006000-d2006fff ioport:3000-303f irq:21

```

There was nothing in the network file.

---

### Post by Steel Frog on 2007-07-17
Boink. Halp! :(

---

### Post by Steel Frog on 2007-07-19
Anything I can do guys? I searched, I went through the stickies but I just can't figure it out.

---

### Post by jglen490 on 2007-07-19
Looks like everything is present for duty in terms of your hardware and a driver.  So it can see your connection, but it just can't do anything about it.  That requires a network manager and because you are using wpa-tkip on you router it also requires wpa-supplicant.

I use kubuntu rather than ubuntu, so I am familiar with some of the KDE tools.  I would search for the network manager (gnome-network-manager, or something like that) and wpa-supplicant[ either on your machine or info here on the forum.

---

### Post by Steel Frog on 2007-07-19
> **jglen490 said:**
> Looks like everything is present for duty in terms of your hardware and a driver.  So it can see your connection, but it just can't do anything about it.  That requires a network manager and because you are using wpa-tkip on you router it also requires wpa-supplicant.

I use kubuntu rather than ubuntu, so I am familiar with some of the KDE tools.  I would search for the network manager (gnome-network-manager, or something like that) and wpa-supplicant[ either on your machine or info here on the forum.

Connects without a hitch through Windows. I've also swapped through three of my Wireless routers so I don't think it's a network issue unfortunately. =/
Wired works fine by the way. It also picks up the network without a hitch, but it just won't connect to it.

---

### Post by fredj on 2007-07-20
Open a terminal and go to /etc/network. Use 'gedit interfaces' to look at the interfaces file. 
You should have only two lines in there that refer to your eth1 wireless interface. They are
auto eth1
iface eth1 inet dhcp  (I assume you are using dhcp to get a network address)
If there are any other eth1 references then remove them. Double click on the network manager icon in the
taskbar. It should show a list of wireless networks so you can select the one you want to connect to.
When you select a network it should ask for your WPA key. Click on the show password box to make 
sure you are typing it correctly. If it still won't connect then make sure that wpasupplicant is installed
using the System-Aministration-Synaptic Package Manager (although I think it is installed by default).

---

### Post by Steel Frog on 2007-07-20
Thanks for the tips, Fredj. Here are my results however:

[LIST]
[*]The 'network' file is empty. I think I'm the one who deleted it's content by mistake while I was reading through a few threads. I'll enter what you've posted and see.
[*]I do believe I'm going through DHCP since the routers are pretty standard and basic.
[*]I see the connection and it does prompt me for the password, which I enter, but after that it just sits there for 10 to 15 minutes trying to connect and eventually just stops trying.
[/LIST]

---

### Post by jglen490 on 2007-07-20
> **Steel Frog said:**
> Connects without a hitch through Windows. I've also swapped through three of my Wireless routers so I don't think it's a network issue unfortunately. =/
Wired works fine by the way. It also picks up the network without a hitch, but it just won't connect to it.

The fact that it works via Windows has nothing to do with getting it to work under Ubuntu.  What I was referring to is software that acts as a network manager - it actually manages the connection(s) that you are seeing right now, but that yoiu can't reach right now.  Also, the wpa-supplicant software in Linux is required to match and manage the wpa-tkip security protocol that is activated on your router with your wifi card by using that protocol within the circuitry on your wifi card.

You simply need to use that software to actvate and use the wireless connection between your wifi card and the router.

---

