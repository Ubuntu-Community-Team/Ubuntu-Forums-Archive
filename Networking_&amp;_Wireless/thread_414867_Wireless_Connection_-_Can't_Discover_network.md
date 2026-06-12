---
title: "Wireless Connection - Can't Discover network"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by jerremy-tamlin on 2007-04-20
Hi,

I'm using Dapper 6.06
My Wireless card on my laptop wasn't configured properly by default and so I was using a PCMCIA card which worked fine except that I had to continually borrow one from my uni.

I recently fixed the configuration of my built-in wireless card in /etc/network/interfaces and now the card seems to work. However, I can't connect to the uni's network anymore.

```
auto lo
iface lo inet loopback

#Internal Wireless Card
auto eth1
iface eth1 inet dhcp
wireless-essid MuWLAN
#wireless-key s:story

#Palmyra Config
auto eth2
iface eth2 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1

#Built in Modem - No Driver!
#auto ppp0

#Modem
#auto eth0
```

When I first start my laptop the wireless card is detected and the signal has plenty of strenght. However, the strength goes up and down a lot and some data is being transmitted and/or recieved.

The IT people at my uni don't support linux and while they try to be helpful they can't give me much advice except to say that there is no WEP Key needed as their wireless network is public and extrememly limited without using vpn.

I have the vpn software installed and it was working properly but now it fails to authenticate me and says ```
Secure VPN Connection terminated locally by Client
Reason: Failed to Enaible Virtual Adapter
```

data still gets transmitted and something is happening but after a while it must give up and the connection gets disabled. I need to find out where the logs are so I can see what it is doing and perhaps discover why it's not working.

When I do "/etc/init.d/networking restart" I get network down errors. The Network Is Not Down - I'm using it to send this post.
```
jesse@windwanderer:~/dnld$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:20:e0:d0:ad:00
Sending on   LPF/eth1/00:20:e0:d0:ad:00
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 134.115.4.33 port 67
SIOCSIFFLAGS: Input/output error
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: Input/output error
SIOCSIFFLAGS: Input/output error
Listening on LPF/eth1/00:20:e0:d0:ad:00
Sending on   LPF/eth1/00:20:e0:d0:ad:00
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]
```

Thanks in advance to anyone who can help.

---

### Post by nise8181 on 2008-04-24
Hello,

I've got exactly the same problem.
Everytime I restart /etc/init.d/networking after a reboot I stay connected for about 10 seconds before it breaks down. 

I tried ```
iwconfig
``` wich says that there is a device called wlan0. All parameters that I've entered in /etc/init.d/interfaces seem to be available (at least my essid).

Now I am not sure if that problem is related with my hardware - a Hama wireless USB stick or something else.


Usefull to configure any WP2 wireless connection was: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

