---
title: "do u think this is a bug?"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by mendingo84 on 2006-12-26
first of all, i must mention that i connect through pppoe.
here goes the fun part:

i configure the connection using "sudo pppoeconf". everything works perfectly till i boot. each time i boot, if i try "ifconfig" it gives me ppp0 but it WON'T WORK (of course, the connection is configured to start at boot time):
> 
ppp0      Link encap:Point-to-Point Protocol
          inet addr:xxxxxxxxx  P-t-P:xxxxxxxxxx Mask:xxxxxxxxxx
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:1204 (1.1 KiB)  TX bytes:1198 (1.1 KiB

if i restart the interface using "sudo /etc/init.d/networking restart" the ppp0 link WANISHES and, of course, no net connection. 
finally, to bring up the connection, i have to go through "sudo pon dsl-provider".
what i want, is for it to start at boot time, as it is configured to do so. i don't want to go through poff and pon each time i boot
here is the "/etc/network/interfaces" file:
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

  #  pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf 

this didn't happen on dapper. do u think it's an edgy bug? :-k

---

