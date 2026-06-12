---
title: "Wireless+WPA needs a network restart before working??"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by ssalman on 2006-10-05
[FONT=&quot][FONT=Verdana]I've been using NetworkManager for my WPA enables wireless connection with a visible ESSID, but I've read somewhere on this forum that I can use hidden ESSID but not with NM, so I go and setup my interfaces file to connect. But I'm puzzled with the following issue... After boot I don't have a connection (my card is scanning for ever), only when I restart my network I get connected... isn't this just running the network booting script twice? Why would it work the second time and not the first? What am I missing?[/FONT]
 
 [/FONT]Thanks.


my /etc/network/interfaces file
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet static
    wpa-driver madwifi
    wpa-ssid <<My_SSID>>
    wpa-psk <<My_PSK_Key>>
    wpa-key-mgmt WPA-PSK
    wpa-pairwise TKIP
    wpa-group TKIP
    wpa-proto WPA
    wpa-conf managed
    wpa-scan-ssid 1
    wpa-ap-scan 2
    address 192.168.2.5
    netmask 255.255.255.0
    network 192.168.2.0
    broadcast 192.168.2.255
    gateway 192.168.2.1
    dns-nameservers 192.168.2.1

```the output when I restart my network after boot
```

$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces... Internet Systems Consortium
DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on   LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPRELEASE on eth0 to xx.xx.x.xxx port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on   LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                      [ ok ]
$ ping www.google.com
PING www.l.google.com (72.14.203.104) 56(84) bytes of data.
64 bytes from 72.14.203.104: icmp_seq=1 ttl=238 time=44.8 ms
64 bytes from 72.14.203.104: icmp_seq=2 ttl=238 time=44.9 ms
64 bytes from 72.14.203.104: icmp_seq=3 ttl=238 time=45.3 ms
64 bytes from 72.14.203.104: icmp_seq=4 ttl=238 time=44.2 ms
64 bytes from 72.14.203.104: icmp_seq=5 ttl=238 time=44.7 ms

--- www.l.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4016ms
rtt min/avg/max/mdev = 44.282/44.833/45.302/0.358 ms
$

```

---

### Post by Clanman on 2006-10-07
This is exactly my problem too
Although I run in dhcp mode

I also have to restart my network for it to work

/etc/network/interfaces

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
        wpa-driver madwifi
        wpa-ssid <<my ssoid>>
        wpa-key-mgmt WPA-PSK
        wpa-psk <<my psk >>


Not a big problem but anoying
I think its time to get a better support for wifi and especially wpa direct in Ubuntu

//Clanman

---

### Post by ssalman on 2006-10-10
So can I conclude that this is an Atheros only problem?? would updating the driver to the latest version help? Thanks.

---

### Post by ssalman on 2006-10-17
Bump...

---

### Post by ssalman on 2006-11-02
I did an Edgy fresh install and confirmed that this is still an issue in Edgy.

What's more interesting, I noticed that removing the wireless PCMIA card and reinserting it will resolve the problem and I will have a solid connection.

This sound like something is starting before it should during boot and preventing the connection to be established, and when I reestablish the network after boot have finished (by restarting the network or reinserting my card) it will run correctly... any ideas? ](*,)

Thanks

---

