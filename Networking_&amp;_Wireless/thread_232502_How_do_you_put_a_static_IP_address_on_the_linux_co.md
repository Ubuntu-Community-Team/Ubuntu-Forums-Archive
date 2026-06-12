---
title: "How do you put a static IP address on the linux computer?"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by boom2k1 on 2006-08-08
Does anyone know how I can put a static ip address on my linux computer? It is connected to the wireless router through a wireless network card. Thanks!

---

### Post by wieman01 on 2006-08-08
Is it already connected? What are your router's settings?

Please post the content of this file: 
> /etc/network/interfaces
That'll help.

In Gnome there is an applet you can use to configure your network. I think it's called "Networking" or similar. There you can change the settings according to your needs.

---

### Post by boom2k1 on 2006-08-09
My router setting is:

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp




iface ath0 inet dhcp
wireless-essid charchar



I am not sure how to configure that in the tool!

---

### Post by boom2k1 on 2006-08-09
i am trying to change from Dhcp to static ip.

how do I know what my gateway is?  thanks!

---

### Post by wieman01 on 2006-08-09
I am assuming that "ath0" is your wireless adapter. With static IPs this is what it should look like:
> iface ath0 inet static
wireless-essid <your_essid>
address 192.168.168.40
netmask 255.255.255.0
network 192.168.168.0
broadcast 192.168.168.255
gateway 192.168.168.230
dns-nameservers 192.168.168.230

You must change the settings and IP addresses according to your own network setup (or use my example for testing). Before you do so, you have to enable static IPs in your router otherwise your wireless adapter won't be able to establish a connection (static IP & DHCP are not compatible).

Find out about your gateway through "ifconfig" or "iwconfig" (terminal).

---

### Post by boom2k1 on 2006-08-09
Thanks! i think i got it :) thanks!

---

