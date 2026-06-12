---
title: "Dual NICs - two switches - best practice?"
date: 2016-06-14
forum: Networking &amp; Wireless
---

### Post by Roasted on 2016-06-14
Hi friends. I'm trying to map out some ideas here and I'm hitting a wall. Curious if you folks could advise.

I have one Ubuntu 14.04 server. I have two network switches. One is a 24 port "main" LAN gigabit switch and the other is an 8 port POE gigabit switch. The POE switch powers some surveillance cameras, which route back in to the server.

The server has two NICs. Ideally, I'd like to use each NIC for each switch. Neither switch has VLAN support, but I got to thinking perhaps the physical differences would help achieve a segregation of traffic. I'd like to keep the video traffic predominantly on the POE switch, leaving the 24 port switch available to do everything else on the LAN. Likewise, if backups or something kick in, they'd be hitting a totally different NIC on the server (including different HDDs inside).

Right now my first NIC is 192.168.1.200, 255.255.255.0. My second NIC I'd like to IP as 192.168.2.200. This would also suggest I would static IP the cameras to 192.168.2.x addressing. I know the cameras would communicate to the server if I did this, but I am doubtful the cameras would be accessible on the network otherwise for configuration changes in their web interfaces.

Would I be able to drop my subnet from 255.255.255.0 to 255.255.0.0 to help the two networks (1.x and 2.x) to communicate? Would that allow me to be on, say, 192.168.1.17 and pull up the web UI for a camera on 192.168.2.221? 

In short, I want my full time video surveillance recordings to route over the POE switch to a dedicated NIC (NIC #2) on the server. Yet if I run backups, if I stream movies from the server, if I save files to the server, I would like that traffic to get passed through NIC #1. At the same token, I want to be on my wireless laptop and pull up the web interface of a camera if need be.

What's my best course of action? Readjusting my network settings, i.e. subnet mask, etc? Setting up a proxy between the two NICs?

---

### Post by SeijiSensei on 2016-06-14
Enable packet forwarding in /etc/sysctl.conf by removing the hash mark from the line
```
net.ipv4.ip_forward=1
```
and reboot.  If the server is the default gateway on both networks, you should be able to see the cameras.

If the server is not the default gateway, then you need to add a static route to the router that handles traffic for the LAN for the 192.168.2.0/24 network using the LAN-side server's address as its gateway.

---

### Post by SeijiSensei on 2016-06-14
Enable packet forwarding in /etc/sysctl.conf by removing the hash mark from the line
```
net.ipv4.ip_forward=1
```
and reboot.  If the server is the default gateway on both networks, you should be able to see the cameras.

If the server is not the default gateway, then you need to add a static route to the router that handles traffic for the LAN for the 192.168.2.0/24 network using the LAN-side server's address as its gateway.  If the router were a Linux box, the route would be
```
ip route add 192.168.2.0/24 via 192.168.1.200
```
Adapt as necessary to your router's configuration.

---

### Post by Roasted on 2016-06-14
> **SeijiSensei said:**
> Enable packet forwarding in /etc/sysctl.conf by removing the hash mark from the line
```
net.ipv4.ip_forward=1
```
and reboot.  If the server is the default gateway on both networks, you should be able to see the cameras.

If the server is not the default gateway, then you need to add a static route to the router that handles traffic for the LAN for the 192.168.2.0/24 network using the LAN-side server's address as its gateway.

The server is not the gateway to the network. I have a simple Netgear home router. Is packet forwarding all that's needed? I thought I'd have to configure NIC A (192.168.1.x) and NIC B (192.168.2.x) to somehow communicate with one another. In my mind I can't envision how the 192.168.2.x traffic would reach the router/gateway otherwise (which is the goal so I can make web UI config changes to devices on 192.168.2.x while being on a system on 192.168.1.x)

Thanks for your help!

---

### Post by SeijiSensei on 2016-06-14
You'll need to add a static route like the one I described to the Netgear router.  Because the Netgear is the default gateway for the LAN, traffic for 192.168.2.0/24 will be sent to it.  If it has a static route for that network, with 192.168.1.200 as its gateway, traffic for that subnet will be forwarded to the server.

I presume the cameras all have 192.168.2.200 as their default gateway.

---

### Post by Roasted on 2016-06-14
> **SeijiSensei said:**
> You'll need to add a static route like the one I described to the Netgear router.  Because the Netgear is the default gateway for the LAN, traffic for 192.168.2.0/24 will be sent to it.  If it has a static route for that network, with 192.168.1.200 as its gateway, traffic for that subnet will be forwarded to the server.

I presume the cameras all have 192.168.2.200 as their default gateway.

This also assumes that the two switches in question are physically linked/connected, yes?

Originally I set things up to be split. That way the video stuff kind of "stays over there" but hits the same box as, well, everything else storage-wise. That way I could just play back feeds when necessary. At the time, this required no linking of the POE switch to the rest of the network.

It was previously laid out just like this:

Router >> 24 port main switch >> NIC A of server... then NIC B of server >> 8 port POE switch. As a result the POE switch had no idea of anything else on the LAN; the router, the 24 port switch, etc.

This worked out great but being able to configure the cameras when necessary instead of setting a static IP and hooking into the POE switch would be nice.

Anyway, just some quick back story. Guess that was clouding my understanding a bit as I read through the response. ;)

