---
title: "2 NICs - how to distinguish?"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by jabooty on 2007-03-05
My machine has two network cards.  One runs to a router and is part of one network, while the other is connected directly to the ol' internet (don't ask why... it's all because of my university... long story).

My question is, Ubuntu does a good job of eventually recognizing where everything goes, but when I first start up my computer, it doesn't like to recognize the outside connection, only the connection running to the router.

Is there any way to change some settings around so that, at startup, ubuntu will recognize both the internal network connection as well as the external connection without me having to wait 5-10 minutes for it to figure it out on its own?

---

### Post by Mr. C. on 2007-03-06
I'm confused - your Subject asked about differentiating between the two NICs.  But, your question here asks about what is causing a delay.

We'll need much more information that you've provided.

How about 

$ ifconfig -a

What type of network connection, configurations, which NIC is LAN, which is the WAN, etc.

Help us help you,
MrC

---

### Post by netztier on 2007-03-06
> **jabooty said:**
> My question is, Ubuntu does a good job of eventually recognizing where everything goes, but when I first start up my computer, it doesn't like to recognize the outside connection, only the connection running to the router.

If there's confusion between **eth0** and **eth1** (or any other number), you might want to start by assigning a ethX name to each interface (resp it's MAC address). Edit the **/etc/iftab** file to look something like this.

```

[FONT="Courier New"]marc@blaze:/etc$ more iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

# eth0 mac 00:04:75:d6:fe:1b arp 1
eth0 mac 00:A0:C9:98:82:0E arp 1
eth1 mac 00:50:8B:07:E9:83 arp 1
[/FONT]
```

You'll need to fill in ethX names and MAC addresses to match your preference and hardware, of course. To find out the MAC addresses of your NICs, you can use this command (for example, as there's other ways, too): **dmesg | grep eth**

```
[FONT="Courier New"]marc@blaze:/etc$ **dmesg | grep eth**
[42949396.490000] e100: eth0: e100_probe: addr 0xe4203000, irq 10, MAC addr 00:A0:C9:98:82:0E
[42949396.510000] e100: eth1: e100_probe: addr 0xe4200000, irq 12, MAC addr 00:50:8B:07:E9:83
[/FONT]
```

This may not actually cure the timeouts you are experiencing, but when running multiple interfaces, it's not a bad idea anyway. And as Mr. C. suggested, please provide us with a bit more information about your network setup: Interfaces and links, IP addressing, kind of Internet connection etc.

best regards

Marc

---

### Post by jabooty on 2007-03-06
Sorry for the confusion.  I'll try to explain a little better.

I have two ethernet cards in my machine.

eth0 runs to a router with no outside connection, it's just an internal network.  IP on that NIC is 192.168.1.10

eth1 runs straight into my wall outlet to the school's WAN, which I have no control over.  It has a separate IP address of 192.237.55.37

On startup Ubuntu does a wonderful job of getting the IP addresses for each NIC.  The problem, however, is that Ubuntu can't seem to figure out how to direct traffic properly.  When I open firefox, gaim, or any other program needing a connection to the internet, it seems as though Ubuntu is trying to route it through my internal network and not my school's WAN.  Eventually (after 5-10 minutes) everything gets sorted out and traffic starts being directed properly.

Does that make more sense?  I don't know the technical stuff all that well, so it's hard for me to put this into jargon that everyone can understand.  It makes perfect sense in MY head! LOL

---

### Post by Mr. C. on 2007-03-06
Yes, makes sense.  You have a routing or network configuration problem.

Show your network parameters for each network

ifconfig -a

Show your route table

route (or netstat -r)

Your router at the end of you 192.168.1/24 network.  I presume you have it because you have other systems connected to that network.  If so, it needs to be told how to reach the internet and your ubuntu stations needs to be configured correctly as a router.  It has to route from the 192.168.1/24 network to your eth1 network 192.237.55.37 (i don't know what your netmask is there, so don't know how large this network is).

I also need to see how you have your router configured.  You need to tell it that there are other routers on your LAN.

MrC

---

### Post by jabooty on 2007-03-07
```
eth0      Link encap:Ethernet  HWaddr 00:01:29:15:C7:27  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:29ff:fe15:c727/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2871604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2768983 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1250678672 (1.1 GiB)  TX bytes:490892304 (468.1 MiB)
          Interrupt:217 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:01:29:16:28:CF  
          inet addr:129.237.55.37  Bcast:129.237.55.255  Mask:255.255.252.0
          inet6 addr: 2002:81ed:34c3:5:201:29ff:fe16:28cf/64 Scope:Global
          inet6 addr: fec0::5:201:29ff:fe16:28cf/64 Scope:Site
          inet6 addr: fe80::201:29ff:fe16:28cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2769584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:390324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:667670921 (636.7 MiB)  TX bytes:49907421 (47.5 MiB)
          Interrupt:66 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:996 (996.0 b)  TX bytes:996 (996.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
129.237.52.0    *               255.255.252.0   U         0 0          0 eth1
default         129.237.55.254  0.0.0.0         UG        0 0          0 eth1
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

```

