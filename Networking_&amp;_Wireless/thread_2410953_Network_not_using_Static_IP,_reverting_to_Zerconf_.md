---
title: "Network not using Static IP, reverting to Zerconf - 16.04"
date: 2019-01-22
forum: Networking &amp; Wireless
---

### Post by lunarsurface on 2019-01-22
I have a server running Ubuntu 16.04 (16.04.5) it's on a vmware esxi vm, but all the other servers are working fine

When it boots it has a ZEROCONF 169.254... address. If I do a "sudo systemctl status networking.service" the network will come back up for about a minute, then go down again. ifconfig will still show the 10.1.1.120 address, however the end of "/var/log/syslog" has:

```

Jan 22 12:55:17 HOSTNAME connmand[1051]: ens160 {add} address 169.254.xx.xxx/16 label ens160 family 2
Jan 22 12:55:17 HOSTNAME connmand[1051]: ens160 {add} route 169.254.0.0 gw 0.0.0.0 scope 253 <LINK>

```

I can't use the sever as the network keeps dropping out. Any help would be great. Thank you

Here is /etc/network/interfaces

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto ens160
iface ens160 inet static
        address 10.1.1.120
        netmask 255.255.255.0
        gateway 10.1.1.1
        broadcast 10.1.1.255
        dns-nameservers 10.1.1.1 8.8.8.8
        dns-search ##### MY DOMAIN ####

```

---

### Post by lunarsurface on 2019-01-22
I had installed lxqt as some software needed a gui. Removing LXQT and the required packages fixed this problem, but I may need the gui again. Any idea what package would be causing this problem?

---

