---
title: "ssh tricky problem"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by roboa1983 on 2006-08-30
Hi
I've been trying to solve a ssh solver all day. I'm pretty sure it has to do with my networking, and perhaps the router...
I can use ssh to most computers, and to localhost, and my internet works fine, but just recently, we (some people at the lab I'm working in and me) were assigned static ip addresses. I work on Ubuntu 6.06 and they do on some Fedora Red Hat distribution.
On /etc/hosts, they setup each of their ip addresses and aliases and worked out perfectly, and they could connect with each other. Meanwhile, my computer does not allow for that, although it has the same text. Nevertheless the /etc/hosts file has some IPV6 information.
I've tried to ping their addresses, as well they have tried my address, and nothing seems to work, but on all other hosts, there seems to be no problem. Furthermore, on a external computer, I cannot access these computers either through ssh.
Thanks for the help

---

### Post by craig552 on 2006-08-31
Try using tracepath to find out where the connection fails.

```
tracepath _destination _[_port_]
```

---

### Post by roboa1983 on 2006-08-31
This is the result of the tracepath:
olive@mandos:~/experimental/scratch$ tracepath bat.fquim.una.mx
1:  mandos.fquim.una.mx (132.248.103.158)                0.365ms pmtu 1500
 1:  no reply
 1:  mandos.fquim.una.mx (132.248.103.158)              2004.222ms !H
     Resume: pmtu 1500
Any ideas?

---

### Post by steve.horsley on 2006-08-31
What is your IP address? 
What is the IP address of one machine you are trying to ping? 
Are they on tht same network?
If not, what is the IP address of the router you go via?
Are mandos and bat both aliases for the same machine?

Can you post the output from these commands?
ifconfig
route -n

---

### Post by roboa1983 on 2006-08-31
My IP address is 132.248.103.xx and the other one, the one I'm trying to ping/ssh is the same, only with different xx.
They are on the same network.
Mandos and bat are not different aliases for the same machine. 

olive@mandos:~/zori/src$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:75:86:0E:61
          inet addr:132.248.103.xx  Bcast:132.248.xx.255  Mask:255.255.255.0
          inet6 addr: fe80::204:75ff:fe86:e61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1754866 errors:0 dropped:0 overruns:1739 frame:0
          TX packets:194015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:313675413 (299.1 MiB)  TX bytes:58431602 (55.7 MiB)
          Interrupt:177 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:01:03:DC:70:9E
          inet addr:132.248.103.xx  Bcast:132.248.xx.255  Mask:255.255.255.0
          inet6 addr: fe80::201:3ff:fedc:709e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1751 errors:0 dropped:0 overruns:1 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:146751 (143.3 KiB)  TX bytes:5676 (5.5 KiB)
          Interrupt:185

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2833561 (2.7 MiB)  TX bytes:2833561 (2.7 MiB)

olive@mandos:~/zori/src$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
132.248.103.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1
132.248.103.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         132.248.103.254 0.0.0.0         UG    0      0        0 eth0
0.0.0.0         132.248.103.254 0.0.0.0         UG    0      0        0 eth1
olive@mandos:~/zori/src$

Furthermore, if I try to connect to mandos from an outside source, it doesn't work either.

---

### Post by steve.horsley on 2006-08-31
Odd. I've not seen computers with two interfaces on the same LAN very often before. Are they both the same actual IP address? Not that I think that matters too much, but you should make sure that they both are actually connected to the same LAN. 

It may be worth trying to shut one of them down, just to make sure there's no confusion and to get back to a more normal configuration. e.g. 
> sudo ifdown eth1

You have a good default route, so I see no reason why you should not be contactable from outside once other machines on the same LAN can talk to you.

One thing to check is the IP address that the SSH servers are configured to listen on. Check in /etc/ssh/sshd_config and make sure it's configured to listen on the new address (or 0.0.0.0).

Can you ping the router on 132.248.103.254?

Oh. and make sure that no other machine has your IP address. That can cause confusion when using static IP addresses.

---

### Post by roboa1983 on 2006-09-01
I disabled eth1, and looked at /etc//ssh/sshd_config, and saw that it was listening.
I can now ssh the other computers, and I'm going to wait until someone arrives to see if I can access my account.
Thanks!

---

### Post by roboa1983 on 2006-09-04
Hey
If I can now access the other computers when I'm in the lab, but not when I'm at home, it probably is a router problem, right?
Thanks

---

