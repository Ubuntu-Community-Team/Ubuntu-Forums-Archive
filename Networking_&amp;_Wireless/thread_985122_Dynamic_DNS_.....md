---
title: "Dynamic DNS ...."
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by dbee on 2008-11-17
I've set up dynamic dns to point to my localhost so that i can show clients the webpages that I've produced. It's a really handy feature for me.

Problem is though, that it very rarely works. I've tried everything that i can think of but i'm having no luck with this.

I'm working on a home connection behind a home router.

```

eth0      Link encap:Ethernet  HWaddr 00:16:36:b3:86:1b  
          inet addr:192.168.1.25  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:feb3:861b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6704 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:5852814 (5.5 MB)  TX bytes:1528628 (1.4 MB)
          Base address:0x4000 Memory:da000000-da020000 

```

I've set 192.168.1.25 as a static NAT in my Netgear home router ...

I've configured the IP address in DynDNS correctly (213.202.167.206) and when i ping the url, i get the correct IP back from DynDNS. It has to be an issue on my side of things.

```

babo@eire:~$ ping ere.homelinux.com
PING eire.homelinux.com (213.202.167.207) 56(84) bytes of data.
64 bytes from 213-202-167-207.bas503.dsl.esat.net (213.202.167.206): icmp_seq=1 ttl=255 time=1.15 ms
64 bytes from 213-202-167-207.bas503.dsl.esat.net (213.202.167.206): icmp_seq=2 ttl=255 time=0.619 ms
64 bytes from 213-202-167-207.bas503.dsl.esat.net (213.202.167.206): icmp_seq=3 ttl=255 time=1.12 ms

--- eire.homelinux.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.619/0.964/1.151/0.245 ms

```

I can access the page on localhost no problem.

Does anyone have any idea where i should go from here ?

Thanks,

---

### Post by Iowan on 2008-11-17
Can you access the page(s) from another machine on your network (inside the router, but not the server)?

---

### Post by dbee on 2008-11-19
I can access the website at 192.168.1.25 but i can't access it at ere.homelinux.com

---

### Post by hyper_ch on 2008-11-19
you need

(1) setup your machine to a static IP in your lan
(2) forward port 80 (for http) from the router to your machine's static IP

---

### Post by superprash2003 on 2008-11-19
and incase you have firestarter or anything similar running, you need to open port 80 there..

---

### Post by dbee on 2008-11-21
Thanks.

I don't have any firewall. I have the computer set up under static NAT as is. I opened port 80 and that seemed to work for a while yesterday.

Now today it still won't work again ...

---

### Post by superprash2003 on 2008-11-21
ensure that your ip address hasnt changed..

---

