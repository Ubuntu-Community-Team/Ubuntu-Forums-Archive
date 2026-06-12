---
title: "Serial connection between Ubuntu and other Debian-type os"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by steve196 on 2007-03-08
I want to make a connection with a serial ("null modem") cable between a desktop running ubuntu and a laptop running "damn small linux". I want to be able to do at least one of two things:
1.) access the file system of the laptop from the desktop
2.) make the desktop provide internet access for the laptop
I have no idea, how to use serial cables in linux.
Any help is appreciated.

---

### Post by Mr. C. on 2007-03-08
Over a serial cable?  That's going to be pretty tough with today's bandwidth hungry apps and bulking content!

You want SLIP - serial line IP.  Its a pain, but you'll find some info with that to start off.

MrC

---

### Post by steve196 on 2007-03-10
Thanks!
The laptop proudly wears a "designed for Windows 95" sticker and is basically a writing machine, so no bandwidth hungry apps there.
I found [http://tldp.org/HOWTO/PPP-HOWTO/direct.html](http://tldp.org/HOWTO/PPP-HOWTO/direct.html) , which seems to describe the internet access through the desktop part. My question for this is, what ip adresses do i use? Do i just randomly choose them? 
The other question is, how do i give the desktop read and write access to the laptop without any risk of also giving it to other computers?

---

### Post by steve196 on 2007-03-10
What does that mean?

pppd: The remote system is required to authenticate itself
pppd: but I couldn't find any suitable secret (password) for it to use to do so.
[1]+  Exit 1                  pppd -detach crtscts lock 10.0.0.1:10.0.0.2 /dev/ttyS0 38400

---

### Post by Mr. C. on 2007-03-10
I believe that pppd requires its peer (other system) to authenticate, by default.  There as a **noauth **setting in pppd.conf.  Just set that and restart pppd.

man pppd.conf

MrC

---

### Post by steve196 on 2007-03-10
On my system neither pppd.conf nor its manpage exists. However I took your suggestion and wrote "noauth" into the command line. Now the command executes without the error, but still the machines cannot ping each other or do anything else.

---

### Post by Mr. C. on 2007-03-10
> **steve196 said:**
> TMy question for this is, what ip adresses do i use? Do i just randomly choose them? 
The other question is, how do i give the desktop read and write access to the laptop without any risk of also giving it to other computers?

Steve, I'm sorry, I didn't notice these two questions in the back-to-back posting.

Because the serial line interface only has two nodes (the two peers), you can assign any IP you want, but both ends must be in the same network (eg. 10.1.0.0 and 10.2.0.0 netmask 255.0.0.0).  I've just picked the 10/8 network as an example, but you can use what you desire.  Don't let that network conflict with others you already have; the networks are separate networks.

show the status of the network with :

ipconfig -a
netstat -rn

We'll get to the desktop sharing question after this is done.
MrC

---

### Post by steve196 on 2007-03-10
Thank you!
The last mistake was using ttyS0 instead of ttyS1. Now the two computers can ping each other, but cannot yet do anything else.

---

### Post by Mr. C. on 2007-03-10
Great!  Ping is the first hurdle.

If you need more help, don't hesitate to ask!

MrC

---

### Post by steve196 on 2007-03-11
I need several things:
On the desktop: offering an internet proxy to 10.0.0.2 but not to anyone else
On the laptop: offering full rw ftp access to 10.0.0.1 but not to anyone else, specifying a nameserver, using the desktop as proxy.

---

### Post by steve196 on 2007-03-11
got ftp access, through ssh, but in a way, that would not prevent other computers from using it if they were reachable.

---

### Post by Mr. C. on 2007-03-11
1) You need to configure the desktop to route packets from your PPP network to the internet.  Let's see your route table and interface info:
```

netstat -rn
fconfig -a
```

I'm confused about your setup.  I assume your desktop has 1 NIC, going to a router or your broadband.  And one serial connection to the laptop.  This setup implies that "others" are connected directly to the router.

Please clarify.
MrC

---

### Post by steve196 on 2007-03-11
I have the serial cable to the laptop and i have a lan connection to a cable modem. The thing with other computers is no problem now, but would be if i successfully gave the laptop indirect internet access.  

[me]@ubuntu:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.0.2        0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
[censored].0    0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         [censored].1    0.0.0.0         UG        0 0          0 eth1
[me]@ubuntu:~$ fconfig -a
bash: fconfig: command not found
[me]@ubuntu:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr [censored]
          inet addr:[censored]  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: [censored] Scope:Link
          UP BROADCAST NOTRAILERS RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:748781 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16859 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:60252364 (57.4 MiB)  TX bytes:2670312 (2.5 MiB)
          Interrupt:10 Base address:0xcf00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:126810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9919484 (9.4 MiB)  TX bytes:9919484 (9.4 MiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:10.0.0.1  P-t-P:10.0.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:35324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:47257688 (45.0 MiB)  TX bytes:1956562 (1.8 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Mr. C. on 2007-03-11
> **steve196 said:**
> ... but would be if i successfully gave the laptop indirect internet access.  

... but how can I give you advice and directions, not knowing how you plan to configure your future setup?

You *can* do what you want, but how you implement it depends very much on what your setup will be.

For example, there is *nothing* your desktop can do to prevent other stations from browsing the internet should you connect them to a router that goes directly to the internet.  Your desktop will never see a byte of their traffic.

MrC

---

### Post by steve196 on 2007-03-11
Setup is:
laptop <> nullmodem cable <> desktop <> ethernet cable <> cable modem <> internet.
No other connections exist.
Main questions are: 
1.) How can i give the laptop internet connection through this?
2.) Once i gave the laptop internet connection, how can i prevent it from offering ssh to anyone except the desktop computer, while i am copying files?

---

