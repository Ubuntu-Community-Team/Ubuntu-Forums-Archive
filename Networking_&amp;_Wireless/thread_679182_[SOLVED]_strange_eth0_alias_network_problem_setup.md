---
title: "[SOLVED] strange eth0 alias network problem setup"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by ph3ar on 2008-01-26
Hello, this is my /etc/network/interfaces

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
auto eth0:0
iface eth0:0 inet static
address 192.168.0.3
netmask 255.255.255.0
#broadcast 192.168.0.255
#network 192.168.0.0

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

The logical thing referring to this setup is that in every boot process i should have an aliased interface eth0:0 with the defined ip and the other interfaces to just take ip from dhcp right?
Ok this setup is not working on boot-up and moreover there is some strange behaviour on the kde desktop... something like my user settings  (desktop,icons,wallpaper...) cannot be loaded until i do manually restart the networking ```
/etc/init.d/networking restart
``` And then is working properly but  the aliased interface eth0:0 is up but sometimes disappears....

Any ideas?????????? :confused:

---

### Post by ph3ar on 2008-01-31
anyone????? ](*,)

---

### Post by ph3ar on 2008-03-04
Upgraded to gutsy 7.10 version and the problem solved.

---

