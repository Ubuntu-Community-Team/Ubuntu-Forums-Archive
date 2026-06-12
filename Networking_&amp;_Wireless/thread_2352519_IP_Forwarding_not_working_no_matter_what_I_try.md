---
title: "IP Forwarding not working no matter what I try"
date: 2017-02-13
forum: Networking &amp; Wireless
---

### Post by vitaly512 on 2017-02-13
Hello guys,

I am having a weird problem where my Ubuntu 14.04server will not forward any packets.

The setup is:

```
vit@stop:~> lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:        14.04
Codename:       trusty
vit@stop:~> uname -a
Linux stop 4.4.0-59-generic #80~14.04.1-Ubuntu SMP Fri Jan 6 18:02:02 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
vit@stop:~> 

```

Packets coming from p1p1.172 should be forwarded out p1p1.171.

```
vit@stop:~> ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: p1p1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 90:e2:ba:d6:00:1c brd ff:ff:ff:ff:ff:ff
    inet6 fe80::92e2:baff:fed6:1c/64 scope link 
       valid_lft forever preferred_lft forever
3: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 70:4d:7b:b6:fe:05 brd ff:ff:ff:ff:ff:ff
    inet 192.0.2.44/27 brd 192.0.2.63 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::724d:7bff:feb6:fe05/64 scope link 
       valid_lft forever preferred_lft forever
4: p1p2: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 90:e2:ba:d6:00:1d brd ff:ff:ff:ff:ff:ff
5: p1p1.171@p1p1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 90:e2:ba:d6:00:1c brd ff:ff:ff:ff:ff:ff
    inet 192.0.2.174/30 brd 192.0.2.175 scope global p1p1.171
       valid_lft forever preferred_lft forever
    inet6 fe80::92e2:baff:fed6:1c/64 scope link 
       valid_lft forever preferred_lft forever
6: p1p1.172@p1p1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 90:e2:ba:d6:00:1c brd ff:ff:ff:ff:ff:ff
    inet 10.5.32.2/30 brd 10.5.32.3 scope global p1p1.172
       valid_lft forever preferred_lft forever
    inet6 fe80::92e2:baff:fed6:1c/64 scope link 
       valid_lft forever preferred_lft forever
7: p1p1.173@p1p1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 90:e2:ba:d6:00:1c brd ff:ff:ff:ff:ff:ff
    inet 10.5.32.6/30 brd 10.5.32.7 scope global p1p1.173
       valid_lft forever preferred_lft forever
    inet6 fe80::92e2:baff:fed6:1c/64 scope link 
       valid_lft forever preferred_lft forever
       
vit@stop:~> ip l
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: p1p1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether 90:e2:ba:d6:00:1c brd ff:ff:ff:ff:ff:ff
3: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 70:4d:7b:b6:fe:05 brd ff:ff:ff:ff:ff:ff
4: p1p2: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 90:e2:ba:d6:00:1d brd ff:ff:ff:ff:ff:ff
5: p1p1.171@p1p1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default qlen 1000
    link/ether 90:e2:ba:d6:00:1c brd ff:ff:ff:ff:ff:ff
6: p1p1.172@p1p1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default qlen 1000
    link/ether 90:e2:ba:d6:00:1c brd ff:ff:ff:ff:ff:ff
7: p1p1.173@p1p1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default qlen 1000
    link/ether 90:e2:ba:d6:00:1c brd ff:ff:ff:ff:ff:ff
```

```
vit@stop:~> ip route
default via 192.0.2.173 dev p1p1.171
10.5.32.0/30 dev p1p1.172  proto kernel  scope link  src 10.5.32.2
10.5.32.4/30 dev p1p1.173  proto kernel  scope link  src 10.5.32.6
192.0.2.32/27 dev eth0  proto kernel  scope link  src 192.0.2.44
192.0.2.172/30 dev p1p1.171  proto kernel  scope link  src 192.0.2.174

```

