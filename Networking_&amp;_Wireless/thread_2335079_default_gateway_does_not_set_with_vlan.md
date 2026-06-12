---
title: "default gateway does not set with vlan"
date: 2016-08-25
forum: Networking &amp; Wireless
---

### Post by alexhemp on 2016-08-25
I've got ubuntu 16.04.1 server with two interfaces, each of them connected to different member of switch stack.

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eno1
iface eno1 inet manual
    bond-master bond0

auto eno2
iface eno2 inet manual
    bond-master bond0

auto bond0
iface bond0 inet manual
    bond-slaves eno1 eno2
    bond-mode 802.3ad
    bond-miimon 100
    bond-lacp-rate 1

auto vlan2
iface vlan2 inet static
    vlan_raw_device bond0
    address 192.168.0.10
    netmask 255.255.255.0
    gateway 192.168.0.1
    dns-nameservers 192.168.0.1 192.168.0.2
    dns-search local


```

After reboot I expect 192.168.0.1 as default gw in routing table but it's not

```

root@ubuntu:/# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0   0.0.0.0         255.255.255.0   U         0 0          0 vlan2

```

After executing  "route add default gw 192.168.0.1" everything works fine

I've temporary solved the problem by adding this command to /etc/rc.local but it should work as expected. Same config on 14.04.04 works fine.

---

### Post by dwa-p on 2016-12-01
Bump.

I have the same issue with 16.04 ... are we doing s'thing wrong ?

thx

---

### Post by andriy-tovstik on 2016-12-01
hi! the same issue..

---

