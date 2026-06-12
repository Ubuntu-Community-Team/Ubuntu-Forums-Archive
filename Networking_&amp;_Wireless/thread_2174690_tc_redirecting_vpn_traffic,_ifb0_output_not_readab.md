---
title: "tc redirecting vpn traffic, ifb0 output not readable?"
date: 2013-09-15
forum: Networking &amp; Wireless
---

### Post by james47 on 2013-09-15
hi, 

when i use these commands to redirect the output from tun0 to ifb0: 

```

 dev=tun0; indev=ifb0; 
tc qdisc add dev $dev handle ffff: ingress 
tc filter add dev $dev parent ffff: protocol ip prio 1 u32 match u32 0 0  action \ 
mirred egress redirect dev $indev 

```

i get this tcpdump output: 
```

tcpdump -i ifb0 
tcpdump: WARNING: ifb0: no IPv4 address assigned 

listening on ifb0, link-type EN10MB (Ethernet), capture size 65535 bytes 
22:44:38.333033 00:00:40:01:43:58 (oui Unknown) > 45:00:00:54:23:22 (oui  Unknown), ethertype Unknown (0x0a08), length 84: 
    0x0000:  000a 0a08 0016 0000 2e57 39db 0009 361c .........W9...6. 
    0x0010:  3652 3c53 0400 0809 0a0b 0c0d 0e0f 1011 6R<S............ 
    0x0020:  1213 1415 1617 1819 1a1b 1c1d 1e1f 2021 ...............! 
    0x0030:  2223 2425 2627 2829 2a2b 2c2d 2e2f 3031 "#$%&'()*+,-./01 
    0x0040:  3233 3435 3637                           234567 
22:44:39.333253 00:00:40:01:43:57 (oui Unknown) > 45:00:00:54:23:23 (oui  Unknown), ethertype Unknown (0x0a08), length 84: 
    0x0000:  000a 0a08 0016 0000 3e52 39db 000a 371c ........>R9...7. 
    0x0010:  3652 2b57 0400 0809 0a0b 0c0d 0e0f 1011 6R+W............ 
    0x0020:  1213 1415 1617 1819 1a1b 1c1d 1e1f 2021 ...............! 
    0x0030:  2223 2425 2627 2829 2a2b 2c2d 2e2f 3031 "#$%&'()*+,-./01 
    0x0040:  3233 3435 3637                           234567 

```
why dont i get the icmp packets that went into the openvpn tunnel? 
and what do i get instead? 

the target is to manage all incoming traffic, but if use eth0 (the real  physical device) as root 
all that goes over the vpn connection is already encrypted and  encapsulated by openvpn. 
so its all one big blob with dst port 1194. 

is there a better way to manage the traffic that goes to the internet  and the one that goes trough a vpn at one bottleneck?

---

### Post by james47 on 2013-09-20
should have checkd what ping packets look like on the receiving side, i was expecting a tc filter that matches small packets to hit it and be redirected in a qdisc. since that qdisc never got any packets i assumed that they never reached the machine...i was wrong

---

