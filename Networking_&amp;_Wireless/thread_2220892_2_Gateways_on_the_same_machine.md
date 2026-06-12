---
title: "2 Gateways on the same machine"
date: 2014-04-29
forum: Networking &amp; Wireless
---

### Post by kamzata2 on 2014-04-29
I've a server web with 2 ethernet cards and I have 2 different gateways. How can I set server so that it answer to the requests coming from a gateway with the same gateway?

---

### Post by drink1297 on 2014-05-02
Do you have IP rules and a second routing table in use for one of the gateways? You should just be able to adjust the IProuting tables

---

### Post by SeijiSensei on 2014-05-02
You need to use the "[Advanced Routing]("http://www.lartc.org/")" features in Linux.  I needed to do this once a while back when a client was transitioning from one ISP to another.  You need to create an entry in /etc/iproute2/rt_tables that defines a symbolic name for your new route.  Then you can use the "ip route" and "ip rule" commands to tell your system when to use that route.

Suppose my server has 10.2.2.2 on a second interface (eth2 below) connected to 10.2.2.1 as a gateway.  In /etc/iproute2/rt_tables I defined a new route numbered 2 and gave it the name "newisp".
```
2 newisp
```
I then used these rules to tell the system to use the "newisp" route to handle packets arriving on 10.2.2.2.
```
/sbin/ip route add default via 10.2.2.1 dev eth2 table newisp
/sbin/ip rule add from 10.2.2.2 lookup newisp prio 1000
```
The first command attaches the defined route to "newisp." The second tells the kernel to apply that rule when sending traffic from 10.2.2.2.  It also assigns that rule a high priority so it will override any alternatives.  That gave me two gateways, one for traffic sent in reply to packets arriving on 10.2.2.2, and the original default gateway for all other traffic.  With this arrangement the machine could, say, host a web page on 10.2.2.2, while sending all other traffic out a different route.

---

### Post by KaMZaTa on 2014-05-04
> **drink1297 said:**
> Do you have IP rules and a second routing table in use for one of the gateways? You should just be able to adjust the IProuting tables

> **SeijiSensei said:**
> You need to use the "[Advanced Routing]("http://www.lartc.org/")" features in Linux.  I needed to do this once a while back when a client was transitioning from one ISP to another.  You need to create an entry in /etc/iproute2/rt_tables that defines a symbolic name for your new route.  Then you can use the "ip route" and "ip rule" commands to tell your system when to use that route.

Suppose my server has 10.2.2.2 on a second interface (eth2 below) connected to 10.2.2.1 as a gateway.  In /etc/iproute2/rt_tables I defined a new route numbered 2 and gave it the name "newisp".
```
2 newisp
```
I then used these rules to tell the system to use the "newisp" route to handle packets arriving on 10.2.2.2.
```
/sbin/ip route add default via 10.2.2.1 dev eth2 table newisp
/sbin/ip rule add from 10.2.2.2 lookup newisp prio 1000
```
The first command attaches the defined route to "newisp." The second tells the kernel to apply that rule when sending traffic from 10.2.2.2.  It also assigns that rule a high priority so it will override any alternatives.  That gave me two gateways, one for traffic sent in reply to packets arriving on 10.2.2.2, and the original default gateway for all other traffic.  With this arrangement the machine could, say, host a web page on 10.2.2.2, while sending all other traffic out a different route.

Thank you for your answers. [This is what i read]("http://openvz.org/Source_based_routing"). So I have read too about "[Policy Based Routing]("http://en.wikipedia.org/wiki/Policy-based_routing")" and "[Source Routing]("http://en.wikipedia.org/wiki/Source_routing")" but I don't understand really the differences.

Anyway... this is what i've done without result:

