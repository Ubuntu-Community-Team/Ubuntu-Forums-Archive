---
title: "Feisty: Unable to wake DHCP server of access point (WLAN)"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by userthebuntu on 2008-02-09
Hi everyone,

I'm using a D-LINK DWL-G122 with the RA73 driver to connect to my neighbor's wireless LAN access point...it's a local provider's access point at a hotel so it's all good.

Anyways, when connecting to the access point at a decent hour, say noonish, when someone else might have already connected to the access point I get a DHCPOFFER right away and have my IP assigned.

However when trying to obtain an IP from the DHCP server at a rather indecent hour..say early morning...that is when I might be the first person trying to do so in a couple of hours I am not able to get a DHCPOFFER no matter how hard and often I try.

If however I use my woman's windows xp computer to connect to that very same access point the windows computer gets an IP right away. Also after the windows computer has obtained its IP I can do so also with my kubuntu box.

Thus my theory goes as follows: I am somehow not able to wake up that DHCP server with my box.


Here's what happens when I'm unable to get an IP:

```
sudo ifdown wlan0

sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:11:14:bf:52
Sending on   LPF/wlan0/00:1b:11:14:bf:52
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

This is what I get when I'm able to obtain an IP:

```
sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:11:14:bf:52
Sending on   LPF/wlan0/00:1b:11:14:bf:52
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPOFFER from x.x.x.x
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from x.x.x.x
bound to x.x.x.x -- renewal in 74 seconds.

```


Also when using pump it won't work:

```
sudo pump -i wlan0

```

I then get a message saying something like "operation failed" after some time.


Also I would like to point out that while being unable to obtain an IP address I can still find the access point using iwlist or kismet.


Does anyone have an idea please?

I'd highly appreciate it!

---

### Post by userthebuntu on 2008-02-10
Anyone please?

---

### Post by userthebuntu on 2008-02-12
Please guys...what's the difference between the XP DHCP client and the ubuntu one (dhcp3-client version 3.0.4-12ubuntu and/or pump version 0.8.24-2) that makes the ubuntu clients unable to wake up an access point / DHCP server?

---

