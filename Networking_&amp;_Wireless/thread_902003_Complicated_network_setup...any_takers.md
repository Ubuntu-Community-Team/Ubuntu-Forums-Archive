---
title: "Complicated network setup...any takers?"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by Marantz on 2008-08-26
Heres what I want...erm...need to accomplish here.

I have two network interfaces, eth0 and eth1

I have VirtualBox. I have an external IP and an internal IP.

Normally I run eth0 as my external set to 24.149.18.240 and eth1 as my internal set to 192.168.11.170.

I have eth1 bridged to br0 and tap0 to allow VirtualBox to join the domain on the internal network.

Heres the problem I have run into... I can't connect to FTP servers now... Yeah go figure. I can connect to everything else no problem, just can't get port 21 to do anything. Whats the deal? What should I do?

I also notice that Ubuntu tries to use eth1(br0) sometimes for internet and runs into issues....can I force Ubuntu to only use eth0 for all its network traffic and only allow VirtualBox to use eth1(br0 tap0) so that this confusion stops?

---

### Post by mrsteveman1 on 2008-08-26
That's not too complex really.

Ok, FTP connections to where? To the internet from another LAN machine? To the internet from the one in the middle of it all? 

Also what makes you say that ubuntu tries to use br0 for internet connections?

If the routes are all set correctly and there is a default route to a machine that is on the eth0 network, it should all work fine.

Post the output of the route command.

EDIT: heres a sketch, right?

[http://i141.photobucket.com/albums/r65/mrsteveman1/Untitled-1.png]("http://i141.photobucket.com/albums/r65/mrsteveman1/Untitled-1.png")

---

### Post by Marantz on 2008-08-27
> **mrsteveman1 said:**
> That's not too complex really.

Ok, FTP connections to where? To the internet from another LAN machine? To the internet from the one in the middle of it all? 

Also what makes you say that ubuntu tries to use br0 for internet connections?

If the routes are all set correctly and there is a default route to a machine that is on the eth0 network, it should all work fine.

Post the output of the route command.

EDIT: heres a sketch, right?

[http://i141.photobucket.com/albums/r65/mrsteveman1/Untitled-1.png]("http://i141.photobucket.com/albums/r65/mrsteveman1/Untitled-1.png")

Sorry...let me try to map this out a bit more clearly...


eth0 is setup as follows 

```

eth0      Link encap:Ethernet  HWaddr 00:18:f3:65:08:44  
          inet addr:24.149.18.240  Bcast:24.149.18.255  Mask:255.255.255.128
          inet6 addr: fe80::218:f3ff:fe65:844/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:742603 errors:0 dropped:0 overruns:0 frame:0
          TX packets:356172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:724390551 (690.8 MB)  TX bytes:26816153 (25.5 MB)
          Interrupt:216 Base address:0x8000 

```

br0 is


```

br0       Link encap:Ethernet  HWaddr 00:18:f3:65:0e:86  
          inet addr:192.168.11.170  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe65:e86/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5626 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1014 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:359563 (351.1 KB)  TX bytes:96735 (94.4 KB)

```

br0 is eth1, the internal network that also has external access. Ubuntu seems to choose to route all the internet traffic through eth1 and just kinda lets eth0 sit. I can tell this by websites reporting my IP as 24.149.18.235, the router internal, instead of 24.149.18.240.

This is also causing a problem with a game that runs with Wine. If it attempts to connect to the gameserver through the internal router it will report it cannot connect, but if I disable eth1 and br0 it will connect through eth0 just fine.

route is

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
24.149.18.128   *               255.255.255.128 U     0      0        0 eth0
192.168.11.0    *               255.255.255.0   U     0      0        0 br0
link-local      *               255.255.0.0     U     1000   0        0 eth0

```



FTP is running in the VirtualBox attempting to connect out of br0 to digitallyevolved.net and won't connect. It won't connect in Linux either until I disable br0 and tap0 and eth1.

---

### Post by mrsteveman1 on 2008-08-27
So you have more than one public IP? Is all internet access supposed to go through this box? In otherwords you don't have another router and another cable modem etc.

I do notice there's no default route listed there.

By all means if you want to draw a diagram on a napkin, go ahead :D

I think i got what you mean though.

---

### Post by Marantz on 2008-08-27
> **mrsteveman1 said:**
> So you have more than one public IP? Is all internet access supposed to go through this box? In otherwords you don't have another router and another cable modem etc.

I do notice there's no default route listed there.

By all means if you want to draw a diagram on a napkin, go ahead :D

I think i got what you mean though.

Nobody connects through my box for internet.

MSPAINT TIME!!

Does that help?

---

### Post by mrsteveman1 on 2008-08-28
ok so you do have 2 public IPs. hmmm

Again you don't have any default route in that routing table you listed. Do you know what the default route is for that ISP?

Also do you actually have 2 cable modems or is there just a switch connecting everything to the cable modem.

---

### Post by Marantz on 2008-08-28
> **mrsteveman1 said:**
> ok so you do have 2 public IPs. hmmm

Again you don't have any default route in that routing table you listed. Do you know what the default route is for that ISP?

Also do you actually have 2 cable modems or is there just a switch connecting everything to the cable modem.

There is just a switch connecting everything to the cable modem. I guess I should have thrown that in.


Honestly now though, I don't even need this setup anymore as I was fired from the job hahaha. Long story short, I moved my boss's chair, and he got mad, and took my keys and told me to take my stuff and leave. So we can pretty much can this thread, but can I PM you later about another issue I'm having with something networking wise?

---

### Post by mrsteveman1 on 2008-08-28
Sure :D

In the meantime though, i believe your issue is as follows:

Both of your public IPs are on the same subnet (otherwise the switch wouldn't work to connect everything or at least would be functioning in an abnormal fashion unless VLANs were involved).

Because of this, whenever that box needs to send packets to the ISPs gateway, it has 2 valid choices. It can either send them out eth0 which is directly connected to the subnet the gateway is on, or it can go through the router which is also directly connected to that subnet just using a different IP.

I would bet that the machine was using the linksys as the default route (esp if DHCP is involved).

Anyway for future reference for anyone reading this, Linux and most other systems will follow a logical set of things to check when sending packets to the internet or anywhere else:

Is the destination IP on a subnet for which i have a directly connected interface? 

If not do i have a static route to the subnet on which that destination IP resides? 

If no static route do i have a default gateway set in the routing table? 

If none of those things are true, the packet can't get anywhere. The default route though in most cases determines what interface your traffic will go over.

---

