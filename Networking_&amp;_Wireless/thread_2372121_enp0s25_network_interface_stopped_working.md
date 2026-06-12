---
title: "enp0s25 network interface stopped working"
date: 2017-09-21
forum: Networking &amp; Wireless
---

### Post by trambar18 on 2017-09-21
Hi,
i have a problem with my network interface. apparently it has stopped working and it is now giving me an error code.
when i run in ifconfig this is my result:

how do i get this device/ interface to work again?
 ```
[I]enp0s25: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 28:d2:44:04:3e:67  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf2500000-f2520000 [/I]
```
p.s. i have already tried the commands:
```
ifconfig enp0s25 down && ifconfig enp0s25 up
```
but that did not work.

---

