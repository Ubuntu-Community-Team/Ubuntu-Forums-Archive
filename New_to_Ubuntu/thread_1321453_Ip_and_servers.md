---
title: "Ip and servers"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by TironN on 2009-11-10
Hey guys what the way in command line to bring up your network info. I'm trying to set up my server as static.

Thanks

---

### Post by Kadajski on 2009-11-10
in terminal type ```
ifconfig
```

---

### Post by albandy on 2009-11-10
you should edit /etc/network/interfaces with your desired configuration and /etc/resolv.conf with your dns servers

For example:

/etc/network/interfaces file:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 172.16.194.1
netmask 255.255.240.0
gateway 172.16.192.1
network 172.16.194.0
broadcast 172.16.207.255


/etc/resolv.conf file:

domain mydomain.loc
search mydomain.loc
nameserver 195.235.113.3
nameserver 195.235.96.90
nameserver 195.235.53.3

---

### Post by TironN on 2009-11-10
what is my gateway? ifconfig doesn't say

---

### Post by albandy on 2009-11-10
route -n

---

### Post by TironN on 2009-11-10
And what do i do for DNS settings?

---

### Post by alphacrucis2 on 2009-11-10
> **albandy said:**
> route -n

Just to clarify, your default gateway is the address listed on the line that has a destinition of 0.0.0.0 and a subnet mask of 0.0.0.0

eg:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.1.0        0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         [COLOR="Red"]10.1.1.1[/COLOR]        0.0.0.0         UG    0      0        0 wlan0

---

### Post by albandy on 2009-11-10
after reboot with your new ip configuration, set /etc/resolv.conf file with your dns settings.

---

### Post by TironN on 2009-11-10
yeah but where can i get my dns settings? what command?

---

### Post by albandy on 2009-11-10
cat /etc/resolv.conf

---

### Post by TironN on 2009-11-10
Ok so I've set up all that and a hostname.

But when I try running "hostname -f" i get lookup failure. Is this due to a failure on my behalf?

Nevermind! I fixed it all and its going fine. Thanks guys!

---