```

root@server /# ifconfig
eth0      Link encap:Ethernet  HWaddr 22:2a:53:40:82:ac
          inet addr:192.168.10.52  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe78::202b:53ff:fe40:82ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2850 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6126899 (5.8 MiB)  TX bytes:83403 (81.4 KiB)

eth1      Link encap:Ethernet  HWaddr a2:3c:88:91:11:54
          inet addr:192.168.1.52  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a01c:99ff:fe82:1144/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:345731 (337.6 KiB)  TX bytes:16940 (16.5 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@server /# ping 192.168.10.1
PING 192.168.10.1 (192.168.10.1) 56(84) bytes of data.
64 bytes from 192.168.10.1: icmp_req=1 ttl=64 time=27.0 ms

root@server /# ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=255 time=6.84 ms

root@server /# ping 8.8.8.8
connect: Network is unreachable

root@server /# ip rule list
0:      from all lookup local
32766:  from all lookup main
32767:  from all lookup default


```

Then I edit /etc/iproute2/rt_tables and I have added "2 mytable" at the end of file.

```


root@server /# ip rule add from 192.168.1.0/24 table mytable
root@server /# ip route add throw 192.168.1.0/24 table mytable
root@server /# ip route add default via 192.168.1.1 table mytable


root@firewall /# ip rule list
0:      from all lookup local
32765:  from 192.168.1.0/24 lookup mytable
32766:  from all lookup main
32767:  from all lookup default


root@server /# ping 8.8.8.8
connect: Network is unreachable



```

and after reboot seems that nothing was saved:

```

root@server /# ip rule list
0:      from all lookup local
32766:  from all lookup main
32767:  from all lookup default

```

Why?

---

### Post by SeijiSensei on 2014-05-05
> **KaMZaTa said:**
> 
root@server /# ping 8.8.8.8
connect: Network is unreachable

Is 8.8.8.8 reachable from machines on the 192.168.10.0/24 network?  If so, maybe you just need to reconfigure the masquerading rules on the upstream router to masquerade traffic from 192.168.1.0/24 as well.

```

root@server /# ip rule add from 192.168.1.0/24 table mytable

```
I believe you need to specify the address of eth1 here, not a CIDR subnet.  You're also missing "lookup" and a "priority."  From my experience the rule should read:
```
ip rule add from 192.168.1.52 lookup mytable prio 1000
```

```

root@server /# ip route add throw 192.168.1.0/24 table mytable

```
What does "throw" do?  Why do you need it?

```

root@server /# ip route add default via 192.168.1.1 table mytable

```
You need to specify the interface here as well.  Look at my example again.
```
/sbin/ip route add default via 10.2.2.1 **dev eth2** table newisp
```
That tells the routing code to use this as the default route for eth2.

> and after reboot seems that nothing was saved:
Routing commands are flushed on reboots.  I presume the change you made to rt_tables is still there.

To enforce these rules at boot, place them in /etc/rc.local.  That is the last script run during the boot process.

---

### Post by KaMZaTa on 2014-05-05
For completeness I show you also my /etc/network/interfaces under below:

```

auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
        address 192.168.10.52
        netmask 255.255.255.0
        gateway 192.168.10.1
        post-up iptables-restore < /etc/iptables.up.rules


auto eth1
iface eth1 inet static
        address 192.168.1.52
        netmask 255.255.255.0
        gateway 192.168.1.1

```

Before I forgot to set gateways (sorry) so now I can ping 8.8.8.8:

```

root@server /# ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=47 time=528 ms

```

But what is gateway in use? 192.168.10.1 or 192.168.1.1? 192.168.10.1 because eth0 is sorted first? How can I check?

About "throw rule": "[A throw rule merely tells the system to stop processing the current table if the destination address matches the criteria provided]("http://openvz.org/Source_based_routing")"

---

### Post by SeijiSensei on 2014-05-06
Install **traceroute** and run "traceroute -n 8.8.8.8".

---

### Post by KaMZaTa on 2014-05-07
While I try add this [interesting reading]("http://lartc.org/howto/lartc.rpdb.multiple-links.html").

---

