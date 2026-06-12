---
title: "Internet connection dies periodically"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by blairm on 2008-12-26
Hi,

A couple of days ago I updated my parents' Ubuntu to Hardy Heron, and since I've done that their internet connection dies about every 30 minutes,
Restarting the computer brings it back.
They have a dynamic address - could that be part of the problem?
Not sure whether it's any use, but the following is the output of ifconfig - however, this is while the connection is working as expected.

eth0      Link encap:Ethernet  HWaddr 00:1b:fc:35:ca:34  
          inet addr:10.1.1.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21b:fcff:fe35:ca34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:824 errors:0 dropped:0 overruns:0 frame:0
          TX packets:900 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:713519 (696.7 KB)  TX bytes:185965 (181.6 KB)
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70900 (69.2 KB)  TX bytes:70900 (69.2 KB)


Any help would be much appreciated,

Thanks,

Blair

---

### Post by zvacet on 2008-12-27
Try with 

```
sudo pppoeconf
```

---

### Post by HereInOz on 2008-12-27
Ok, so when it "dies" are you still able to ping an IP address or not?  I am trying to work out here whether it is a DNS resolution problem, or a TCP/IP problem.

Try pinging 72.14.205.100 and if you get a response, then try to ping google.com.

If the IP address ping works but the url ping doesn't, it is DNS, but if the IP address ping fails, then it is a TCP/IP issue.

Your ifconfig output looks OK, so if it is a TCP/IP issue, then I would suspect hardware to start with, and perhaps replace the network card as a quick and easy test.  I know that it happened when you did the Hardy upgrade, but it could have been coincidental, and may not be related to the Hardy upgrade at all.

---

### Post by blairm on 2008-12-27
Thanks for your replies, and apologies for the delay in getting back to you.

sudo ppoeconf - says it found one ethernet device (eth0). When I selected yes, it performed a scan came up with the following:

Sorry, I scanned 1 interface, but the Access             &#9474; 
          &#9474; Concentrator of your provider did not respond. Please    &#9474; 
          &#9474; check your network and modem cables. Another reason      &#9474; 
          &#9474; for the scan failure may also be another running pppoe   &#9474; 
          &#9474; process which controls the modem.      

In terms of the pings, got the following results:

robin@timaru-desktop:~$ ping 72.14.205.100 
PING 72.14.205.100 (72.14.205.100) 56(84) bytes of data.
64 bytes from 72.14.205.100: icmp_seq=1 ttl=240 time=282 ms
64 bytes from 72.14.205.100: icmp_seq=2 ttl=240 time=280 ms
64 bytes from 72.14.205.100: icmp_seq=3 ttl=240 time=282 ms
64 bytes from 72.14.205.100: icmp_seq=4 ttl=240 time=281 ms
64 bytes from 72.14.205.100: icmp_seq=5 ttl=240 time=282 ms

robin@timaru-desktop:~$ ping google.com
PING google.com (209.85.171.100) 56(84) bytes of data.
64 bytes from google.com (209.85.171.100): icmp_seq=1 ttl=241 time=243 ms
64 bytes from google.com (209.85.171.100): icmp_seq=2 ttl=241 time=240 ms
64 bytes from google.com (209.85.171.100): icmp_seq=3 ttl=241 time=240 ms
64 bytes from google.com (209.85.171.100): icmp_seq=4 ttl=241 time=240 ms

Not sure whether it's important, but using a dlink dsl502t modem/router.

---

