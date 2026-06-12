---
title: "tunneling vpn with ssh help"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by Underpants on 2007-07-16
[http://www.debian-administration.org/articles/539](http://www.debian-administration.org/articles/539)

I've set this up. My server only has one ethernet connection. eth1. 

I can connect the tunnel, and ping eth1 to and from each machine. I am having trouble pinging a different server on the servers local network from my client. 

Any help? is this a packet forwarding problem? 
anything to do with this? net.ipv4.conf.default.forwarding=1

---

### Post by Mr. C. on 2007-07-17
There's too little information here to give you an answer.

Did you enable forwarding as the article suggests ?

MrC

---

### Post by Underpants on 2007-07-17
Let me know what info you'd like and I'll have it here in a few minutes.

Yes, the forwarding is enabled. I rebooted and everything :)

```
 /etc/sysctl.conf: Make sure net.ipv4.conf.default.forwarding is set to 1
net.ipv4.conf.default.forwarding=1
```



My server is behind a DSL router and obviously port 22 is forwarded correctly. I can ping (from here, the client) my servers local ip address (192.168.1.58) and it's pointopoint ip address (10.254.254.1) but I can't ping anything else on my servers network, like 192.168.1.200 or 192.168.1.254

---

### Post by Underpants on 2007-07-17
route -n from the server when the link is established
```

aaron@aaron-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.254.254.0    *               255.255.255.252 U     0      0        0 tun0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
aaron@aaron-desktop:~$ 

```

Here's a traceroute from my client, to an IP on the servers network... so it's routing OUT of my client properly, but it's not forwarding on the server.

```

aaron@aaron-desktop:~$ traceroute 192.168.1.200
traceroute to 192.168.1.200 (192.168.1.200), 30 hops max, 40 byte packets
 1  10.254.254.1 (10.254.254.1)  77.286 ms  73.288 ms  76.428 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *

```


Do I need some sort of route statement that goes between eth1 and tun0? I'm sleepy.

---

### Post by Underpants on 2007-07-17
[https://bugs.launchpad.net/ubuntu/+bug/108896](https://bugs.launchpad.net/ubuntu/+bug/108896)
[http://ubuntuforums.org/showthread.php?t=324001&highlight=net.ipv4.conf.forwarding](http://ubuntuforums.org/showthread.php?t=324001&highlight=net.ipv4.conf.forwarding)

---

### Post by Mr. C. on 2007-07-17
Sorry about the delay.  Are you up and running now ?

MrC

---