```
vit@stop:~> cat /proc/sys/net/ipv4/ip_forward
1
```

iptables is clean:
```
$IPT -P INPUT ACCEPT
$IPT -P FORWARD ACCEPT
$IPT -P OUTPUT ACCEPT
$IPT -t nat -F
$IPT -t nat -X
$IPT -t mangle -F
$IPT -t mangle -X
$IPT -t raw -F
$IPT -t raw -X
$IPT -F
$IPT -X
```

Then:

```
iptables -t raw -A PREROUTING -d 192.0.2.38 -j TRACE
```

I am pinging a host with the ip address of 192.0.2.38 through p1p1.172

produces:

```
Feb 13 15:33:24 stop kernel: [873912.017189] TRACE: raw:PREROUTING:policy:2 IN=p1p1.172 OUT= MAC=90:e2:ba:d6:00:1c:4c:5e:0c:14:17:88:08:00 SRC=192.0.2.154 DST=192.0.2.38 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=30417 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=571 
Feb 13 15:33:24 stop kernel: [873912.017226] TRACE: mangle:PREROUTING:policy:1 IN=p1p1.172 OUT= MAC=90:e2:ba:d6:00:1c:4c:5e:0c:14:17:88:08:00 SRC=192.0.2.154 DST=192.0.2.38 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=30417 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=571 
Feb 13 15:33:24 stop kernel: [873912.017241] TRACE: nat:PREROUTING:policy:1 IN=p1p1.172 OUT= MAC=90:e2:ba:d6:00:1c:4c:5e:0c:14:17:88:08:00 SRC=192.0.2.154 DST=192.0.2.38 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=30417 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=571 

```

And that's it. The packet does not even get in the FORWARD chain and no counters in the FORWARD chain are increasing.

I am completely lost here. I don't know why Ubuntu refuses to forward packets.

Anyone have any idea what might be going on?

---

### Post by SeijiSensei on 2017-02-13
Are you sure the receiving host, 192.0.2.38, has a route to send the packets back to their origin?  Is it sending them to its default gateway?  Does that gateway know what to do with traffic for the originating host?  Often I've found when routing doesn't seem to work, it's a problem with the host on the other end of the connection.

---

### Post by vitaly512 on 2017-02-13
SeijiSensei, thank you for replying. The problem is, the packet to host 192.0.2.38 (or any other host for that matter) disappears inside this Ubuntu box on its way **there**. It does not get to reach the destination host in the first place. The scheme is like this:

Path: 1) Origin host (192.0.2.154) -> 2) Core router (192.0.2.173) -> 3) (IN p1p1.172) Ubuntu box (192.0.2.174) OUT (p1p1.171) -> 4) Core router (192.0.2.173) -> 5) Destination host (192.0.2.38).

Step 3 is where the packet disappears.

---

### Post by SeijiSensei on 2017-02-13
Well, I have no idea what "p1p1.172" is?  Is it an interface? A hostname? Does it have an IP address?  I'm afraid I can only help with IP routing.

---

### Post by vitaly512 on 2017-02-13
> **SeijiSensei said:**
> Well, I have no idea what "p1p1.172" is?  Is it an interface? A hostname? Does it have an IP address?  I'm afraid I can only help with IP routing.

p1p1 is an Intel NIC

p1p1.172 is a VLAN interface on the Intel NIC (vlan tag 172).

As I stated in the original post it does have an IP address:

> 
6: p1p1.172@p1p1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 90:e2:ba:d6:00:1c brd ff:ff:ff:ff:ff:ff
    inet 10.5.32.2/30 brd 10.5.32.3 scope global p1p1.172
       valid_lft forever preferred_lft forever
    inet6 fe80::92e2:baff:fed6:1c/64 scope link 
       valid_lft forever preferred_lft forever

It comes into Ubuntu via this interface, it's fine. But then the packet just disappears without trace before it hits the FORWARD chain in iptables.

---

