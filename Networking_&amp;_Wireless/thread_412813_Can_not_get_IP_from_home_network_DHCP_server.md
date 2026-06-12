---
title: "Can not get IP from home network DHCP server"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by ToohTaah on 2007-04-18
Hi,

I am using Netgear WG311T wireless card I bought 2 days ago (lspci gives me "05:06.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)". I could get it up and connect to my home network (with WEP key) before. The commands I used to get it connected were;

```

sudo killall dhclient3
sudo ifconfig ath0 down
sudo iwconfig ath0 essid mynetwork mode managed key "mykey"
sudo dhclient3 ath0

```

However, last night, I played around with it and tried to connect to a wireless network I scanned and found. Obviously, that network doesn't have a key. Then, I wanted to switch back to connect to my home network, but I could not obtain IP from DHCP. What I got was;

```

There is already a pid file /var/run/dhclient.pid with pid 14185
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:6c:89:23:0b
Sending on   LPF/ath0/00:14:6c:89:23:0b
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
Trying recorded lease 192.168.2.113
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

Trying recorded lease 192.168.1.124
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.071/1.071/1.071/0.000 ms
bound: renewal in 9938 seconds.

```

It seems that the wireless card can connect to the router from the ping command output, but I have found that it is because I also connected a cable to my ethernet port.

I also tried to route an ssh server to the wireless adapter using command 

```

sudo route add -net x.x.x.x netmask 255.255.255.255 ath0

```

Then, I tried to connect it and got this message.

```
ssh: connect to host x.x.x.x port 22: No route to host
```

I believe the problem is that I could not get IP from DHCP server. Any solution?

Actually, I also tried to assign the IP to the wireless card using the command

```
sudo ifconfig ath0 192.168.1.77 netmask 255.255.255.0
```

I could see that ath0 has the IP I assigned, but I could not get it connect to the router still.

P.S. I could go back, connet and get IP from the wireless network of the house near to me without any problem.

P.S.2 I prefer not to start the wireless card automatically since I dont use it all the time.

---

### Post by ToohTaah on 2007-04-18
anyone?

---

### Post by SuperOmegaSlack on 2007-04-18
did you try to disable, then enable your card?  or try power-cycling your router?  Not much, but I hope it helps.

---

### Post by ToohTaah on 2007-04-18
How could I disable my card?

---

### Post by ToohTaah on 2007-04-18
I, finally, got it to work by adding the access point mac address to the iwconfig command.

```
sudo killall dhclient3
sudo ifconfig ath0 down
sudo iwconfig ath0 essid mynetwork mode managed key "mykey" ap "mac address of the ap"
sudo dhclient3 ath0
```

---

