---
title: "yet another wireless card connected but no network"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by mirceacomanici on 2007-01-25
Hi, I'm new to Linux and I need some help. 
I'm running Ubuntu 6.10 (Edgy) (dual boot with Windows XP) on a Packard Bell Laptop. I have a wired ethernet connection (eth0 - which is working ok) and a wireless pcmcia card (Asus wl107g) which I managed to connect to my wireless router (US robotics USR 8054) following this instructions 

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#head-af86b211b480d43b791cd9b4e698f96638d6d25f](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#head-af86b211b480d43b791cd9b4e698f96638d6d25f)  

Now, the Network Monitor applet shows the wireless network connected and some existing traffic on this connection (ra0) but in Firefox I can't access the router. If I plug the cable in the wired interface (eth0) is working ok. When I remove it and remain only the wireless network again I have no router acces. The Wirless Card is working ok from Windows. On the router web interface I can see that the Asus card is connected to the router so I suspect that somehow Ubuntu don't know to use the wireless connection to acces the network.

My setup is as follows :
Router IP :192.168.123.254
DHCP Off (I tried swithing it On but to with same results)
WPA PSK 

Asus WL107g Wireless Card with ralink Ra2500 chipset
ra0
IP: 192.168.123.102

Rhine II wired NIC
eth0
IP:192.168.123.103

my /etc/network/interfaces contain is:

---------------------------------------------------

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.123.103
netmask 255.255.255.0
gateway 192.168.123.254

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto ra0
iface ra0 inet static
address 192.168.123.102
netmask 255.255.255.0
gateway 192.168.123.254
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "MiddleEarth"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="A1@rgus#"
pre-up ifconfig ra0 up

----------------------------------------------------------------

in System Administration Networking I set the DNS and Search Domains to 192.168.123.254
(eth0 is working ok)

Thanks in advance!

---

