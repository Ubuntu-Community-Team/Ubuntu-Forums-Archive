---
title: "Problem with multiple NIC and Network setup. Not matched by other threads I think"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by frasch on 2007-03-10
've read several posts and howto's but nothing matched to my needs. Or in short I' am to stupid :) Maybe you could give me some advise

First my current network configuration

Notebook:
```

ifconfig -a

eth0      Protokoll:Ethernet  Hardware Adresse 00:16:36:AE:B6:E0  

          inet Adresse:192.168.0.8  Bcast:192.168.0.255  Maske:255.255.255.0

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          Kollisionen:0 Sendewarteschlangenlänge:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

          Interrupt:16 



eth1      Protokoll:Ethernet  Hardware Adresse 00:18:DE:9D:09:60  

          inet Adresse:192.168.0.10  Bcast:192.168.0.255  Maske:255.255.255.0

          inet6 Adresse: fe80::218:deff:fe9d:960/64 Gültigkeitsbereich:Verbindung

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:14744 errors:0 dropped:59 overruns:0 frame:0

          TX packets:13710 errors:0 dropped:0 overruns:0 carrier:0

          Kollisionen:0 Sendewarteschlangenlänge:1000 

          RX bytes:16192587 (15.4 MiB)  TX bytes:1575566 (1.5 MiB)

          Interrupt:21 Basisadresse:0x2000 Speicher:edf00000-edf00fff 



irda0     Protokoll:IrLAP  Hardware Adresse 00:00:00:00  

          NOARP  MTU:2048  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          Kollisionen:0 Sendewarteschlangenlänge:8 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



lo        Protokoll:Lokale Schleife  

          inet Adresse:127.0.0.1  Maske:255.0.0.0

          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:101 errors:0 dropped:0 overruns:0 frame:0

          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0

          Kollisionen:0 Sendewarteschlangenlänge:0 

          RX bytes:8177 (7.9 KiB)  TX bytes:8177 (7.9 KiB)


whereas eth1 is a wireless lan card.

netstat -r

Kernel IP Routentabelle

Ziel            Router          Genmask         Flags   MSS Fenster irtt Iface

192.168.0.0     *               255.255.255.0   U         0 0          0 eth1

192.168.0.0     *               255.255.255.0   U         0 0          0 eth0

link-local      *               255.255.0.0     U         0 0          0 eth0

default         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

default         192.168.0.1     0.0.0.0         UG        0 0          0 eth1


```


PC:
```

ifconfig -a

eth0      Protokoll:Ethernet  Hardware Adresse 00:50:8D:D7:C8:C8  

          inet Adresse:192.168.0.2  Bcast:192.168.0.255  Maske:255.255.255.0

          inet6 Adresse: fe80::250:8dff:fed7:c8c8/64 Gültigkeitsbereich:Verbindung

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:150 errors:0 dropped:0 overruns:0 frame:0

          TX packets:167 errors:0 dropped:0 overruns:0 carrier:0

          Kollisionen:0 Sendewarteschlangenlänge:1000 

          RX bytes:23073 (22.5 KiB)  TX bytes:19182 (18.7 KiB)

          Interrupt:18 



eth1      Protokoll:Ethernet  Hardware Adresse 00:40:F4:7B:B0:EE  

          inet Adresse:192.168.0.4  Bcast:192.168.0.255  Maske:255.255.255.0

          inet6 Adresse: fe80::240:f4ff:fe7b:b0ee/64 Gültigkeitsbereich:Verbindung

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:59 errors:0 dropped:0 overruns:0 frame:0

          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0

          Kollisionen:0 Sendewarteschlangenlänge:1000 

          RX bytes:7948 (7.7 KiB)  TX bytes:4153 (4.0 KiB)

          Interrupt:20 Basisadresse:0xa000 



lo        Protokoll:Lokale Schleife  

          inet Adresse:127.0.0.1  Maske:255.0.0.0

          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:66 errors:0 dropped:0 overruns:0 frame:0

          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0

          Kollisionen:0 Sendewarteschlangenlänge:0 

          RX bytes:5104 (4.9 KiB)  TX bytes:5104 (4.9 KiB)


netstat -r

Kernel IP Routentabelle

Ziel            Router          Genmask         Flags   MSS Fenster irtt Iface

192.168.0.0     *               255.255.255.0   U         0 0          0 eth0

192.168.0.0     *               255.255.255.0   U         0 0          0 eth1

link-local      *               255.255.0.0     U         0 0          0 eth0

default         192.168.0.1     0.0.0.0         UG        0 0          0 eth1

default         192.168.0.1     0.0.0.0         UG        0 0          0 eth0



```
For both the /etc/hosts

