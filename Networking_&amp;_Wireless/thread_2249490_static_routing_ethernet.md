---
title: "static routing ethernet"
date: 2014-10-22
forum: Networking &amp; Wireless
---

### Post by uPatrick on 2014-10-22
I have a problem route my ethernet interface on ubuntun.

my configuration:
internet <=> router <=> laptop wlan0 ---- laptop eth0 <=> pc eth0

laptop eth0 and pc eth0 are set static address for 192.168.30.101 and 192.168.30.102
laptop wlan0 has ip from router (dhcp) 192.168.20.105.

how could i do a static routing to get pc access to internet ?

Thank

---

### Post by uPatrick on 2014-10-22
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


auto eth0
allow-hotplug eth0
iface eth0 inet static
address 192.168.30.101
geteway 192.168.30.1
netmask 255.255.255.0
dns-nameservers 192.168.20.1 8.8.8.8 8.8.4.4


#auto wlan0
#iface wlan0 inet dhcp

#not working if enable
#up route add -net 192.168.30.0/16 netmask 255.255.255.0 gw 192.168.20.1 dev eth0
#up route add -net 192.168.20.0/16 gw 192.168.30.1 dev wlan0

---

### Post by weatherman2 on 2014-10-22
Have you tried doing it with the Gui?

[http://askubuntu.com/questions/169473/sharing-connection-to-other-pcs-via-wired-ethernet](http://askubuntu.com/questions/169473/sharing-connection-to-other-pcs-via-wired-ethernet)

Ubuntu can even run a DHCP server on the eth0 port as I recall, if you want it to.  You may need a switch (or router) between the laptop and the desktop or a crossover ethernet cable, unless one network interface can automatically do that to make an ad hoc network...

---

### Post by uPatrick on 2014-10-22
does it work if i route traffic from wlam0 to laptop eth0 ?
any cmd line that i can use ?

---

### Post by weatherman2 on 2014-10-23
It should work that way, too, sure.  Just choose wlan0 as the one you share.  No, I don't know how to do it via command line.

---

