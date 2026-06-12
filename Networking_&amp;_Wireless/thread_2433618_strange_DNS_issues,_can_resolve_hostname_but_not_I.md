---
title: "strange DNS issues, can resolve hostname but not IP and access some sites"
date: 2019-12-22
forum: Networking &amp; Wireless
---

### Post by moopthemighty on 2019-12-22
**examples:**

ping hangs on IP address

```

moop@fightbiscuits:~/Downloads$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5114ms

```

but not on hostname

```

moop@fightbiscuits:~/Downloads$ ping google.com
PING google.com(dfw25s27-in-x0e.1e100.net (2607:f8b0:4000:814::200e)) 56 data bytes
64 bytes from dfw25s27-in-x0e.1e100.net (2607:f8b0:4000:814::200e): icmp_seq=1 ttl=55 time=24.4 ms
64 bytes from dfw25s27-in-x0e.1e100.net (2607:f8b0:4000:814::200e): icmp_seq=2 ttl=55 time=23.0 ms
64 bytes from dfw25s27-in-x0e.1e100.net (2607:f8b0:4000:814::200e): icmp_seq=3 ttl=55 time=18.2 ms
^C
--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 18.233/21.900/24.410/2.651 ms

```

can connect to ubuntu servers so updates work

```

moop@fightbiscuits:~/Downloads$ sudo apt-get update
Get:1 file:/var/cuda-repo-10-0-local-10.0.130-410.48  InRelease
Ign:1 file:/var/cuda-repo-10-0-local-10.0.130-410.48  InRelease
Get:2 file:/var/cuda-repo-10-0-local-10.0.130-410.48  Release [574 B]
Get:2 file:/var/cuda-repo-10-0-local-10.0.130-410.48  Release [574 B]
Get:3 file:/var/cuda-repo-10-0-local-10.0.130-410.48  Release.gpg [833 B]
Get:3 file:/var/cuda-repo-10-0-local-10.0.130-410.48  Release.gpg [833 B]
Ign:3 file:/var/cuda-repo-10-0-local-10.0.130-410.48  Release.gpg
Hit:4 https://deb.nodesource.com/node_13.x bionic InRelease
Hit:5 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Hit:6 http://archive.canonical.com/ubuntu bionic InRelease

```

It's almost as if it is random as to what sites it can access as I can curl and wget certain sites and not others.

I don't know what to do. The conf files look ok. someone please walk me through the steps to troubleshoot this, I used to be pretty good at networking and linux but years of depression have robbed me of my skills and I'm trying to get back in the game!

---

### Post by TheFu on 2019-12-22
Looks like IPv6 networking is working, but not IPv4.
Not all websites support IPv6.  None of mine do.  I don't have any IPv6 DNS records at all.

---

### Post by moopthemighty on 2019-12-22
So how do i troubleshoot what to do to fix it?

---

### Post by chili555 on 2019-12-22
Did your router issue an IPv6 address only and not IPv4? Check:```
ip addr show
```You should see something like:

```
3: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether xx:c5:d4:0e:64:xx brd ff:ff:ff:ff:ff:ff
    [COLOR="#FF0000"]inet 192.168.0.11/24 [/COLOR]brd 192.168.0.255 scope global dynamic noprefixroute wlp3s0
       valid_lft 169902sec preferred_lft 169902sec
    inet6 2600:1700:5aa0:83c:b9cc:b20b:18f9:ba08/64 scope global temporary dynamic 
       valid_lft 601905sec preferred_lft 83395sec
    inet6 2600:1700:5aa0:83c:3c95:2494:87db:e8fa/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 2591796sec preferred_lft 604596sec
    inet6 fe80::3f3e:a058:dc6d:df91/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```I suspect that you have inet6, that is IPv6, only. Please try rebooting the router.

---

### Post by moopthemighty on 2019-12-22
Hmmm...  wierd but I'll reboot the router when I'm done setting this other stuff up. Getting a virtual machine installed to run a gameserver. Thank you, would there be anything else I could try if that doesn't work?

```

moop@fightbiscuits:/etc/update-motd.d$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether b4:b5:2f:cf:75:42 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.44/24 brd 192.168.0.255 scope global dynamic noprefixroute eno1
       valid_lft 574122sec preferred_lft 574122sec
    inet6 2600:8807:5400:1321:c029:5c57:dd21:2021/64 scope global temporary dynamic
       valid_lft 86398sec preferred_lft 53469sec
    inet6 2600:8807:5400:1321::631a/128 scope global dynamic noprefixroute
       valid_lft 491092sec preferred_lft 491092sec
    inet6 2600:8807:5400:1321:c3d:4028:fa88:bb05/64 scope global temporary deprecated dynamic
       valid_lft 86398sec preferred_lft 0sec
    inet6 2600:8807:5400:1321:c0c6:e848:ebfe:bdb5/64 scope global dynamic mngtmpaddr noprefixroute
       valid_lft 86398sec preferred_lft 86398sec
    inet6 fe80::2a4c:110c:c7ef:6a0f/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
moop@fightbiscuits:/etc/update-motd.d$

```

---

### Post by chili555 on 2019-12-22
You certainly have an inet (IPv4) address. Can you ping the router?```
ping -c3 192.168.0.1
```It may otherwise be 192.168.0.254.

Any clues here?```
traceroute -4 www.ubuntu.com
```

---

### Post by moopthemighty on 2019-12-22
wI don't see anything odd with the router configuration but I'll delete the entry from it and reset now
```

moop@fightbiscuits:/$ traceroute -4 www.ubuntu.com
traceroute to www.ubuntu.com (91.189.89.115), 30 hops max, 60 byte packets
 1  _gateway (192.168.0.1)  2.288 ms  3.645 ms  4.838 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
(kept going to 30)
moop@fightbiscuits:/$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=2.22 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=1.62 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=2.09 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 1.621/1.980/2.222/0.264 ms

moop@fightbiscuits:/$ 


```

omg I'm a moron. I'm sorry for wasting your time on such an obvious step. resetting the router worked.

---

### Post by chili555 on 2019-12-22
It doesn't appear that IPv4 traffic gets past the router. I agree that the problem may be in its configuration. Please check.

---

### Post by TheFu on 2019-12-22
> **moopthemighty said:**
>  omg I'm a moron. I'm sorry for wasting your time on such an obvious step. resetting the router worked.

We've all been there too.  What you could do to help the community here is use the "thread tools" button near the top and mark this thread "SOLVED".

---

