---
title: "My Ipv4 address looks like a local address. Can you explain this?"
date: 2023-11-18
forum: Networking &amp; Wireless
---

### Post by ned12345 on 2023-11-18
Hi All,

My ipv4 address looks like a local address. I am pasting the screenshot below:[IMG]https://i.stack.imgur.com/FzAqs.png[/IMG]
An the output from ip addr is:
```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 98:e7:f4:0f:3d:01 brd ff:ff:ff:ff:ff:ff
3: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether b8:81:98:cc:2d:bf brd ff:ff:ff:ff:ff:ff
    altname wlp3s0
    inet 192.168.1.xx/24 brd 192.168.1.255 scope global dynamic noprefixroute wlo1
       valid_lft 84833sec preferred_lft 84833sec
    inet6 2403:580e:7b3c:0:b69:4100:a7f4:xxxx/64 scope global temporary dynamic 
       valid_lft 6707sec preferred_lft 3105sec
    inet6 2403:580e:7b3c:0:1f61:fea0:6275:xxxx/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 6707sec preferred_lft 3105sec
    inet6 fe80::a117:ea44:a262:xxxx/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```

And the output from ip route is:

```

default via 192.168.1.1 dev wlo1 proto dhcp metric 600 
169.254.0.0/16 dev wlo1 scope link metric 1000 
192.168.1.0/24 dev wlo1 proto kernel scope link src 192.168.1.xx metric 600 
```

I can't see my global ip address.

---

### Post by TheFu on 2023-11-18
Because you have a router that is at 192.168.1.1 as your edge gateway to the internet.  Look up "NAT Router" for more.

---

### Post by SeijiSensei on 2023-11-18
You can only see your external IP from outside your network using a tool like this: [https://www.whatismyip.com/](https://www.whatismyip.com/)

---

### Post by ned12345 on 2023-11-19
Thanks for your answers.

---

