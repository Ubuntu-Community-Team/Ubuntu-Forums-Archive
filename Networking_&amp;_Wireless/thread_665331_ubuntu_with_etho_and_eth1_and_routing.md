---
title: "ubuntu with etho and eth1 and routing"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by giannirusso on 2008-01-12
Hello, I have two interfaces on ubuntu (eth0 and eth2) for working like router software (i have did it on the past with my old debian):
Here my configuration:
eth0: 192.168.1.215 connected to many pic win on the same range of address 192.168.1.x
eth1: 192.168.157.1 connected to dsl modem (address 192.168.157.100)
The problem is ( I had similar on my debian but I don't remeber the solution!) that I can surf on internet JUST from linux machine. Pc win won't connect to internet even if they can ping 192.168.1.215 and viceversa. I can exclude this is a dns problem,
This is my .../networking/interfaces
auto eth0
iface eth0 inet static
address 192.168.1.215
netnask 255.255.255.0
gateway 192.168.157.100 (modem private adress) [I tried with and without this line]
auto eth2
iface eth2 inet static
address 192.168.157.1
netnask 255.255.255.0
gateway 192.168.157.100 (modem private adress) [I tried with and without this line]
This is my route -n:
81.174.x.x         0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0       0.0.0.0         255.255.255.0      U      0      0        0 eth0
192.168.157.0   0.0.0.0         255.255.255.0     U      0      0        0 eth2
0.0.0.0                 0.0.0.0         0.0.0.0                   U      0      0        0 ppp0

I tried to type "route add default gw 192.168.157.100" but no luck.
I have not set any iptables rule. When I try with the default firewall-masq I can't either surf either ping pc win.
For connecting I type pon dsl-provider.

I need help....
Thanks
Gianni

---

### Post by amo-ej1 on 2008-01-12
have you enabled forwarding ? 

```

edb@Flying-Spaghetti-Monster:~$ cat /proc/sys/net/ipv4/ip_forward 
0

```

There should be a 1 there for ip forwarding to function to echo 1 > /proc/sys/net/ipv4/ip_forward should do the trick.

It can be made persistent by writing it /etc/sysctl.conf:

```

edb@Flying-Spaghetti-Monster:~$ cat /etc/sysctl.conf | grep forw
# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1
# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1

```

---

### Post by giannirusso on 2008-01-12
> **amo-ej1 said:**
> have you enabled forwarding ? 

```

edb@Flying-Spaghetti-Monster:~$ cat /proc/sys/net/ipv4/ip_forward 
0

```

There should be a 1 there for ip forwarding to function to echo 1 > /proc/sys/net/ipv4/ip_forward should do the trick.

[CODE]


Yes I tried it, but I wiill try again.
But I think this is a routing problem...

Thanks
Gianni

---

### Post by amo-ej1 on 2008-01-12
Well try to ping to a host on the internet or try a traceroute from the pc behind your router. Then use tcpdump on your router to see how far traffic flows.

---

### Post by amo-ej1 on 2008-01-12
Oh yeah, one thing that  doesn't seems to be clear at first sight. So your router has two ethernet ports and a ppp0 link. The ppp0 link is your default gateway from that box, so why would any traffic flow through 192.168.157.1 ?

---

### Post by giannirusso on 2008-01-12
> **amo-ej1 said:**
> Oh yeah, one thing that  doesn't seems to be clear at first sight. So your router has two ethernet ports and a ppp0 link. The ppp0 link is your default gateway from that box, so why would any traffic flow through 192.168.157.1 ?

Because pc win come with 192.168.1.x address and gateway 192.168.1.215 (eth0 address). 
They ping 192.168.1.215 but can't go out to internet. This is the BIG problem!

Thanks
Gianni

---

### Post by giannirusso on 2008-01-12
> **amo-ej1 said:**
> Well try to ping to a host on the internet or try a traceroute from the pc behind your router. Then use tcpdump on your router to see how far traffic flows.

This is a traceroute output from a machine behind the router (192.168.1.x):
# traceroute [www.google.com](www.google.com)
traceroute: unknow host [www.google.com](www.google.com)

And this is tcpdump on linux box:
20:04:05.074975 IP sidi-desktop.1026 > ug-in-f9.google.com.domain:  44545% [1au] A? [www.l.google.com](www.l.google.com). (45)
20:04:06.994131 IPX 00000000.00:50:ba:4f:03:5d.0452 > 00000000.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp 0142 'HLSERVER_0250_000000000050BA4F035D[|ipx 64]
20:04:07.084649 IP sidi-desktop.1026 > py-in-f9.google.com.domain:  2654 A? [www.l.google.com](www.l.google.com). (34)
20:04:09.094269 IP sidi-desktop.1026 > mg-in-f9.google.com.domain:  33433 A? [www.l.google.com](www.l.google.com). (34)

This lines are referred to some firewall? I don't know how I can start or stop may default /etc/ppp/firewall-masq.
And when I type iptables -L, no rules seems availables.
Thanks for any suggestions.
Gianni

---

### Post by giannirusso on 2008-01-15
It works now.
It was just a iptables problem.
(I don't think you are interested to my iptables rules because they are from some copy and paste of other working iptables found on the net!)
Thanks and regards all.

---