---

### Post by The Cog on 2016-06-14
> Would I be able to drop my subnet from 255.255.255.0 to 255.255.0.0 to help the two networks (1.x and 2.x) to communicate?
Trying that would lead to all sorts of problems. 

> This also assumes that the two switches in question are physically linked/connected, yes?
No. No need to connect the switches together.

SeijiSensei is right in all he says. The cameras need to have 192.168.2.x addresses and 192.168.2.200  (the server) as their default gateway. This means they will send anything destined outside of 192.168.2.x to the server (which will forward it on). I don't know how you configure the cameras initially though.

On the main LAN, all the PCs will have the NetGear as their default gateway. This means that all traffic they want to send outside of 192.168.1.x will go to the netgear router. Placing a "static route" in the netgear can tell it that it should reach 192.168.2.x via 192.168.1.200 (the server) instead of its default via the internet, and it will redirect all traffic for the cameras to the server instead. The server will then forward the traffic to the right camera. Hope this helps.

---

### Post by Roasted on 2016-06-14
> **The Cog said:**
> On the main LAN, all the PCs will have the NetGear as their default gateway. This means that all traffic they want to send outside of 192.168.1.x will go to the netgear router. Placing a "static route" in the netgear can tell it that it should reach 192.168.2.x via 192.168.1.200 (the server) instead of its default via the internet, and it will redirect all traffic for the cameras to the server instead. The server will then forward the traffic to the right camera. Hope this helps.

Hearing the same response articulated in two different ways kind of resonated with me... so I think I got the jist of it. I'll have to look in the router config to see what route options there are. Nothing comes to memory, but I've never searched for it, so there's that.

I suppose in the end, this keeps video stuff on video(POE) switch, yet if I call a camera's web UI at, say, 192.168.2.221, it should show up. Fancy.

P.S. - This assumes I'm leaving the subnet entirely alone, yes?

Thanks for your help folks. I'll take a closer look this evening!

---

