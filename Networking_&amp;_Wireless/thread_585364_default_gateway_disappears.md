---
title: "default gateway disappears"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by TheWizzard on 2007-10-21
i'm completely stuck with my wifi. 
here's the story:
i installed gutsy on a desktop pc with a ralink rt61 wifi card (linksys). the card worked before in dapper. i used the same method to install the drivers. 
the card seems to work out of the box. i was able to connect to my network with knetworkmanager, although the first attempt always failed and the second attempt succeeded. this is not very practical.

however, i tried to connect by setting /etc/network/interfaces. this is what i always do. 
this is where the trouble starts. my default gateway is either disappearing or it is set to 0.0.0.0
does anyone know what's happening and what i can do to set my default gateway permanently?? it looks like there's a deamon messing with the network settings. i disabled knetworkmanager, but that didn't help. 

on "sudo route add default gw 192.168.1.1" i often receive an error message. but not all the time... 

is there anyone who understand what's going on???

cheers, wizzard

---

### Post by Hero of Time on 2007-10-21
What error do you get when you get it? What if you uninstall knetworkmanager and networkmanager, set a static ip address with the gateway and bring the interface back up with ifup eth1 (or whatever name your wifi has). You can also use ifconfig to set an ip address. If you use DHCP, try a new lease with dhclient.

---

### Post by TheWizzard on 2007-10-22
the problems is that my routing table disapperars.
 i disabled knetworkmanager. is networkmanager active when knetrworkmanager is not started? 
i did set a static ip with default gw. 

groeten

---

### Post by Hero of Time on 2007-10-22
Yes, it's possible Network Manager still runs. Afterall, knetworkmanager runs on network-manager, just like gnome-network-manager does. That's why I asked to remove them. It's still strange though, as any network manager should keep the settings that the user sets.

---

### Post by TheWizzard on 2007-10-22
worked like a charm! thanks hero.
actually i remember i had the same problem a few years ago in fedora core 2. 

i have now one smaller problem left. the network daoesn' t start on bootup. i can' t ping the router. after
sudo /etc/init.d/networking restart
everything works fine. any clues?

cheers

---

### Post by Hero of Time on 2007-10-23
Check your /etc/network/interfaces file and check if every interface is listed as auto and have valid settings. Since networking restart works, I think your interfaces aren't started automatically.

---

### Post by TheWizzard on 2007-10-23
i can' t see anything unusual in /etc/network/interfaces

```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface wlan0 inet static
address 192.168.1.102
netmask 255.255.0.0
gateway 192.168.1.1
wireless-essid Homelan99
wireless-key xxxxxxxxxxxxxxxxxxxxx
auto wlan0

iface eth0 inet dhcp
auto eth0

```



however, i get feedback when i start the network. it is similar to this tread:
[http://ubuntuforums.org/showthread.php?p=3606918](http://ubuntuforums.org/showthread.php?p=3606918)

any ideas???

```
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                   There is already a pid file /var/run/dhclient.eth0.pid with pid 4678
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1d:60:0d:99:3b
Sending on   LPF/eth0/00:1d:60:0d:99:3b
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1d:60:0d:99:3b
Sending on   LPF/eth0/00:1d:60:0d:99:3b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                                                  [ OK ]

```

---

### Post by TheWizzard on 2007-10-23
mmm, i've been messing around with drivers. looks like i created a problem. i'll try a fresh install.

---

