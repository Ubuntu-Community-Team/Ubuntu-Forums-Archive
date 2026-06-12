---
title: "Why would my computer be using IP 1.0.0.0:80?"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by ortaa23 on 2011-07-11
Having difficulties downloading things through Terminal, finding that it's using IP 1.0.0.0:80.

It has been suggested to me that this is some error. I know little about IP's so not really sure where to go from here...

---

### Post by Grenage on 2011-07-11
Please post the output of the following command:

```
ifconfig
```

---

### Post by ortaa23 on 2011-07-11
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:18:bd:f2  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::92e6:baff:fe18:bdf2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58081 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45084 errors:0 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000 
          RX bytes:70489952 (70.4 MB)  TX bytes:5519714 (5.5 MB)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5110 (5.1 KB)  TX bytes:5110 (5.1 KB)

---

### Post by Grenage on 2011-07-11
Your IP is 192.168.1.3, which is a standard class C IP.

What problems are you experiencing.

---

### Post by ortaa23 on 2011-07-11
While trying to resolve Youtube issues using Flash-Aid, which used Terminal to download, some difficulties arose. Here's what someone who seems to know what they're talking about said:

> **lovinglinux said:**
> 
I think you had some issue in your connection, since it was trying to  download from my site using IP 1.0.0.0:80. I suppose it didn't download  the package from the repositories as well. I don't know why it did that.  Do you have any local server, proxy or something else?

---

### Post by Grenage on 2011-07-11
> **ortaa23 said:**
> While trying to resolve Youtube issues using Flash-Aid, which used Terminal to download, some difficulties arose. Here's what someone who seems to know what they're talking about said:

Lovinglinux is a switched-on chap.

Have you had any problems downloading anything else, either from a web page or the repositories?
Is your internet connection through a router provided by the ISP, with machines connected to that router?

If you can post the output of a traceroute, that might help.  It might ask you to install trouceroute; I can't recall if it's there by default:

```
traceroute google.com
```

---

