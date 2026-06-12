---
title: "NIC installed - can't ping, Internet works"
date: 2005-05-17
forum: Networking &amp; Wireless
---

### Post by SWAT on 2005-05-17
First off let me say that I feel really silly posting this, because I somehow know the answer to be very simple. But here it goes.
I installed Hoary and everything works. I can view files with the SMB viewer, I can use IRC, Firefox, GAIM, the work. At this moment I'm feeling  \\:D/ 
Now I install a home Debian-server and try to *ping/ssh* it. It doesn't work at all, I can't even ping my router! With ping I get "Destination Host unreachable" and with SSH I get a  "no route to host" error. When I try to ping the internet or resolve a website-name, it works flawlessly. When I ping from my Debian server I get a ping reply from my router, but not from my current computer.
I even switched my firewall off to check if it could be that, well the firewall isn't installed now and it still doesn't work  ](*,) 
I'm using a static-IP configuration (if that helps). Could it be that I need to edit a couple of files so linux doesn't use the DNS to resolve them or edit the host files something? (like the LAN adresses)

---

### Post by alastair on 2005-05-17
Is this a problem with a Debian machine or the Ubuntu machine? I could not follow all of it.

Describe the network and what is connected e.g.

```

sys A  <-----------------------> sys B
IP = A                           IP = B

```

ping <B> from sys A fails?

Check (on A) :

ifconfig -a
route -n

and also check this on B.

---

### Post by SWAT on 2005-05-17
```
Ubuntu (U)                 Debian (D)                Router (R)
    |                           |                         |
     -----------------------------------------------------

```

(U) can't ping (D) or (R)
(U) can ping the internet
(D) can ping (R) but can't ping (U)
(D) can ping the internet
--> The Ubuntu machine has a problem somewhere. But GAIM/Xchat/Firefox work fine  :-? (I'm ONLY using eth1, it's the only one connected)

*ifconfig -a* gives this: 
```
eth0      Link encap:Ethernet  HWaddr 00:11:09:67:DB:A7
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fe67:dba7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:15592 (15.2 KiB)
          Interrupt:20 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:11:09:67:DB:A8
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fe67:dba8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:509554 errors:0 dropped:0 overruns:0 frame:0
          TX packets:521131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:201936934 (192.5 MiB)  TX bytes:217125019 (207.0 MiB)
          Interrupt:16 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:51902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51902 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3941382 (3.7 MiB)  TX bytes:3941382 (3.7 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

*route -n* gives: 
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

---

### Post by nad on 2005-05-18
Are both the ubutu and debian machines multihomed? Are you connecting through the debian machine? Do you have a dns running?

Are you pinging hostnames or addresses? Yes, I imagine that a hosts file would help.

---

### Post by SWAT on 2005-05-18
(U) and (D) and (R) are connected to the same switch. (R) is connected to the internet. I tried to ping the IP addresses. (which didn't work). I find it strange that my Debian (stable) machine just worked and that Ubuntu has problems with this.
But could you give me pointers on what config files I should check/edit? (I guess the error must be in there somewhere) I can vaguely remember that somehow there is a way to disable DNS for certain hosts (something to do with the hostfile)....

---

### Post by alastair on 2005-05-18
Try removing BOTH the eth0 routes (you say eth1 is the only one connected).

---

### Post by nad on 2005-05-18
DNS is obviously working on the wan, as your web apps are correctly connecting. You can check /etc/resolv.conf to see the addresses used. You don't want to disable dns unless you have your own server running.

Something internal is being confused. This is why I asked if the machines are multihomed. The ubuntu machine is. The route file looks correct.

Just add entries to your /etc/hosts file, dotted_quad_address canonical_name, one per line to hard resolve your internal addresses. 

Any different?

---

### Post by SWAT on 2005-05-18
I edited my hosts file AND disabled the second ethernet adapter. It works now :D, I think it was the eth0 device. Yet I still wonder why... But hey, it works  :grin: 
There was only one eth device active, so why was Ubuntu flipping and how can I choose (in the future) the eth device to be used by a certain service? For example: 1x Copy using eth0 and 1x Copy using eth1?

---

### Post by alastair on 2005-05-18
I have not looked into this in detail - but Ubuntu seems to have problems if you have 2 routes for the same network configured. This has happened to me in the past on my laptop with the wireless device. Deleting a route solved things.

---

