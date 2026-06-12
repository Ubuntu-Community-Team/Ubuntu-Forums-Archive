---
title: "ping -c 2 8.8.8.8 connect: Network is unreachable"
date: 2020-09-16
forum: Networking &amp; Wireless
---

### Post by baduba on 2020-09-16
I need a same problem with my ubuntu configs

Can help me ?

```
root@srv00:~# sudo /etc/init.d/networking restart && sudo dhclient
[ ok ] Restarting networking (via systemctl): networking.service.
root@srv00:~# ping -c 2 8.8.8.8
connect: Network is unreachable
root@srv00:~# uname -a
Linux srv00 4.15.0-117-generic #118-Ubuntu SMP Fri Sep 4 20:02:41 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
root@srv00:~# cat /etc/hosts
127.0.0.1 localhost
#10.0.0.8 localhost
127.0.1.1 srv00


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
root@srv00:~# cat /hosts
cat: /hosts: No such file or directory
root@srv00:~# cat /etc/hosts
127.0.0.1 localhost
#10.0.0.8 localhost
127.0.1.1 srv00


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
root@srv00:~# ifconfig -a
docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:d2:de:b4:a8  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enp0s3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::a00:27ff:fe85:ffbd  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:85:ff:bd  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 141  bytes 43718 (43.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 19  base 0xd020


enp0s8: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.125  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::a00:27ff:fe47:71be  prefixlen 64  scopeid 0x20<link>
        inet6 2804:5500:0:8401:a00:27ff:fe47:71be  prefixlen 64  scopeid 0x0<global>
        ether 08:00:27:47:71:be  txqueuelen 1000  (Ethernet)
        RX packets 1557  bytes 196338 (196.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1244  bytes 192594 (192.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  base 0xd240


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 12  bytes 720 (720.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 12  bytes 720 (720.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


root@srv00:~#
```

---