### Post by SeijiSensei on 2016-06-14
[http://kb.netgear.com/app/answers/detail/a_id/24322/~/how-do-i-set-or-edit-static-routes-on-a-netgear-router%3F](http://kb.netgear.com/app/answers/detail/a_id/24322/~/how-do-i-set-or-edit-static-routes-on-a-netgear-router%3F)

---

### Post by Roasted on 2016-06-14
Quick question. I'm doing something wrong, and I'm sure it's simple.

For the 192.168.2.X network with the 2nd NIC in the server, what should that look like with the interfaces file? I assume it needs a gateway - but which? Am I just using 192.168.2.200? I tried a few combinations, but so far the best I can get is the server can ping a camera, but from my laptop (192.168.1.x network) I cannot. I know it's something with my NIC #2 configuration, or the static route in the router UI...

```
administrator@vault:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.2.200   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 p5p1
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0

```

```
administrator@vault:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto p5p1
iface p5p1 inet dhcp

# The network interface for CCTV
auto eth0
iface eth0 inet static
address 192.168.2.200
netmask 255.255.255.0
gateway 192.168.2.200

```

Router screenshot: [http://i.imgur.com/PifSiPJ.png](http://i.imgur.com/PifSiPJ.png)
(note: the destination IP, regardless of what I put in, defaults the last octet to 0)

---

### Post by SeijiSensei on 2016-06-14
No, there should be only one default gateway, on the Netgear side.  Delete the "gateway" directive for eth0.

The default gateway handles traffic for which there is no established route.  Traffic on the camera side will use Ethernet broadcasts to pass traffic around rather than routing.  The default gateway only comes into play for traffic on neither network, like traffic headed out to the Internet.  For that you want the Netgear to handle the routing.

---

### Post by Roasted on 2016-06-14
> **SeijiSensei said:**
> No, there should be only one default gateway, on the Netgear side.  Delete the "gateway" directive for eth0.

The default gateway handles traffic for which there is no established route.  Traffic on the camera side will use Ethernet broadcasts to pass traffic around rather than routing.  The default gateway only comes into play for traffic on neither network, like traffic headed out to the Internet.  For that you want the Netgear to handle the routing.

Hmm. Unless there's another config somewhere I goofed, I'm a little unsure where the issue lies.

From laptop on 192.168.1.3:
```
jason@mobile-hq1:~$ ping 192.168.2.203
PING 192.168.2.203 (192.168.2.203) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=3 Destination Host Unreachable
From 192.168.1.1 icmp_seq=6 Destination Host Unreachable
From 192.168.1.1 icmp_seq=9 Destination Host Unreachable

```

From server over SSH (ssh'd into 192.168.1.200):
```
root@vault:/home/administrator# ping 192.168.2.203
PING 192.168.2.203 (192.168.2.203) 56(84) bytes of data.
64 bytes from 192.168.2.203: icmp_seq=1 ttl=64 time=0.298 ms
64 bytes from 192.168.2.203: icmp_seq=2 ttl=64 time=0.282 ms
64 bytes from 192.168.2.203: icmp_seq=3 ttl=64 time=0.276 ms

```

So server can ping the 2.203 camera, but laptop cannot. (not surprising)

/etc/network/interfaces file from server:
```
root@vault:/home/administrator# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto p5p1
iface p5p1 inet dhcp

# The network interface for CCTV
auto eth0
iface eth0 inet static
address 192.168.2.200
netmask 255.255.255.0

```

Then of course the router screenshot from earlier:
[http://i.imgur.com/PifSiPJ.png](http://i.imgur.com/PifSiPJ.png)

Not seeing where my hangup is...?

---

### Post by Roasted on 2016-06-14
Well, I think I worked around it. Or maybe what I was doing above was working around it? I read some documentation online about bridging network adapters. Some sources lead me to believe it might be the preferred way to go for what I was looking to do. I set it up in a hot second and did a few tests of my own. Everything works as I'd want it to. Likewise, if I boot up the server with NIC A disconnected, the video recording still takes over issue free since everything is a static IP (the bridged NIC + each camera). So even with the main network out of the loop, it still does its job.

Judging by the connectivity lights it seems as if its the NIC B (the one I wanted) getting hammered by the video bandwidth, leaving the main NIC alone.

Everything is on a 192.168.1.x network now, so there's no subnetting or additional hoops to jump through.

Couple configs for those future Googlers and those curious:
(as you can see, most of this config is commented out. Relevant parts at the bottom)
```
administrator@vault:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto p5p1
#iface p5p1 inet dhcp

# The network interface for CCTV
#auto eth0
#iface eth0 inet static
#address 192.168.2.200
#netmask 255.255.255.0

# Bridged network adapter for main interface and CCTV interface
auto br0
iface br0 inet static
	address 192.168.1.200
	netmask 255.255.255.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	dns-nameservers 192.168.1.1
	bridge_ports p5p1 eth0
	bridge_stp off
	bridge_maxwait 10

```
(not sure why bridge_ports isn't tabbed over... it is in the config I copied)

ifconfig:
```
administrator@vault:~$ ifconfig
br0       Link encap:Ethernet  HWaddr bc:6f:d4:63:f0:6b  
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::be5f:f4ff:fe64:f06b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:439431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:531957 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:983215486 (983.2 MB)  TX bytes:275245676 (275.2 MB)

eth0      Link encap:Ethernet  HWaddr f7:f2:3d:05:7a:e4  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:696605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:346132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1006530181 (1.0 GB)  TX bytes:22949094 (22.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:379 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73471 (73.4 KB)  TX bytes:73471 (73.4 KB)

p5p1      Link encap:Ethernet  HWaddr ba:3f:f4:64:f0:6b  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:187042 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5135929 (5.1 MB)  TX bytes:252731489 (252.7 MB)

```

And a favorite utility of mine, bmon:
[http://i.imgur.com/niDV1tT.png](http://i.imgur.com/niDV1tT.png)

As you can see in bmon, eth0 has a higher network load. eth0 is NIC B, i.e. my PCIE NIC I just added. This is the NIC I wanted to get hammered with the video bandwidth. p5p1 is my onboard NIC, i.e. NIC A. 

I appreciate the insight everyone gave me. In the end, this setup seems to do what I was after. I'm going to run with it for now and see how things go. Thanks again everyone!

---