eth0 is connected to a router that has absolutely no outside connectivity.  It just connects this computer, my file server computer, and my xbox.  

eth1 is connected to the internet via my school's network.  I just plug into the wall and have absolutely no way of changing settings or anything there.

---

### Post by Mr. C. on 2007-03-08
```
default         129.237.55.254  0.0.0.0         UG        0 0          0 eth1
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
```

Your system has two default routes.  This is not usable.  If you want all machines to be able to access the internet, you need to remove the 192.168.1.1 route.

This configuration is telling the system is should forward traffic to two different networks when the traffic is not local to either network.

I presume your eth0 interface is getting its IP automatically via DHCP.  If so, change it to be a static IP, and assign it an IP outside the range of IPs your router provides via DHCP.  Be sure your static IP, netmask, and broadcast address are correct for the 192.168.1.0/24 network.

Once you've done this, your system will no longer place two default routes into the routing table.

Try a reboot, and you'll see it should just work.
Do you know hot to configure a static IP on your system, and ensure that you do not use one of the DHCP-reserved IPs from your router?

MrC

---

### Post by jabooty on 2007-03-08
No, I don't know how to set a static IP on my machine.  

Let me see if I get this straight, though.  I should assign a static IP to the NIC going to the router, but make it outside the range given by the DCHP server?  So I'd have to set a static IP based on this machine's MAC address or something?

---

### Post by Mr. C. on 2007-03-08
Partly correct.

To configure the static IP, go to:

System->Administration->Networking

Select the wired connection that refers to your LAN (your eth0) connection, and click Properties.

Change the configuration to "Static IP Address", and enter your chosen 192.168.1.X IP address, where you've selected X, such that 192.168.1.X is outside the DHCP addresses.  See below for determining X.

Set the Subnet mask to 255.255.255.0 and Broadcast to 192.168.1.255.  Set the gateway address to be 129.237.55.254, and click Ok.

You don't need to worry about MAC addresses - just connect to your router via its web interface, and find the DHCP enable and/or config section.  There will be something that allows you to change either the entire range, or the high end of a range.

Give yourself perhaps 20 DHCP addresses, or whatever you think you'll need, and then pick an IP above that (say, from 192.168.1.21 to 192.168.1.254).  You can't use the .255 address, because that's the broadcast address mentioned above.

Thats it.
MrC

---

### Post by jabooty on 2007-03-08
```
eth0      Link encap:Ethernet  HWaddr 00:01:29:15:C7:27  
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:29ff:fe15:c727/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3401720 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3305352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1405100287 (1.3 GiB)  TX bytes:588833277 (561.5 MiB)
          Interrupt:217 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:01:29:16:28:CF  
          inet addr:129.237.55.37  Bcast:129.237.55.255  Mask:255.255.252.0
          inet6 addr: 2002:81ed:34c3:5:201:29ff:fe16:28cf/64 Scope:Global
          inet6 addr: fec0::5:201:29ff:fe16:28cf/64 Scope:Site
          inet6 addr: fe80::201:29ff:fe16:28cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3328645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:675395 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:822208031 (784.1 MiB)  TX bytes:77022044 (73.4 MiB)
          Interrupt:66 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5107 (4.9 KiB)  TX bytes:5107 (4.9 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
129.237.52.0    *               255.255.252.0   U         0 0          0 eth1
default         129.237.55.254  0.0.0.0         UG        0 0          0 eth1

```

That's how it looks now.  Better?

---

### Post by Mr. C. on 2007-03-08
Looks great - how's it working ?

MrC

---

### Post by jabooty on 2007-03-10
Works like a charm!  Thanks so much!

---

### Post by Mr. C. on 2007-03-10
Fantastic!

I'm been meaning to ask: does your "jabooty" moniker have any relation to Djibouti?

MrC

---

### Post by jabooty on 2007-03-10
You know, I dreally don't know.  When I was much younger, I was watching Saturday Night Live and heard someone say something that sounded like "Jabooty" in a really funny sketch.  At the time I had never even heard of Djibouti.  The word (and my interpretation of the spelling) stuck in my head for years, and one day when trying to come up with a username (and consequently, domain name), this word came up again.

Long story short - it might have something to do with it, but not intentionally :)

---

