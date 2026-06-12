---
title: "Ubuntu server 15.05 NAT problem"
date: 2016-02-22
forum: Networking &amp; Wireless
---

### Post by federicop2 on 2016-02-22
Hello,
i'm trying to setup a simple NAT:

the computer has 2 network interfaces
enp5s0  -  external, internet.
enp2s0  -  lan

outgoing traffic from lan should reach the internet through the same public IP
but i'm not able to get it working :(

lan machines has theese settings:
gateway 192.168.135.254
address 192.168.135.XXX
network 192.168.135.0
netmask 255.255.255.0


cat /etc/network/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto enp5s0
iface enp5s0 inet static
        [public ip settings]


auto enp2s0
iface enp2s0 inet static
        address 192.168.135.254
        broadcast 192.168.135.255
        netmask 255.255.255.0
        network 192.168.135.0



```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         internet_gateway   0.0.0.0         UG    0      0        0 enp5s0
internet_address   0.0.0.0         255.255.255.248 U     0      0        0 enp5s0
192.168.135.0   0.0.0.0         255.255.255.0   U     0      0        0 enp2s0

```

sudo iptables -v -t nat -L
```
Chain PREROUTING (policy ACCEPT 89 packets, 4254 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain INPUT (policy ACCEPT 7 packets, 360 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 108 packets, 6747 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain POSTROUTING (policy ACCEPT 44 packets, 2907 bytes)
 pkts bytes target     prot opt in     out     source               destination
   64  3840 MASQUERADE  all  --  any    enp2s0  anywhere             anywhere



```

sudo iptables -v  -L FORWARD
```
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes) pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  enp2s0 enp5s0  anywhere             anywhere             state RELATED,ESTABLISHED
    0     0 ACCEPT     all  --  enp5s0 enp2s0  anywhere             anywhere



```

sudo cat /proc/sys/net/ipv4/ip_forward
```
1
```

ifconfig shows that both enp2s0 and enp5s0 are UP and RUNNING



i can reach the internet from enp5s0 but not from lan machines through enp2s0

sudo tcpdump -i enp2s0 reports NOTHING. no packets
which is the the most weird thing because there are at least 10 computers connected to that lan (plus IP cams and printers)

p.s.
i'm really sorry for my bad english.
i hope you will be able to understand what i wrote

---

### Post by newbie-user on 2016-02-22
Is the cable plugged into enp2s0? Can you ping enp2s0 from the server itself?

---

### Post by The Cog on 2016-02-22
> Is the cable plugged into enp2s0?
The fact that the interface shows RUNNING indicates that the cable is connected and working.