```

127.0.0.1 localhost

192.168.0.8 Newton
192.168.0.10 Keppler
192.168.0.2 Darwin
192.168.0.4 Gauss
192.168.0.3 Einstein


```

All Nic's are connected to a Netgear WGT 624 Router

My Problem:
I want to setup the network so that eth0 from the PC and the wireless network card (eth1) at the notebook is bind strictly to the internet (Firefox, Mail, etc). The other card of each PC, should only be bind to the local network (Samba, NFS, SSH) because of smoothing partition of bandwidth and security.

Here what I get so far:
Samba, SSH, NFS, is listen to eth1 at the PC and to eth0 (wired) at the notebook. But even when I want to access to shares via nautilus, nautilus displayed only the names Darwin instead of Gauss and Newton instead of Keppler. Furthermore, observing network traffic shows, that local and internet traffic is going via eth0 at the PC instead of one half each eth0 and eth1. The same is true dependent on whether the cable is connected or not at the notebook.

An additionally observance is that when the notebook is not connected to a Ethernet cable then the Name resolving is very very slow through I perform 
```

sudo ifdown eth0

```
Afterwards all is becoming normal even so If I perform
```

sudo ifup eth0

```
without being connected to a cable


Any suggestions??

I'm very glad to getting advice, suggestions or a lot of help

Thank you in advance

Frank

---

### Post by Mr. C. on 2007-03-10
You have all interfaces on the same network - this will not solve your needs.

You need to have one card from each system on one network, and the other two on another.  For example:

Network #1
192.168.0.0/24
eth0 PC
eth1 laptop
Internet route/Access Point

Network #2
10.0.0.0/24
eth1 PC
eth0 laptop
Switch

Network #2 will be a private network, and you can disable routing to ensure no traffic goes between Net1 and Net2

Make sense?
MrC

---

### Post by frasch on 2007-03-10
Yes, I think so. But is it necessary that the second network-address-range is connected to another switch or could the available Router (which is also a switch or not??) be used. And how I do disabling routing. Is it sufficient to delete the gateway-line in "interfaces" or must I delete the route via route --delete??

And do you know why nautilus only displayed the DNS-Name of the "first" NIC. Will this behaviour being changed when I following your advise, so that I could connect to the local network via the DNS-Name graphically. This will be ensure that novice user :) can connect to

Thanks for quick response

Frank

---

### Post by Mr. C. on 2007-03-10
You can attempt to use a cross-over cable to connect the Net2 NICs, however I never recommend such a solution because you will not get the highest performance possible, and is often problematic for many.  It might just work fine.

You cannot use the same commodity router to connect all the cables, because they do not provide a separation of what is called Broadcast Domains.  (Consider what happens  when a broadcast packet is sent over the wire - all stations in that broadcast domain receive the packet.)  Unless your router has VLAN support, you need two separate pieces of hardware (eg existing router, new switch).

The value in the virtual file /proc/sys/net/ipv4/ip_forward dictates whether ip packet fowarding is enabled.  If the value is 0, it is off, and packets will not be fowarded from one network to the other.
```

# cat /proc/sys/net/ipv4/ip_forward 
0
```

You need to have a default gateway to your broadband's interface for your Net1 to communicate to the internet.  Once you have your setup configured, you can look at 
```

netstat -rn
```

