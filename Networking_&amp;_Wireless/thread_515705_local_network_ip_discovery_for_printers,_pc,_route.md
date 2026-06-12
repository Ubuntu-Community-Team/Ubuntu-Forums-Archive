---
title: "local network ip discovery for printers, pc, routers, etc"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2007-08-02
what can I run for it to tell me what my devices are connectoed to my local network

I know this  

networked HP laser is 192.168.1.102
linksys router 192.168.1.1
motorola cable modem 192.168.100.1
linsys voip 2102 192.168.0.1

What I would like is a program I could run that will tell me all of these

I tried nmap, but it wants a target? what if you dont know what your target is?
I need it to just scan all the ip in a range I suppose and tell me what they are.

---

### Post by eggdeng on 2007-08-02
According to the manual, nmap is supposed to discover hosts with the -sL switch, but I haven't been able to get it to work. It will take ranges as arguments though. I tried

```
 nmap 192.168.2.0-255
```

> Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-08-02 21:09 CEST
Interesting ports on 192.168.2.1:
Not shown: 1695 closed ports
PORT   STATE SERVICE
53/tcp open  domain
80/tcp open  http

Interesting ports on 192.168.2.2:
Not shown: 1695 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http

Interesting ports on 192.168.2.3:
Not shown: 1695 closed ports
PORT     STATE SERVICE
80/tcp   open  http
6001/tcp open  X11:1

Nmap finished: 256 IP addresses (3 hosts up) scanned in 4.414 seconds

Broadening the range a little, ```
nmap 192.168.0-2.0-255
``` it took quite a bit longer but found another IP.

> Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-08-02 21:13 CEST
Interesting ports on 192.168.0.1:
Not shown: 1695 closed ports
PORT     STATE SERVICE
80/tcp   open  http
6001/tcp open  X11:1

Interesting ports on 192.168.2.1:
Not shown: 1695 closed ports
PORT   STATE SERVICE
53/tcp open  domain
80/tcp open  http

Interesting ports on 192.168.2.2:
Not shown: 1695 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http

Interesting ports on 192.168.2.3:
Not shown: 1695 closed ports
PORT     STATE SERVICE
80/tcp   open  http
6001/tcp open  X11:1

Nmap finished: 768 IP addresses (4 hosts up) scanned in 8.881 seconds

With an IP range as wide as yours, it could take forever though.

---