Have you enabled ip forwarding? [http://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent](http://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent)

---

### Post by federicop2 on 2016-02-23
> **The Cog said:**
> The fact that the interface shows RUNNING indicates that the cable is connected and working.

Have you enabled ip forwarding? [http://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent](http://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent)

ipv4 forwarding is enabled (uncommented from /etc/sysctl.conf )
also [COLOR=#000000]sudo cat /proc/sys/net/ipv4/ip_forward shows 1.
[/COLOR]ipv6 forwarding is disabled. Enabling or disabling it doesn't seem to make a difference


sudo ping -I enp2s0 127.0.0.1
```
PING 127.0.0.1 (127.0.0.1) from 192.168.135.254 enp2s0: 56(84) bytes of data.
From 192.168.135.254 icmp_seq=1 Destination Host Unreachable
[...]

```
sudo ping -I enp2s0 8.8.8.8
```
PING 8.8.8.8 (8.8.8.8) from 192.168.135.254 enp2s0: 56(84) bytes of data.
From 192.168.135.254 icmp_seq=1 Destination Host Unreachable
[...]

```
sudo tcpdump -i enp5s0 port not 22

tcpdump shows nothing during the above pings.....



sudo ping -I enp5s0 192.168.135.254
```
PING 192.168.135.254 (192.168.135.254) from 93.150.29.242 enp5s0: 56(84) bytes of data.
^C
--- 192.168.135.254 ping statistics ---
87 packets transmitted, 0 received, 100% packet loss, time 86688ms

```
sudo tcpdump -vvv -i enp5s0 port not 22  (during the above ping)
```
09:20:49.989543 IP (tos 0x0, ttl 64, id 9220, offset 0, flags [DF], proto ICMP (1), length 84)
    "example.com" > 192.168.135.254: ICMP echo request, id 4662, seq 67, length 64
09:20:50.997533 IP (tos 0x0, ttl 64, id 9272, offset 0, flags [DF], proto ICMP (1), length 84)
     "example.com"  > 192.168.135.254: ICMP echo request, id 4662, seq 68, length 64
09:20:52.005547 IP (tos 0x0, ttl 64, id 9435, offset 0, flags [DF], proto ICMP (1), length 84)
     "example.com"  > 192.168.135.254: ICMP echo request, id 4662, seq 69, length 64

```

---

### Post by The Cog on 2016-02-23
I wonder if we're missing something obvious. Can you post the output of 
```
ifconfig
ip -s -d link
```
after trying to ping one of the LAN PCs for a while?

---

### Post by federicop2 on 2016-02-23
> **The Cog said:**
> I wonder if we're missing something obvious. Can you post the output of 
```
ifconfig
ip -s -d link
```
after trying to ping one of the LAN PCs for a while?

i bet there's something obvious, but it's driving me crazy (plus i'm a newbie..)

ping 192.168.135.186
```
PING 192.168.135.186 (192.168.135.186) 56(84) bytes of data.
From 192.168.135.254 icmp_seq=1 Destination Host Unreachable


```

sudo ping -I enp2s0 192.168.135.186
```
PING 192.168.135.186 (192.168.135.186) from 192.168.135.254 enp2s0: 56(84) bytes of data.
From 192.168.135.254 icmp_seq=1 Destination Host Unreachable

```



ifconfig
```
enp2s0    Link encap:Ethernet  HWaddr 60:e3:27:00:21:98
          inet addr:192.168.135.254  Bcast:192.168.135.255  Mask:255.255.255.0
          inet6 addr: fe80::62e3:27ff:fe00:2198/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:1202 (1.2 KB)


enp5s0    Link encap:Ethernet  HWaddr 30:5a:3a:7e:7a:3a
          inet addr: public_ip  Bcast: public_bcast  Mask:255.255.255.248
          inet6 addr: public_ip Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6729 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2106310 (2.1 MB)  TX bytes:3283026 (3.2 MB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13936 (13.9 KB)  TX bytes:13936 (13.9 KB)

```


ip -s -d link
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00 promiscuity 0 addrgenmode eui64
    RX: bytes  packets  errors  dropped overrun mcast
    27712      300      0       0       0       0
    TX: bytes  packets  errors  dropped carrier collsns
    27712      300      0       0       0       0
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 60:e3:27:00:21:98 brd ff:ff:ff:ff:ff:ff promiscuity 0 addrgenmode eui64
    RX: bytes  packets  errors  dropped overrun mcast
    0          0        0       0       0       0
    TX: bytes  packets  errors  dropped carrier collsns
    6410       147      0       0       0       0
3: enp5s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 30:5a:3a:7e:7a:3a brd ff:ff:ff:ff:ff:ff promiscuity 0 addrgenmode eui64
    RX: bytes  packets  errors  dropped overrun mcast
    2110692    6795     0       0       0       0
    TX: bytes  packets  errors  dropped carrier collsns
    3289527    5216     0       0       0       0



```

maybe the iptables MASQUERADING settings are wrong?
(i posted them in the first post)

---

### Post by The Cog on 2016-02-23
> maybe the iptables MASQUERADING settings are wrong?
Actually, yes it is wrong. It should go on the internet facing interface enp5s0 instead. 

That would stop things working, but I'm not sure that it should prevent receive packets from being counted in on the interface. enp2s0 does appear to be as deaf as a post, even though it has detected the cable present. 
And I don't know what could make it deaf like that.

---

### Post by federicop2 on 2016-02-24
> **The Cog said:**
> Actually, yes it is wrong. It should go on the internet facing interface enp5s0 instead. 

That would stop things working, but I'm not sure that it should prevent receive packets from being counted in on the interface. enp2s0 does appear to be as deaf as a post, even though it has detected the cable present. 
And I don't know what could make it deaf like that.

I swapped the 2 interfaces and completely flushed iptables rules.
enp5s0 is now able to ping and being pinged from LAN
enp2s0...... i really don't know... there was a moment (through the many reboots) it worked and reached the internet..
now it doesn't work anymore..

It seems that ONLY ONE NIC works at a time.
If i let enp5s0 down and bring enp2s0 up (configured with the public ip stuff) it works and i reach the Internet through it.

I'm sure enp2s0 is not broken because we tested it with other windows computers and even another Ubuntu (Home, not server) computer.
Both enp2s0 and enp5s0 has the same controller (both TP-LINK 1Gbit ethernet...)

---

### Post by federicop2 on 2016-02-24
[SIZE=6][B]EDIT
[/B][/SIZE]SOLVED with this iptables rule
sudo iptables -A INPUT -i enp2s0 -j ACCEPT

lan machines are able to use my dns.

last thing which confuses me is that
sudo ping -I enp2s0 google.it
still reports
```

PING google.it (173.194.112.152) from 192.168.135.254 enp2s0: 56(84) bytes of data.
From 192.168.135.254 icmp_seq=1 Destination Host Unreachable

```

OLD POST:
> 
ok finally almost solved!!!
the main problem was... unbelievable...

if I
sudo reboot
after making changes, then the second NIC won't work (or ONE of the nic won't work...)
if I
sudo poweroff
and then I manually switch on the computer... everything works..

I don't know why, but I tested this behaviour several times.........


Now i have the last problem:
every lan machine has 192.168.135.254 as DNS. (which is my second nic, so i'm the dns)
I installed bind9 to cache DNS requests (the main and real DNS will be the ISP DNS).
configured to listen-on 192.168.135.254
but.. it's not working :(
it's working only if accessed from enp5s0 (the internet nic).
not working if accessed from enp2s0 (lan, 192.168.135.254)

network/interfaces configurations:
```

auto lo
iface lo inet loopback


# The primary network interface
auto enp5s0
iface enp5s0 inet static
        [public ip stuff]
        dns-nameserver 127.0.0.1


auto enp2s0
iface enp2s0 inet static
        address 192.168.135.254
        broadcast 192.168.135.255
        netmask 255.255.255.0
        network 192.168.135.0

```

bind9 configurations:
```

options {
        directory "/var/cache/bind";
        listen-on {
                127.0.0.1;
                192.168.135.254;
        };


        forwarders {
                isp_dns;
        };


        dnssec-validation auto;


        auth-nxdomain no;    # conform to RFC1035
        //listen-on-v6 { any; };
};

```





---

