---
title: "Wired Network Connection, but no internet"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by secretspicy15 on 2007-05-08
Hi everyone,
I just updated to Feisty from Edgy, and now I cannot access the internet. I have a wired connection that worked fine with edgy, without any finagling. Since updating to Feisty, the network connects and appears to get an IP address assigned to it, but Firefox (and I've tried dillo, a bare-bones browser) cannot resolve any domain names. Same thing when I try to ping urls. 
Here are my ifconfig and dhclient outputs:

```
tj@tj-laptop:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 6494
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:02:98:b8:bf
Sending on   LPF/eth1/00:13:02:98:b8:bf
Listening on LPF/eth0/00:15:c5:37:46:29
Sending on   LPF/eth0/00:15:c5:37:46:29
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.252
bound to 10.87.2.19 -- renewal in 232813 seconds.

```
```

tj@tj-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr <address hidden> 
          inet addr:10.87.2.19  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe37:4629/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37291 (36.4 KiB)  TX bytes:2048 (2.0 KiB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr <address hidden>
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:54 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xc000 Memory:dcfff000-dcffffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


```

I've been searching and reading other threads for ages and have tried much and nothing has worked.
If anyone has any ideas, please help, i'm going mad! If you need any more info, just ask.

---

### Post by DWRZ on 2007-05-09
I'm having a similar issue. Have you found a solution yet, by any chance? :(

---

### Post by Calson33 on 2007-05-09
I am having similar problems. I can connect to my router, but not the internet. I did find a temporary work-around if you are using a router. Just reset the router, and internet will be restored.. For a while.

---

### Post by .rdg on 2007-05-09
Could you post your DNS server settings and routing table? In terminal use:

netstat -rn
that one is for routing table

cat /etc/resolv.conf
and that one is for your DNS settings.

Regards,
.rdg

---

### Post by DWRZ on 2007-05-09
I'm hoping my own [post]("http://ubuntuforums.org/showthread.php?p=2620436#post2620436") might get an answer... I'm not using/don't have access to the router, so... :\

---

### Post by .rdg on 2007-05-09
The same strange thing as in DWRZ case - your IP broadcast address is set up wrong. Perhaps there is an issue with dhcp client in Feisty? Don't know - but we'll find out pretty soon. Check back on the post DWRZ linked - I would like to stick to one topic and there I had more info already. It should help you out as well.

---

### Post by subra on 2007-05-09
I had a similar problem. The dns servers that were picked up from the DHCP (feed?) were wrong and didn't work. I tried two solutions:

1. temporary fix: put the correct dns servers by hand. you can do this by choosing network under administration and saving the settings as  new 'location'. The problem with this is that every time the system reboots, it goes back to the wrong dns servers. Same problem with editing the file /etc/resolv.conf by hand. The dns servers change on rebooting. So I wasn't happy and wanted a better solution.

2. Linux guru pablo's suggestion fixed the problem. I went to /etc/dhcp3/dhclient.conf and uncommented the line which says "prepend domain name servers" and put in the right dns servers. Now after rebooting, the dns servers are correct. Firefox works.

---

