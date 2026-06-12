---
title: "[SOLVED] dhclient"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by camellochapin on 2007-09-26
Hi,

I've been using linux for the last 18 months, nowadays running Ubuntu 7.04 on my laptop.  Having access to the internet was never a problem, The "DHCP" option in the Network-Settings GUI for the wired connection is activated, never changed it before.

For the last weeks, everytime I restart my computer sometimes I have no access to the internet and sometimes I do.... so I have to manually type ```
sudo dhclient
``` in order to get internet access whenever I don't have.

The content of my "/etc/network/interfaces" is:

```

auto lo
iface lo inet loopback


iface eth0 inet dhcp
address 192.168.0.34
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
iface eth1 inet dhcp
wireless-essid FreeDomServer
wireless-channel 9
wireless-mode Managed

pre-up ifconfig eth1 up
pre-up iwpriv eth1 auth 3
pre-up iwpriv eth1 enc 3
pre-up iwconfig eth1 channel 9
pre-up iwconfig eth1 essid FreeDomServer
pre-up iwpriv eth1 wpapsk xxxxx
pre-up iwconfig eth1 essid FreeDomServer

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

```

The problem happens only with my wired connection "eth0"

Could any of you give me some help?  Thanks a lot!

---

### Post by Bachstelze on 2007-09-26
If the interface is DHCP, you mustn't mention address/netmask/gateway. Ditch those three lines :

```
address 192.168.0.34
netmask 255.255.255.0
gateway 192.168.0.1

```

---

### Post by camellochapin on 2007-09-26
Thanks a lot!

How come I didn't notice it before?!?!?!

Once I was doing some test back at home with fixed IP numer, net mask, gateway, etc... and I did it thru the network-settings GUI.... later on I switched back to DHCP... but it didn't delete that entry into that file!

anyway, thanks a lot!

---

