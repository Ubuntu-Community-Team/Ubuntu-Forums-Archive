---
title: "Virtualbox host IP address change doesn't work."
date: 2009-03-05
forum: New to Ubuntu
---

### Post by Doom750 on 2009-03-05
Hello,

I did do a search about this, but no one seems to be having the same problem I am.  My configuration for /etc/network/interfaces is below.  I am using 8.0.4 Hardy, and Virtual box 2.0.2.  I know the newer version of virtualbox works easier with host networking, but I am not in a situation where I can upgrade virtualbox.

I originally had the below configuration working, but when I tried to change the IP address in the interfaces file and reboot, there was no more networking.  Please help.


```
auto lo0
iface lo0 inet loopback

auto eth0
iface eth0 inet manual


auto tap0
iface tap0 inet manual
tunctl_user squid
uml_proxy_arp 192.168.1.2
uml_proxy_ether eth0


auto br0
iface br0 inet static
address 192.168.1.2
network 192.168.1.0
netmask 255.255.255.0
gateway 192.168.1.1
bridge_ports eth0 tap0
bridge_maxwait 0
```

---

### Post by Doom750 on 2009-03-05
Ok, maybe I posted this in the wrong section...Should it be moved to a "Networking" section?

---

