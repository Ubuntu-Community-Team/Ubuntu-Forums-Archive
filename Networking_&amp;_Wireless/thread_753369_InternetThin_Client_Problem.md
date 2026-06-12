---
title: "Internet/Thin Client Problem"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by afrimax on 2008-04-12
Greetings:

After much effort, I finally got my thin client system up and running. However, in doing so I can no longer get on the internet. Here is the deal:

Did a fresh install of Edubuntu, using 192.168.0.254 as the eth0 static IP. Eth1 is set at .10. After some tinkering, the clients were able to log in just fine. However, the internet no longer worked on the server. I went to network tools and changed eth0 from static to local zero, and I was back on the internet, but the thin clients got booted. 

So, it appears I can either have a thin client network or go on the internet, but not both. I am on a laptop using the wireless network now. Obviously there is some conflict with the static settings.

Please help.

---

### Post by unutbu on 2008-04-12
Hello afrimax.
I am by no means an expert at networking (or anything else! :)), but since no one else has responded, I'll take a whack.

Your problem sounds like a problem with routing tables.
I don't know anything about setting up thin client networks, so here is my suggestion:

Get your thin client network running, and then issue this command on the server:

```
route
```

Then reconfigure your server so the server can reach the internet and again run
```
route
```

The route command should spit out a routing table -- a set of rules which it applies to each packet it receives and which reveals how the machine is deciding where to send each packet.

Post the results of both route commands here and perhaps I or someone more knowledgeable will be able to give you the right commands to get the network working right.

---

### Post by prshah on 2008-04-12
> **afrimax said:**
>  using 192.168.0.254 as the eth0 static IP. Eth1 is set at .10. After some tinkering, the clients were able to log in just fine. However, the internet no longer worked on the server. I went to network tools and changed eth0 from static to local zero, and I was back on the internet, 

If you are going with a static ip configuration, remember that you have to set up the DNS server information manually, ie, edit the /etc/resolv.conf and add your nameserver addresses (usually your router address or your ISP supplied DNS servers).

> 
Sun Apr 13 03:17:56 ~:$ cat /etc/resolv.conf
nameserver 192.168.1.1
Sun Apr 13 03:18:00 ~:$ 


---

### Post by dstew on 2008-04-12
> So, it appears I can either have a thin client network or go on the internet, but not both.I assume you are booting your thin client using DHCP and PXE BIOS. To do this, your netboot server needs to be a DHCP server. It will assign an internet address to your thin client. You have to let this DHCP server be the authoritative DHCP server on its network, and assign IP addresses to the other computers too. Make sure you disable the DHCP server in your router, if it is on the same network. The network should have only one DHCP server, so that conflicts do not occur. There is no essential conflict between using a DHCP server to act as the netboot server, and to assign IPs to the other non-PXE computers.

---

### Post by afrimax on 2008-04-13
ok, here is my route with the thin client operational:

Kernel IP routing table
Destination          Gateway       Genmask            Flags   Metric   Ref    Use  Iface
localnet               *                     255.255.255.0    U         0           0       0       eth0
locanet                *                     255.255.255.0    U         0           0      0        eth1
default                192.168.0.1    0                         UG      0           0       0       eth1
default                192.168.0.1    0                         UG      100       0        0      eth0

Here it is while on the internet- no thin client network- using zeroconf instead of static:
Kernel IP routing table
Destination          Gateway       Genmask            Flags   Metric   Ref    Use  Iface
localnet               *                     255.255.255.0    U         0           0       0       eth0
locanet                *                     255.255.255.0    U         0           0      0        eth1
default                192.168.0.1    0                         UG      0           0       0       eth1


Also, if I undo the DHCP on my router, does that mean I will no longer be able to log in using my off-thin client laptop? I will have to get a separate wireless router for those purposes?

thank you!

max

---

### Post by afrimax on 2008-04-13
I just turned off DHCP on the router and it had no impact. I still cannot get on the internet using the server. By the way, I am using a netgear router, which has always been very complicated, so I do not know if that is causing more problems.

Both eth0 and eth1 are static, at .254 and .10 respectively.

---

### Post by afrimax on 2008-04-13
Woo-hoo!

The problem lied in the DNS, not the DHCP.

Following the lead from another post, I went to
System --> Administrative --> Network

then selected the DNS tab. The DNS server was set to the router. I changed it to the static DNS IPs provided by my ISP and that did the trick.

Thank you all for your help!

---

