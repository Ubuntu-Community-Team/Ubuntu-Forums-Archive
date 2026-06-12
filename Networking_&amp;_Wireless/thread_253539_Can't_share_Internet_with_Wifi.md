---
title: "Can't share Internet with Wifi"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by der_kaiser on 2006-09-08
Hi everybody,
I've git 2 computers with Dapper installed on them. The first one is a desktop (PC1) connected to internet via ppp0 and has a Wifi PCI card. The second is a laptop (PC2) with a wifi integrated card. 
I want to share Internet using wifi.
My /etc/network/interfaces on PC1 looks like this : 
##########################################
# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.1
netmask 255.255.255.0
pre-up /sbin/iwpriv wlan0
wireless_mode Master
wireless_channel 9
wireless-essid Home

iface eth0 inet static
address 192.168.2.1
netmask 255.255.255.0

auto eth0
#####################################
And the one on PC2 looks like this : 
#####################################
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

auto ath0
iface ath0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
wireless_mode Managed
wireless-essid Home
######################################

The command iwlist ath0 scan on the laptop detects the network, but when I try to ping one of the computers, it fails on both senses.
I've desactivated all the firewalls, and the problem is still persistent.
Can any one help me on that?
Thank you!

---

### Post by der_kaiser on 2006-09-09
Really no idea?

---

### Post by der_kaiser on 2006-09-09
Really no idea?

---

