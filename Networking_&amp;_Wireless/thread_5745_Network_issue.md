---
title: "Network issue"
date: 2004-11-22
forum: Networking &amp; Wireless
---

### Post by gballard on 2004-11-22
When I initially installed Ubuntu...I told it to use my D-Link 650+ wireless as the default network connection.  That is all fine while I am using the laptop at home but when I got to the office this morning...I needed it to use the onboard network adapter at eth0.  During the boot sequence, it got to the point where it was bringing up the network interfaces.  It started spitting errors in relation to eth0...something about unable to set multicast or something along those lines.  It eventually booted up to the desktop and I logged in.  I opened a terminal and typed in ifconfig...it sees a network card at eth0 and gives the MAC address and even gives an IPv6 IP address...but no IPv4 address is listed.  Is this an instance where I need to setup a profile for home and a profile for work?  If so...how do I do that?....:(

---

### Post by p!=f on 2004-11-22
You might want to try following packages:
```

apt-cache show laptop-net netenv

```

---

### Post by gballard on 2004-11-22
What do those packages do exactly?

---

### Post by gballard on 2004-11-22
[QUOTE=gballard]What do those packages do exactly?[/QUOTE]
 OK...I figured out what happened. It sees the built-in wireless as eth0 and eth1 is actually my on-board ethernet card. I edited /etc/network/interfaces and made the changes where needed and then typed ifup eth1 and its working now...thanks for the input.

---

### Post by gballard on 2004-11-27
[QUOTE=gballard]OK...I figured out what happened. It sees the built-in wireless as eth0 and eth1 is actually my on-board ethernet card. I edited /etc/network/interfaces and made the changes where needed and then typed ifup eth1 and its working now...thanks for the input.[/QUOTE]
 what is the syntax for specifying a WEP key in the /etc/network/interfaces file? I had to reload my laptop and for some reason wlan0 wasn't able to be configured...what else would I need to specify in the interfaces?...wep key...essid....?

When I type ifup wlan0 i get the following....

root@gballardlap:/etc/network # ifup wlan0
Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0d:88:98:e8:8c
Sending on LPF/wlan0/00:0d:88:98:e8:8c
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I guess I could hardcode the IP eh?

---

### Post by gballard on 2004-11-28
[QUOTE=gballard]what is the syntax for specifying a WEP key in the /etc/network/interfaces file? I had to reload my laptop and for some reason wlan0 wasn't able to be configured...what else would I need to specify in the interfaces?...wep key...essid....?

When I type ifup wlan0 i get the following....

root@gballardlap:/etc/network # ifup wlan0
Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0d:88:98:e8:8c
Sending on LPF/wlan0/00:0d:88:98:e8:8c
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I guess I could hardcode the IP eh?[/QUOTE]
 well...I guess I must have typed in my WEP key wrong...I am re-installing again...and apparently it is case sensitive....detected the wireless access point and got an IP address right away this time...go figger eh?

---