to see the routing table.   I will help you understand that if  you are interested, and/or you can read Week 6 "Routing" and the lab work here: [http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

About Nautilus, first I'll say that I don't use it (I'm a command line type).  Are you referring to  Go->Network.  Whatever it is, here's an explanation about hostnames and DNS.

A host only has one hostname.  A multihomed host (one with more than one interface) prsent the problem that a hostname no longer makes sense, as one name cannot refer to two interfaces.  Consider hostname and DNS names as distinct.  You can create DNS or /etc/host entries for each interface and all systems on those attached networks, and you can refer to those networks by those names.  Eg:
```

$ cat /etc/hosts
127.0.0.1      localhost
192.168.0.1  redned-gw
192.168.0.5  PC1
10.0.0.1       greennet-gw
10.0.0.5       PC2
```

MrC

---

### Post by frasch on 2007-03-10
Thank you very much Mr. C.. I've already start reading the recommended tutorial. That's help. So as I understand there is no way to implement two independent "networks" on one hardware host independently whether there are multiple NICs or not until there is a hardware router which is able to share Broadcast-Address-Ranges (VLAN = virtual lan???). Consequently, I can only create several ip-adresses bind to dns-names in /etc/host and give several instructions to services like samba or ssh to listen on a special ip-address.
Correct me please if I being wrong.

And yes you are right, I can access to the shares via the names given in /etc/hosts (See my first post) but I'am not able to do so graphically because only the host name defined for the first NIC is displayed at the "network-browser" (here Nautilus). Or is there any other possibility for "multihostname" to realise on one hardware host?? According to your post NO or I misunderstood

Consequently, I've to create links in the network-browser for mouse-orientated actions. (This is important, because I must given such a "possibility" to my girlfriend.

And a general question:
How will a complex network be realised, let us say, by people who conduct a apache server on a PC which is concurrently act as a normal pc. More illustrated, how can I conduct a network which can be accessed by the internet for data-transfer and simultaneously accomplish data-transfer within the local network without loosing performance? I know that seems to be a little bit obscure

I hope to hear about more salutary thinks from you. But again many thanks to Mr. C.

Frank

---

### Post by Mr. C. on 2007-03-10
Right - only one network per commodity (i.e. cheap) router.  Where would you put the second network mask?  There is no place in the router UI to allow a second netmask, or second set of IP's, right ?  You want that functionality, jump up to a Cisco or equivalent router.   They are 50-100 times more expensive than your commodity $50 switch!

If you can find an inexpensive VLAN switch, you can perform the task you indicate.  But it is MUCH cheaper to buy a simple switch; they can be purchased for something like $20-30US.

You have some confusion about hostnames and DNS.  You can place hostnames, really "interface names" inside /etc/hosts.  These are separate and distinct from DNS - they each are lookup table mechanisms.  You cannot simply add name/IP address pairs inside the hosts file and expect to have services listening on those interfaces.  The interfaces must exist, real or aliases.  But yes, you can request that a server such as postfix, apache, samba listen to only specific interfaces.

There is no "multihostname".  There is only a single hostname for a machine.    How you setup either or both of /etc/hosts or DNS is entirely your choice.  If you have a single network, and browse via Nautilus, as you do now, Nautilus can only see that single network.  If you add additional networks, then you should be able to select which network you are referring to.  Get your network cleared up, and then see how things are working.

I'm understanding your question about running a web server on a system to mean how will the web server impact performance when it is both used internally and externally.  Is this correct?  If so, it depends on how fast your server is.  With an even moderate PC running as a web server, it will most likely outperform any network you are likely to have.  Thus, simultaneous internal and external web clients won't be much of an impact.  If you expect thousands or hundreds of thousands of hits per hour, then dedicated hardware might be the best option.

MrC

---

### Post by frasch on 2007-03-10
Ok, your advise help me much. My intention is maybe to do complicated things on a easy way:) . But now, I understand and be willing to play around with this matter. I've a second switch lying around and will test.

But today, people (or only myself) will doing things solving flexible. That means for my case described here, I would take my notebook, sit down on my couch and using the wireless connection for both surfing at the net and doing network tasks. A moment later, I'm going to my home office plug a cable into the notebook and except that the wireless card is only addressed to the net  and the NIC to the local network:) :) :)  Do you know what I mean?

But seriously, thanks for your advise I will try and work it out and look how it works. The plan I've is to setup a network alike described so as to access from University my PC at home while my girlfriend is able to browse the local network without having trouble with performance or security issues. You might ask why to hell then this trouble about. The answer is I must understand things deeply before I use it.
If I run into trouble, I will be back here again and ask you for furthermore advice, if you don't object.
In the end I have to thank you again and wish you a very good night. So long 

Frank

PS: I think we should mark this thread for the time being as solved.

---

### Post by Mr. C. on 2007-03-10
Ok, sounds good Frank.  Go ahead and change to Solve if you want.

Best of luck!
MrC

---

### Post by Jichino on 2008-06-14
Say Frank, i know this thread is kinda old, but did you ever figure out how to get that setup working? I have basically the same network setup you have and i'm having some difficulty setting it up.

---

