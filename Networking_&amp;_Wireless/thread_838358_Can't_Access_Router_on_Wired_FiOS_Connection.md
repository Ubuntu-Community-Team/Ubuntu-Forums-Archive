---
title: "Can't Access Router on Wired FiOS Connection"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by corngeek on 2008-06-23
Hi.

After returning from vacation yesterday, I started to get my unplugged computer up and running again. After it got up, I realized something had gone wrong with the internet connection.

My problem: There's several symptoms, actually, but I am sure they all are related to one problem. I cannot access any webpage (tried Google, Slashdot, etc.) nor can I access the router (192.168.1.1). Also, when I use the Network Tools and press "configure" on eth0, it returns "The interface does not exist". I have found remedies for that online, but haven't followed up on them since I know that's not the root of my problem. KNetworkManager says that there is no active device when I set the connection to a static IP, but when I switch it to be DHCP allocated, it pops up with the interface info (still get a "does not exist" error in Network Tools, however). 

Normally, I would think it was a router issue. But, the other two computers on the network are working fine. I tested the laptop on the same ethernet cable into the same jack and it worked fine. So, I was led to believe it's something with my configuration. I have a Kubuntu/WinXP dual boot, and it doesn't work in Windows *either*. That leads me to believe it's something with my ethernet card.

Also, I can ping the router from the computer in question. But, it usually results in a 50-75% packet return rate. Same with a website. I can ping Google, and it resolves the DNS name (so it's not an issue with that) but only a portion of packets are returned. 

Some more mucking around leads me to the router logfile. It gives this error repeatedly (presumably every time the computer in question requests information from the net):
```
First packet in connection is not a SYN packet: TCP 192.168.1.2:1179->xx.xx.xxx.xxx:5190 on clink0
```
I have just a cursory knowledge of networking, enough to know what a SYN packet is, but have no idea how to remedy this problem. 

I've tried everything I can think of on both OS's. I unplugged the ethernet cable before I left on the trip (at least, I'm pretty sure I did) so the computer had no access to the power grid, making it safe from a surge (right?). I have no idea how all of these problems are related, but I'm sure there's some small technological nuance at work. I'm led to believe that this problem is mostly a hardware issue. I'm reluctant to disconnect the box and take it apart though, because it's pretty inconvenient. I have a USB-Ethernet adapter somewhere around here, but I don't know how much configuring I would have to do to get something like that working under Linux. So, what do you think? Something happened to my ethernet card while it was sitting dormant for a week? Or is it some shared configuration issue between Windows and Linux? 

My router is one of the newer FiOS routers, and I have an onboard nVidia ethernet (which is enabled in the BIOS). 

I'm completely at a loss as to what to do, short of replacing the ethernet card. Does the community have any ideas as to what's going on here?

Thanks.

---

### Post by corngeek on 2008-06-23
Bump?

---

### Post by RichieV on 2008-06-24
Have you tried restarting the router?  I have an actiontec router from Verizon, and for some reason, it will periodically fail to give my devices an ip address.  It happens about once a month to my devices which are repeatedly turned on and off (Xbox one and Xbox 360).

---

### Post by jmagsho on 2008-07-16
I ended up replacing the router I got from Verizon after about a year.  The wireless functions would work okay, but I could not get the thing to route properly when using hardwired ethernet connections.

However, it sounds like you may be correct in assuming that it is a hardware issue - have you tried the other network card yet?

---

