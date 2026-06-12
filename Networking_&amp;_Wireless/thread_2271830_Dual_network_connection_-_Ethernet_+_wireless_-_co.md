---
title: "Dual network connection - Ethernet + wireless - connection problems"
date: 2015-04-01
forum: Networking &amp; Wireless
---

### Post by procco on 2015-04-01
Hi. I am trying to setup a dual connection network for a robotic application.  A diagram is attached.

I am controlling a mobile robot via a dedicated wireless link (bridge).  This bridge passes UDP multicast traffic to control the robot and relay telemetry information back to the control station (Toughbook computer).  All devices in this network have static IP addresses as shown in the diagram and the system works great.  

To support field upgrades and trouble-shooting I want to allow a user to connect the Toughbook to the Internet via its wireless adapter (wlan0) so I can connect remotely to access the robot's computer (and other peripherals on the network).  The problem I'm facing is that I don't know anything about the client's Internet connection prior to configuring the Toughbook.  Every wireless connection will be different and I need access to the Toughbook remotely (via Teamviewer at the moment) through wlan0 and I need to access the robot network via eth0.  If both connections are active, Internet traffic will not pass through wlan0.  

To set up the proper (I thought) routing, I did the following:
[LIST]
[*]UDP multicast is configured with: route add -net 239.255.76.0 netmask 255.255.255.0 dev eth0
[*]then I had the client connect the Toughbook to the Internet via wlan0 and determine its IP address via ifconfig
[*]using the IP address from ifconfig, I set the default gateway as follows: route add default gw *ip.address *wlan0
[LIST]
[*]NOTE: if the IP address was 10.10.0.150 I set the gateway to 10.10.0.1 with the command above
[/LIST]
[/LIST]

My problem is this seems to work sometimes, and other times it doesn't.  My UDP multicast traffic doesn't always make it through.  I can connect remotely once the default gateway is set and I can access the 192.168.0.XX network but without multicast traffic, I cannot do the work I need to do. 

Is there an alternative method to route Internet traffic to wlan0 as a default without prior knowledge of the wireless network's gateway or IP address range?  Should I be routing the UDP multicast data in an alternative way?  I did get it working after making numerous routing changes but it didn't stay working and I couldn't repeat the steps to get it running.

The Toughbook is running Ubuntu 14.04 Desktop 64-bit with the latest upgrades and updates (as of today).  Network manager is being used to configure the static IP of the Toughbook (IPV4 manual - set IP address, netmask and gateway as shown in the diagram). The wireless connection is set via dhcp through network manager. Any ideas or thoughts on what I can do to make this work properly?  I'll admit I'm no network expert so hopefully it's an easy problem to solve for someone that actually knows what they are doing.

---

### Post by TheFu on 2015-04-02
a) **don't use network manager for this** - it works for trivial networking only.
b) if you don't know the IP, then use DHCP
c) if you need static IPs AND DHCP, then have the DHCP server provide a reserved IP
d) you'll need to manage the routes for each subnet manually - I'd use post-up options in the interface file
e) More cmd output would be helpful; less descriptions

ifconfig -a
route

I haven't needed to route multicast ever.  Did some searching [http://ubuntuforums.org/showthread.php?t=1405360](http://ubuntuforums.org/showthread.php?t=1405360) They mention  mrouted or pimd.

---

### Post by procco on 2015-04-02
Hi TheFu,
Thanks for the reply.  The problem was network manager.  
I modified my /etc/network/interfaces file to handle the eth0 connection (robot network) and everything works perfectly fine.  I did have to set post-up and pre-down scripts for the UDP multicast but that was no big deal.
Here is what I have:

ifconfig -a output (connected to Internet via usb tether and to robot network via eth0):
```

prs@prs-CF-30KAPAX2M:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1b:d3:1a:66:78  
          inet addr:192.168.0.151  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:d3ff:fe1a:6678/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:301396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:143634670 (143.6 MB)  TX bytes:5029216 (5.0 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:161680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:132786513 (132.7 MB)  TX bytes:132786513 (132.7 MB)

usb0      Link encap:Ethernet  HWaddr 02:57:04:54:38:63  
          inet addr:192.168.42.167  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::57:4ff:fe54:3863/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3742 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2916619 (2.9 MB)  TX bytes:517964 (517.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:7f:b2:4b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:76177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50164654 (50.1 MB)  TX bytes:53205360 (53.2 MB)

```

route:
```

prs@prs-CF-30KAPAX2M:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.42.0    *               255.255.255.0   U     1      0        0 usb0
239.255.76.0    *               255.255.255.0   U     0      0        0 eth0

```

Finally, here is my /etc/network/interfaces file:
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.151
netmask 255.255.255.0
gateway 192.168.0.1
post-up route add -net 239.255.76.0 netmask 255.255.255.0 dev eth0
pre-down route del -net 239.255.76.0 netmask 255.255.255.0 dev eth0

```

Thanks again for your help.
Paul.

---

### Post by TheFu on 2015-04-02
> **procco said:**
> Hi TheFu,
Thanks for the reply.  The problem was network manager. 

Please mark thread **SOLVED** using the thread tools.

---

