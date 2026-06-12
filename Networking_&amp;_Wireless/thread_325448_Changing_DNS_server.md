---
title: "Changing DNS server"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by tsmets on 2006-12-25
My network is configured as what follows :

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.5.100
        netmask 255.255.255.0
        network 192.168.5.0
        broadcast 192.168.5.255
        gateway 192.168.5.254
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.5.254
```


I believe that to allow other / new dns servers, I just need to add to the /etc/resolv.conf, the following lines :
```
nameserver w00.x00.y00.z00
nameserver w11.x11.y11.z11

```
Is this correct ...  :-k  ?
Tx,
\T,

---

### Post by Stemp on 2006-12-25
In your your /etc/resolv.conf you must have must the real adress of your dns.
If it's not done automatically try the OpenDsn :
```
nameserver 208.67.222.222
nameserver 208.67.220.220

```

---

