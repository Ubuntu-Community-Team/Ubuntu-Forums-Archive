---
title: "Network timeout when I turn on the Ubuntu machine"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by Opsive on 2008-07-31
Hello,

I did a search and my problem is similar to [this thread]("http://ubuntuforums.org/showthread.php?t=627751&highlight=wpn824v2"), but I am unable to post replies so I am creating a new post.

When I turn on my Ubuntu machine, the entire network behind the Netgear WPN824v2 router times out whenever I try to connect to an external site or directly to the router.  When I turn the machine off, everything starts to work again.  What could be causing this?  The Ubuntu machine (version 8 ) is hard wired to the router, and it has been working great for the past couple of months.

Per the suggestion in the thread I linked to, I disabled ipv6 but that didn't change anything.

Thank you,
Justin

---

### Post by superprash2003 on 2008-08-01
go to the ubuntu machine and type ifconfig and post output

---

### Post by Opsive on 2008-08-01
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:80:5c:e3:7e
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8735 (8.5 KB)  TX bytes:12017 (11.7 KB)
          Interrupt:17 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14989 (14.6 KB)  TX bytes:14989 (14.6 KB)

I forgot to mention that when I am getting the network timeout errors I can still connect to the ubuntu machine from a different machine.

Thanks for your help,
Justin

---

### Post by superprash2003 on 2008-08-01
it could be an ipconflict.. is there any other router or pc having the same ip 192.168.1.3?

---

### Post by Opsive on 2008-08-02
No, there isn't.  I changed the machine to use a static address, and got the same results.

Are there any logs of some sort or anything that I can look at to see what is going wrong?

---

