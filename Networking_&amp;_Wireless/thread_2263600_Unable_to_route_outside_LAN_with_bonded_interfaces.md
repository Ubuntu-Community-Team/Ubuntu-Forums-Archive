---
title: "Unable to route outside LAN with bonded interfaces"
date: 2015-02-02
forum: Networking &amp; Wireless
---

### Post by Derek_Gentle on 2015-02-02
Hello All

My apologies if the answer is obvious, but I am suffering with a terrible head cold at the moment.

I have just setup a 4-NIC truck on my media storage server.  LACP is working fine as internal connectivity works fine. I've obviously missed something, but I cant brain today as I am suffering from the dumb.  Can anyone help me out?


```

/etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

#eth0 is manually configured, and slave to the "bond0" bonded NIC
auto eth0
iface eth0 inet manual
bond-master bond0

#eth1 ditto, thus creating a 2-link bond.
auto eth1
iface eth1 inet manual
bond-master bond0

#eth2 ditto, thus creating a 3-link bond.
auto eth2
iface eth2 inet manual
bond-master bond0

#eth3 ditto, thus creating a 4-link bond.
auto eth3
iface eth3 inet manual
bond-master bond0

# bond0 is the bonded NIC and can be used like any other normal NIC.
# bond0 is configured using static network information.
auto bond0
iface bond0 inet static
address 192.168.1.251
gateway 192.168.1.100
netmask 255.255.255.0
# bond0 uses standard IEEE 802.3ad LACP bonding protocol
bond-mode 4
bond-miimon 100
bond-lacp-rate 1
bond-slaves eth0 eth1 eth2 eth3


```

```

route                                                                                                         
Kernel IP routing table                                                                                                             
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.100   0.0.0.0         UG    0      0        0 bond0
192.168.1.0     *               255.255.255.0   U     0      0        0 bond0

```

```

:~$ ifconfig
bond0     Link encap:Ethernet  HWaddr 00:30:48:60:54:7a 
          inet addr:192.168.1.251  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe60:547a/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:13761 errors:0 dropped:1350 overruns:0 frame:0
          TX packets:1009 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1575997 (1.5 MB)  TX bytes:114575 (114.5 KB)

eth0      Link encap:Ethernet  HWaddr 00:30:48:60:54:7a 
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:4252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:474693 (474.6 KB)  TX bytes:77059 (77.0 KB)
          Interrupt:19 Memory:feae0000-feb00000

eth1      Link encap:Ethernet  HWaddr 00:30:48:60:54:7a 
          inet6 addr: fe80::230:48ff:fe60:547a/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:4060 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:417040 (417.0 KB)  TX bytes:13112 (13.1 KB)

eth2      Link encap:Ethernet  HWaddr 00:30:48:60:54:7a 
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:2739 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:348224 (348.2 KB)  TX bytes:11978 (11.9 KB)
          Interrupt:17 Memory:fea80000-feaa0000

eth3      Link encap:Ethernet  HWaddr 00:30:48:60:54:7a 
          inet6 addr: fe80::230:48ff:fe60:547a/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:2710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:336040 (336.0 KB)  TX bytes:12426 (12.4 KB)

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13600 (13.6 KB)  TX bytes:13600 (13.6 KB)


```

---

### Post by bab1 on 2015-02-02
> **Derek_Gentle said:**
> Hello All

My apologies if the answer is obvious, but I am suffering with a terrible head cold at the moment.

I have just setup a 4-NIC truck on my media storage server.  LACP is working fine as internal connectivity works fine. I've obviously missed something, but I cant brain today as I am suffering from the dumb.  Can anyone help me out?

How do you handle public DNS?  What happens if you ping a known public URL by IP address.  For example one of the google.com IP addresses is  63.110.67.52.  Can you ping it or use it in a web browser?

---

### Post by Derek_Gentle on 2015-02-02
Hi
This is a server with no desktop or browser. 
When I SSH on to it, I am able to ping by IP.. not by name.

---

### Post by bab1 on 2015-02-02
> **Derek_Gentle said:**
> Hi
This is a server with no desktop or browser. 
When I SSH on to it, I am able to ping by IP.. not by name.

If you can ping an Internet address by IP address from this host then you have a working default gateway (i.e Internet IP connectivity).  It sounds like you have a DNS configuration problem.

How have you configured Internet DNS?  Is the host behind NAT on a private IP network (e.g. 192.168.0.0/24 or some such)?

---

### Post by Derek_Gentle on 2015-02-02
Everything was working fine before I trucked the NIC's together.
The server is connected to a Sophos UTM that provides the DHCP / DNS services through a Cisco SGE2000 switch.
Sophos lives at 192.168.1.100

---

### Post by bab1 on 2015-02-02
> **Derek_Gentle said:**
> Everything was working fine before I trucked the NIC's together.
The server is connected to a Sophos UTM that provides the DHCP / DNS services through a Cisco SGE2000 switch.
Sophos lives at 192.168.1.100
What is the output of these commands from the server```

cat /etc/resolvconf

[COLOR="#0000FF"]**Note that the below has a dot (.) in it**[/COLOR]
cat /etc/resolv.conf

```
What is the hostname and IP address of the server?

[COLOR="#0000FF"]Edit:  What do you get if you use dig.  Such as [/COLOR]```
dig google.com
```

---

### Post by Derek_Gentle on 2015-02-02
```
cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
```

```
dig google.com

; <<>> DiG 9.9.5-3ubuntu0.1-Ubuntu <<>> google.com
;; global options: +cmd
;; connection timed out; no servers could be reached
```

---

### Post by Derek_Gentle on 2015-02-02
accidentally posted twice

---

### Post by bab1 on 2015-02-02
> **Derek_Gentle said:**
> ```
cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
[COLOR="#FF0000"]**#no dns servers listed**[/COLOR]
```

```
dig google.com

; <<>> DiG 9.9.5-3ubuntu0.1-Ubuntu <<>> google.com
;; global options: +cmd
;; [COLOR="#FF0000"]**connection timed out; no servers could be reached**[/COLOR]
```

See my comments in red.  

I'm sorry.  I missed that you didn't add a dns-nameservers line in your /etc/network/interfaces file.  Add in the bond0 config add the line```

dns-nameservers 8.8.8.8 8.8.4.4
```...or whatever DNS servers you wish to use

---

### Post by Derek_Gentle on 2015-02-02
Thanks!
I knew it was something simple :)
I'll blame it one the flu... ;)

```
dig google.com

; <<>> DiG 9.9.5-3ubuntu0.1-Ubuntu <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 59726
;; flags: qr rd ra; QUERY: 1, ANSWER: 11, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             50      IN      A       74.125.226.97
google.com.             50      IN      A       74.125.226.101
google.com.             50      IN      A       74.125.226.100
google.com.             50      IN      A       74.125.226.105
google.com.             50      IN      A       74.125.226.98
google.com.             50      IN      A       74.125.226.110
google.com.             50      IN      A       74.125.226.99
google.com.             50      IN      A       74.125.226.102
google.com.             50      IN      A       74.125.226.104
google.com.             50      IN      A       74.125.226.96
google.com.             50      IN      A       74.125.226.103

;; Query time: 39 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Mon Feb 02 05:07:35 EST 2015
;; MSG SIZE  rcvd: 215


```

---

### Post by bab1 on 2015-02-02
> **Derek_Gentle said:**
> Thanks!
I knew it was something simple :)
I'll blame it one the flu... ;)


Perfect!  Please mark the thread solved.  You can do that from the thread tools menu at the top right.

---

