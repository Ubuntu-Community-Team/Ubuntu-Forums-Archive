---
title: "Can't DHCP with Netgear wg311v3"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by Mutant on 2008-01-05
Hi,

I'm trying to get a Netgear wg311v3 PCI card to connect to my router. I've followed the instructions at:

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

I've successfully installed ndiswrapper, and can scan and find my router, however I can't get an IP address via DHCP:

```
$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:14:6c:c4:e2:95
Sending on   LPF/wlan0/00:14:6c:c4:e2:95
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory
```

Assigning a static IP address doesn't seem to help either. (The card works fine if I boot into WinXP).

My /etc/network/interfaces:

```
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-key s:mywirelesskey
wireless-essid MyRouter

auto wlan0
iface eth0 inet static
address 192.168.7.2
netmask 255.255.255.0

auto eth0
```

Output of ndiswrapper -l

```

mrv8335 : driver installed
        device (11AB:1FAA) present
```

iwconfig output:

```


wlan0     IEEE 802.11g  ESSID:off/any   
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Anyone have any ideas?

Thanks.

---

### Post by Predator[23rd] on 2008-01-05
your eth0 card has a static configuration ... is your router running a DHCP server at all?

can you correct your */etc/network/interfaces* entries a bit to be:

[I]auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-key s:mywirelesskey
wireless-essid MyRouter

auto eht0
iface eth0 inet static
address 192.168.7.2
netmask 255.255.255.0
[/I]

---

### Post by Mutant on 2008-01-05
My eth0 is not connected to the router, it's connected to a crossover cable to my other PC. DHCP is on on the wireless router and works for both my boxes under Windows (and the other 3-4 boxes connected to it). It just doesn't work under Ubuntu.

---

### Post by Predator[23rd] on 2008-01-05
is the network card working  with manual ip assignment?

---

### Post by Dngrsone on 2008-01-05
Are you running WEP Shared?

If so, then try this:

```
ifconfig wlan0 up
iwpriv wlan0 authmode 2
dhclient wlan0

```

Of course, you should be doing this as root or prefixing these commands with sudo.

---

### Post by Mutant on 2008-01-05
> **'Predator[23rd] said:**
> is the network card working  with manual ip assignment?

Yes, my wired network card appears to work (at least I can ping my other box, I haven't tried anything more than that yet). My wireless card doesn't work if I assign a static IP address though (that could be the router though).

> Are you running WEP Shared?

If so, then try this:

Think it's running WEP Open (the router from my ISP is fairly locked down with these settings unfortunately).

Trying to run iwpriv with authmode gives "Invalid command : authmode".

I have a sneaking suspicion that the problem is to do with the WEP key not getting recognised by the router, although not sure how I can verify that.

---

### Post by Predator[23rd] on 2008-01-05
> **Mutant said:**
> Y... at least I can ping my other box, I haven't tried anything more than that yet...

How can you ping another box without a prober configured network card???

---

### Post by Mutant on 2008-01-05
> **'Predator[23rd] said:**
> How can you ping another box without a prober configured network card???

There are two adaptors on the box, one wired, one wireless. The wired one is working fine, and is connected via crossover cable to my other PC. The wireless one is the one I'm having problems with.

---

### Post by Mutant on 2008-01-05
Well, I ended up swapping the wireless card out of my other PC, which is a bcm43xx based one, and it works perfectly.

I guess the wg311v3 is just not well supported.

Thanks for your help anyway.

---

