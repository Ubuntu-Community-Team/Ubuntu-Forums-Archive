---
title: "routing problems with zaurus"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by Sir_Yaro on 2007-03-14
That's my network:
[IMG]http://yaro.gdi.pl/pic/diagram01.jpg[/IMG]

No matter what i try I can't set up routing for my palmtop **zaurus**.

zaurus ping usb0 and eth0 and can't get 192.168.0.1 (router)

On **desktop**:
```
[yaro]@d[~]$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:02:B3:95:9F:CC
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:b3ff:fe95:9fcc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16685 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14996632 (14.3 MiB)  TX bytes:3004685 (2.8 MiB)

``````

[yaro]@d[~]$ ifconfig usb0
usb0      Link encap:Ethernet  HWaddr FE:69:EC:91:C3:A8
          inet addr:192.168.129.1  Bcast:192.168.129.255  Mask:255.255.255.0
          inet6 addr: fe80::fc69:ecff:fe91:c3a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1494  Metric:1
          RX packets:564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:33401 (32.6 KiB)  TX bytes:47072 (45.9 KiB)

[yaro]@d[~]$  
```

routing table:
```
[yaro]@d[~]$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.129.0   *               255.255.255.0   U     0      0        0 usb0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
172.16.10.0     *               255.255.255.0   U     0      0        0 vmnet8
default         router          0.0.0.0         UG    0      0        0 eth0
[yaro]@d[~]$ host router
router has address 192.168.0.1
[yaro]@d[~]$  

```
answers on **desktop**:
```
[yaro]@d[~]$ ping -c 1 192.168.129.201
PING 192.168.129.201 (192.168.129.201) 56(84) bytes of data.
64 bytes from 192.168.129.201: icmp_seq=1 ttl=255 time=1.37 ms

--- 192.168.129.201 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.375/1.375/1.375/0.000 ms
[yaro]@d[~]$ 
[yaro]@d[~]$ ping -c 1 192.168.129.1
PING 192.168.129.1 (192.168.129.1) 56(84) bytes of data.
64 bytes from 192.168.129.1: icmp_seq=1 ttl=64 time=0.078 ms

--- 192.168.129.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.078/0.078/0.078/0.000 ms
[yaro]@d[~]$ 
[yaro]@d[~]$ ping -c 1 192.168.0.100
PING 192.168.0.100 (192.168.0.100) 56(84) bytes of data.
64 bytes from 192.168.0.100: icmp_seq=1 ttl=64 time=0.075 ms

--- 192.168.0.100 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.075/0.075/0.075/0.000 ms
[yaro]@d[~]$ 
[yaro]@d[~]$ ping -c 1 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.417 ms

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.417/0.417/0.417/0.000 ms
[yaro]@d[~]$     

```


On **zaurus**:
```
root@zaurus:~# ifconfig usbd0
usbd0     Link encap:Ethernet  HWaddr 40:00:01:00:00:01
          inet addr:192.168.129.201  Bcast:192.168.129.255  Mask:255.255.255.0
          inet6 addr: fe80::4200:1ff:fe00:1/10 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1494  Metric:1
          RX packets:843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:710 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:55198 (53.9 KiB)  TX bytes:58233 (56.8 KiB)

root@zaurus:~#   
```
answers on **zaurus**:
```
root@zaurus:~# ping -c 1 192.168.129.201
PING 192.168.129.201 (192.168.129.201): 56 data bytes
64 bytes from 192.168.129.201: icmp_seq=0 ttl=255 time=0.4 ms

--- 192.168.129.201 ping statistics ---
1 packets transmitted, 1 packets received, 0% packet loss
round-trip min/avg/max = 0.4/0.4/0.4 ms
root@zaurus:~# 
root@zaurus:~# ping -c 1 192.168.129.1
PING 192.168.129.1 (192.168.129.1): 56 data bytes
64 bytes from 192.168.129.1: icmp_seq=0 ttl=64 time=1.5 ms

--- 192.168.129.1 ping statistics ---
1 packets transmitted, 1 packets received, 0% packet loss
round-trip min/avg/max = 1.5/1.5/1.5 ms
root@zaurus:~# 
root@zaurus:~# ping -c 1 192.168.0.100
PING 192.168.0.100 (192.168.0.100): 56 data bytes
64 bytes from 192.168.0.100: icmp_seq=0 ttl=64 time=1.8 ms

--- 192.168.0.100 ping statistics ---
1 packets transmitted, 1 packets received, 0% packet loss
round-trip min/avg/max = 1.8/1.8/1.8 ms
root@zaurus:~# 
root@zaurus:~# ping -c 1 192.168.0.1
PING 192.168.0.1 (192.168.0.1): 56 data bytes

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 0 packets received, 100% packet loss
root@zaurus:~#    

```
routing table:
```
root@zaurus:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.129.0   *               255.255.255.0   U     0      0        0 usbd0
default         192.168.129.1   0.0.0.0         UG    0      0        0 usbd0
root@zaurus:~#    

```

I tried almost everything but no matter I do i can't route packets from pda to router. It should be damn easy but it just doesn't work and I have no clue why :confused: :confused: :/ 

Any help appreciated...

---

### Post by Sir_Yaro on 2007-03-14
i just find solution!!!

```
modprobe ip_tables
modprobe iptable_nat

echo 1 > /proc/sys/net/ipv4/ip_forward
echo 1 > /proc/sys/net/ipv4/ip_dynaddr

EXTIF="eth0"
INTIF="usb0"

iptables -P INPUT ACCEPT
iptables -F INPUT
iptables -P OUTPUT ACCEPT
iptables -F OUTPUT
iptables -P FORWARD DROP
iptables -F FORWARD
iptables -t nat -F

iptables -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
iptables -A FORWARD -j LOG

iptables -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE
```
and everything works like charm... :)

---

### Post by Sir_Yaro on 2007-03-16
[http://wiki.openzaurus.org/HowTos/Bridging_with_Gentoo](http://wiki.openzaurus.org/HowTos/Bridging_with_Gentoo)

> 
I found that the MTU assigned to usbd0 on the Zaurus was diferent from that assigned to usb0 on the PC: 

Different MYU does not prevent logging into the Zaurus using ssh but does prevent downloading files larger than about 1kB. I am not sure why this happens, it may be related to this kernel bug report 

The solution is to reduce the MTU on the Zaurus end. You can configure the Zaurus to do this automatically by editing /etc/network/interfaces. Find the section starting 'iface usbd0' and add the following line: 

 up ifconfig usbd0 mtu 1494 



---

