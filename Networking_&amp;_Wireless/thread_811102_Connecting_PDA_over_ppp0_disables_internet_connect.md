---
title: "Connecting PDA over ppp0 disables internet connection vie eth0"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by jeroenvrp on 2008-05-28
Hello,

I have a Ipaq. It makes the connection with USB over ppp0. All works fine, except:

When I make connection to ppp0, the PDA is connected, but there is no internet connection anymore (eth0), When I disconnect ppp0 (unplugging the USB cable), internet is back to normal.

I read something about network-manager setting ppp0 as default and to ignore this device by network-manager I had to set this line in /etc/network/interfaces:
```
iface ppp0 inet dhcp
```

I did a /etc/init.d/networking restart, but still the same problem. My whole /etc/network/interfaces is:
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface ppp0 inet dhcp

iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.254

auto eth0

```

I also restarted my desktop to be sure for 100%.

What am I doing wrong?

---

### Post by jeroenvrp on 2008-06-01
I did some further investigation and I think it has to do with routing. When ppp0 is not active I have this as route:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         speedtouch.lan  0.0.0.0         UG    100    0        0 eth0

When I connect the iPaq and run synce-serial-start I have this route:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.131.201 *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.131.201 0.0.0.0         UG    0      0        0 ppp0
default         speedtouch.lan  0.0.0.0         UG    100    0        0 eth0

When I do a ifconfig, ppp0 says:

ppp0      Link encap:Point-to-Point Protocol
          inet addr:192.168.131.102  P-t-P:192.168.131.201  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:2358 (2.3 KB)  TX bytes:34575 (33.7 KB)

..and eth0 says (although when the device is unplugged it is the same):

eth0      Link encap:Ethernet  HWaddr 00:0c:6e:c1:eb:38
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fec1:eb38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5237797 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6456853 errors:1 dropped:0 overruns:1 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2264957027 (2.1 GB)  TX bytes:998430139 (952.1 MB)
          Interrupt:17 Base address:0xe000



Please help?

---

### Post by lincoln32 on 2008-07-07
you got farther than i did. good luck!!!!

---