### Post by TheFu on 2020-09-16
I can't help at all with docker, but for normal ubuntu servers, please follow these troubleshooting steps, in order.
[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

My first guesses are that either 
[LIST]
[*]a routing problem, 
[*]firewall problem, or 
[*]driver problem.
[/LIST]
Could be a HW issue too. Can it ping anything else on the LAN? 

That's why troubleshooting steps should be done in order.

---

### Post by SeijiSensei on 2020-09-16
Install traceroute from the repositories. It will show every step along the way between you and 8.8.8.8.

```

$ traceroute 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 64 hops max
  1   192.168.100.1  0.520ms  0.387ms  0.380ms 
  2   10.16.144.1  7.433ms  7.926ms  8.568ms 
  3   146.115.22.197  9.605ms  9.285ms  11.257ms 
  4   207.172.18.97  17.750ms  17.335ms  19.046ms 
  5   207.172.19.76  18.634ms  17.730ms  18.568ms 
  6   207.172.19.94  16.642ms  16.666ms  16.504ms 
  7   72.14.219.192  16.955ms  15.984ms  16.560ms 
  8   108.170.248.97  15.653ms  16.049ms  15.869ms 
  9   8.8.8.8  16.822ms  17.470ms  16.826ms 

```

---

### Post by The Cog on 2020-09-16
Can you post the result of these commands:
```
ip address
ip route
ip route get 8.8.8.8
ip neighbor
```

---

### Post by baduba on 2020-09-17
root@srv00:~# traceroute 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  192.168.0.1 (192.168.0.1)  8.288 ms  8.262 ms  9.421 ms
 2  10.100.100.1 (10.100.100.1)  9.897 ms  9.527 ms  9.478 ms
 3  9.164.165.45.fiberfamily.com.br (45.165.164.9)  9.260 ms  9.222 ms  11.077 ms
 4  170-246-215-241.redebandalarga.net.br (170.246.215.241)  11.365 ms  11.351 ms  11.336 ms
 5  as15169.saopaulo.sp.ix.br (187.16.218.58)  11.853 ms  11.743 ms  10.723 ms
 6  108.170.245.129 (108.170.245.129)  10.737 ms  4.432 ms 74.125.243.1 (74.125.243.1)  4.010 ms
 7  209.85.248.167 (209.85.248.167)  6.485 ms 209.85.250.51 (209.85.250.51)  7.480 ms 72.14.239.25 (72.14.239.25)  6.048 ms
 8  dns.google (8.8.8.8)  5.984 ms  6.141 ms  5.920 ms
root@srv00:~# ping [www.uol.com.br](www.uol.com.br)
PING [www.uol.com.br(2600:9000:214e:aa00:1:5a19:8b40:93a1](www.uol.com.br(2600:9000:214e:aa00:1:5a19:8b40:93a1) (2600:9000:214e:aa00:1:5a19:8b40:93a1)) 56 data bytes
From 2804:5500:ffff:ffff::2 (2804:5500:ffff:ffff::2) icmp_seq=1 Destination unreachable: No route
From 2804:5500:ffff:ffff::2 (2804:5500:ffff:ffff::2) icmp_seq=2 Destination unreachable: No route
From 2804:5500:ffff:ffff::2 (2804:5500:ffff:ffff::2) icmp_seq=3 Destination unreachable: No route
From 2804:5500:ffff:ffff::2 (2804:5500:ffff:ffff::2) icmp_seq=4 Destination unreachable: No route
^C

---

### Post by baduba on 2020-09-17
root@srv00:~# ip address
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether 08:00:27:85:ff:bd brd ff:ff:ff:ff:ff:ff
    inet6 fe80::a00:27ff:fe85:ffbd/64 scope link
       valid_lft forever preferred_lft forever
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether 08:00:27:47:71:be brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.125/24 brd 192.168.0.255 scope global enp0s8
       valid_lft forever preferred_lft forever
    inet 192.168.0.128/24 brd 192.168.0.255 scope global secondary enp0s8
       valid_lft forever preferred_lft forever
    inet 192.168.0.105/24 brd 192.168.0.255 scope global secondary dynamic enp0s8
       valid_lft 23558sec preferred_lft 23558sec
    inet6 2804:5500:0:8401:a00:27ff:fe47:71be/64 scope global dynamic mngtmpaddr noprefixroute
       valid_lft 295sec preferred_lft 115sec
    inet6 fe80::a00:27ff:fe47:71be/64 scope link
       valid_lft forever preferred_lft forever
4: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default
    link/ether 02:42:d2:de:b4:a8 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
root@srv00:~# ip route
default via 192.168.0.1 dev enp0s8
default via 192.168.0.1 dev enp0s8 proto dhcp src 192.168.0.105 metric 100
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown
192.168.0.0/24 dev enp0s8 proto kernel scope link src 192.168.0.125
192.168.0.1 dev enp0s8 proto dhcp scope link src 192.168.0.105 metric 100
root@srv00:~# ip route get 8.8.8.8
8.8.8.8 via 192.168.0.1 dev enp0s8 src 192.168.0.125 uid 0
    cache
root@srv00:~# ip neighbor
192.168.0.113 dev enp0s8 lladdr f8:da:0c:23:e8:d1 REACHABLE
192.168.0.1 dev enp0s8 lladdr b0:be:76:33:bc:09 REACHABLE
fe80::8432:9591:20a:9a21 dev enp0s8 lladdr f8:da:0c:23:e8:d1 router STALE
2804:5500:0:8401:fd73:5f84:1bee:4e88 dev enp0s8 lladdr f8:da:0c:23:e8:d1 router STALE
fe80::b2be:76ff:fe33:bc09 dev enp0s8 lladdr b0:be:76:33:bc:09 router STALE
root@srv00:~#

---

### Post by TheFu on 2020-09-17
IPv6 is being used.  I find it easier to just disable it completely, but that isn't an option for everyone.
**sudoedit /etc/default/grub**
Modify the line as follows:
```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"
```
**sudo update-grub**
and reboot the system.
That should disable IPv6 on the box, completely.


And *please, please, please, please, please, please, please, please* use code tags whenever posting terminal output.

---

### Post by baduba on 2020-09-17
--- [www.uol.com.br](www.uol.com.br) ping statistics ---
15 packets transmitted, 0 received, +15 errors, 100% packet loss, time 14035ms


root@srv00:~# sudo update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-117-generic
Found initrd image: /boot/initrd.img-4.15.0-117-generic
Found linux image: /boot/vmlinuz-4.15.0-109-generic
Found initrd image: /boot/initrd.img-4.15.0-109-generic
done
root@srv00:~# ping [www.uol.com.br](www.uol.com.br)
PING [www.uol.com.br(2600:9000:214e:5400:1:5a19:8b40:93a1](www.uol.com.br(2600:9000:214e:5400:1:5a19:8b40:93a1) (2600:9000:214e:5400:1:5a19:8b40:93a1)) 56 data bytes
From 2804:5500:ffff:ffff::2 (2804:5500:ffff:ffff::2) icmp_seq=1 Destination unreachable: No route
From 2804:5500:ffff:ffff::2 (2804:5500:ffff:ffff::2) icmp_seq=2 Destination unreachable: No route
From 2804:5500:ffff:ffff::2 (2804:5500:ffff:ffff::2) icmp_seq=3 Destination unreachable: No route
From 2804:5500:ffff:ffff::2 (2804:5500:ffff:ffff::2) icmp_seq=4 Destination unreachable: No route
From 2804:5500:ffff:ffff::2 (2804:5500:ffff:ffff::2) icmp_seq=5 Destination unreachable: No route
From 2804:5500:ffff:ffff::2 (2804:5500:ffff:ffff::2) icmp_seq=6 Destination unreachable: No route
^C
--- [www.uol.com.br](www.uol.com.br) ping statistics ---
6 packets transmitted, 0 received, +6 errors, 100% packet loss, time 5013ms


root@srv00:~#

---

### Post by TheFu on 2020-09-17
Please prove/confirm that /etc/default/grub was modified and that you rebooted the system.

BTW, ping with only IPv4 should look like this:
```
$ ping [www.uol.com.br](www.uol.com.br) 
PING dftex7xfha8fh.cloudfront.net (13.249.123.45) 56(84) bytes of data.
64 bytes from server-13-249-123-45.atl51.r.cloudfront.net (13.249.123.45): icmp_seq=1 ttl=243 time=14.4 ms
64 bytes from server-13-249-123-45.atl51.r.cloudfront.net (13.249.123.45): icmp_seq=2 ttl=243 time=16.4 ms
```

---

### Post by SeijiSensei on 2020-09-18
I usually disable IPv6 in /etc/sysctl.conf. 

```

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1

```

This works on an ancient CentOS 6.10 machine. But the directory structure under /proc/sys/net/ipv6/conf on my 20.04 machine is the same.  So I'd guess adding these two lines to /etc/sysctl.conf and rebooting will also do the trick.

---

### Post by TheFu on 2020-09-18
Sadly, no.  If only they still worked, my life would have been much easier.

The old sysctl.conf methods haven't worked on ubuntu for at least 4 yrs.Blacklisting the ipv6 module stopped working a few yrs ago too.  I used those methods when they worked because they were less risky than screwing with grub and ansible handled them more easily.

---

