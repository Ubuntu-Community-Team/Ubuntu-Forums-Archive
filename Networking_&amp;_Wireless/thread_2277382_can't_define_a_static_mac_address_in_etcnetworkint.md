---
title: "can't define a static mac address in /etc/network/interfaces"
date: 2015-05-08
forum: Networking &amp; Wireless
---

### Post by eyaln on 2015-05-08
Hi, 

can't define a static mac address in /etc/network/interfaces
this was done in conjunction with a dummy interface:

my  /etc/modprobe.d/dummy.conf file:

sudo /sbin/modprobe dummy numdummies=3
sudo /sbin/ip link set name eth10 dev dummy0
sudo /sbin/ifconfig eth10 hw ether 00:10:10:ff:ff:ff

my /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)


auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp


auto eth10
iface eth10 inet static
address 192.168.1.18
netmask  255.255.255.0

---

### Post by themaninthehat on 2015-05-09
Were you following some instructions from somewhere else to do this?

---

