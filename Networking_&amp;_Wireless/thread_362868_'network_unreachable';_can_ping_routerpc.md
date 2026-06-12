---
title: "'network unreachable'; can ping router/pc"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by Naubra on 2007-02-16
ok here we go lets see if i can go w/o forgetting something

using an onboard nic on dell latitude c510 (lspci | grep ontroller shows 3com corp 3c905c-tx/tx-m [tornado] (rev 78))

when i specify an ip/dns/gateway/etcetera, i can ping my router, another pc, localhost, but nothing outside the router/local network.  however, sudo ifdown eth0 gets "ifdown: interface eth0 not configured", and sudo ifup eth0 / networking restart returns "SIOCADDRT: Network is unreachable Failed to bring up eth0"

when i use dhcp, i dont get either.

#'s in front of everything in /etc/network/interfaces, except:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.24
netmask 255.255.255.0
network 192.168.1.1 (router ip)
gateway xxxxxxxxxx
```

ifconfig:
```

eth0
Link encap:Ethernet  HWaddr 00:06:6b:e0:e6;13
inet addr:192.168.1.24  Bcast 192.168.1.255  Mask: 255.255.255.0
inet6 addr: fe80::206:5bff:fee0:e613/64 scope:link
up broadcast running multicast mtu:1500 metric:1
rx packets:1652 errors: 0 dropped:0 overruns:1 frame:0
txpackets:184 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
rx xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
interrupt: 11 base address:0x6c00

lo

link encap:localloopback
inetaddr:127.0.0.1 mask:255.0.0.0
inet6addr::1/128 scope:host
xxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxx
```


and to recap: static gives eth0 errors on 'ifup/down', but allows to ping router, and pc on network.  dhcp reports no errors on 'ifup/down', but doesnt allow me to ping.

any suggestions? soon as i tackle this, i can move on to ndiswrapper and getting my wireless pcmcia card to work.

thanks in advance!

---

### Post by Naubra on 2007-02-16
also: any pings outbound to ip's out of my network result in 'connect: Network is unreachable'

---

### Post by Naubra on 2007-02-16
might i mention that i can also access my router's web-based config in firefox

---

### Post by apjone on 2007-02-16
Change your gateway to the routers ip. And might be worth adding your routers DNS's into /etc/resolv.conf

---

### Post by Naubra on 2007-02-16
thank you sir, that fixed it!

oops on posting external ip. 

now to get this wireless working...

---

### Post by apjone on 2007-02-16
Sorry , I wont be much help with wireless.

---

