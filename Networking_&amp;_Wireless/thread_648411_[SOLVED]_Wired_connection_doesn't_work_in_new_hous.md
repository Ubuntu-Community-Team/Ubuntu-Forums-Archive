---
title: "[SOLVED] Wired connection doesn't work in new house!"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by roastbeef on 2007-12-23
Ubuntu 7.10.

Back home my computer connects to wired internet fine - even behind two linksys routers.  I brought my computer up home for the holidays (yes, I can't live without it!) and now have been hitting brick walls trying to get it to connect.

It seems no matter what I do I can't get a connection.  So far, I've tried two different linksys routers, hooking up my computer directly to the cable modem (skipping the router), blacklisting ipv6, trying a static IP address, and I've gotten nowhere.

Here's some (hopefully) useful info:

Output on my windows machine connected to the same router:

```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\clay>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : db
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : hsd1.fl.comcast.net.

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : hsd1.fl.comcast.net.
        Description . . . . . . . . . . . : Marvell Yukon Gigabit Ethernet 10/10
0/1000Base-T Adapter, Copper RJ-45
        Physical Address. . . . . . . . . : 00-11-D8-A5-4A-74
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 68.59.87.99
        Subnet Mask . . . . . . . . . . . : 255.255.248.0
        Default Gateway . . . . . . . . . : 68.59.80.1
        DHCP Server . . . . . . . . . . . : 68.87.74.13
        DNS Servers . . . . . . . . . . . : 68.87.74.162
                                            68.87.68.162
        Lease Obtained. . . . . . . . . . : Sunday, December 23, 2007 11:49:57 A
M
        Lease Expires . . . . . . . . . . : Wednesday, December 26, 2007 8:28:19
 PM

C:\Documents and Settings\clay>
```

On my ubuntu machine I've logged into recovery mode so I don't have X running - just the command line.

Contents of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:13:D4:FF:11:87  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60650 (59.2 KB)  TX bytes:1556 (1.5 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:B6:5D:51:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-B6-5D-51-01-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

Contents of /etc/network/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

auto eth0

```

Output of netstat -rn:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 wlan0

```

Contents of /etc/resolv.conf

```
nameserver 192.168.1.1
```

I can ping 192.168.1.1 (router) just fine, and I can access the router via Firefox.  However I cannot reach anything else!  I've tried pinging [www.google.com](www.google.com), nothing happens.  I tried pinging the ip address of google, still nothing.

When I run dhclient I get:

```
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:16:b6:5d:51:01
Sending on   LPF/wlan0/00:16:b6:5d:51:01
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:13:d4:ff:11:87
Sending on   LPF/eth0/00:13:d4:ff:11:87
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 127 seconds.


```

Any help would be appreciated.  Like I said, it was working fine on my connection back home, but here no go.

---

### Post by jflaker on 2007-12-23
Is there internet access to the house?

If you HAD internet at one point, was this DSL or Cable?

---

### Post by roastbeef on 2007-12-23
I had internet working on my Ubuntu machine in Orlando.  I took my computer to Panama City, and now it's not working.  However, we have internet here at the house - I'm posting on my dad's windows computer, which is how I was able to output the ipconfig /all info at the top of my first post.

Both here and Orlando have used a cable modem.

---

### Post by gilf on 2007-12-23
Just throwing a couple of simple things out there without much evidence:

try out the "direct connection to internet " and "automatically configure proxy" options in Firefox preferences.

try out a different pair of DNS entries in the DNS tab of the network manager.

a couple of open DNS addresses can be found here:

[https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)

be sure to add them AHEAD of the existing ones, so they get used in preference.

---

### Post by jflaker on 2007-12-23
Instead of using your modem....just plug the connection from your father's cable modem into the WAN/INTERNET port of your router....plug your computer (or use wireless) and his into the router and you should be good to go..........

Bring all devices down, 

then bring up the modem first and let it acquire the network.
Bring up your router, then the computers.........

reply back.

---

### Post by gilf on 2007-12-23
> So far, I've tried two different linksys routers, hooking up my computer directly to the cable modem (skipping the router),

he tried  that

---

### Post by roastbeef on 2007-12-23
Thanks, I'll try those here in a second.

---

### Post by roastbeef on 2007-12-23
I tried open dns, that didn't seem to change things.  However, my brother got his XP laptop out and hooked it up to the router, which ALSO can't connect - so now I have to suspect the router is somehow not working correctly?  

What's totally bizarre is that I am typing on my dad's computer which is connected to the router, yet any other computer connected to router doesn't seem to be able to connect. 

Before, I had the router setup so that a cat5 cable connecting the modem was patched to the 4th linksys port.  Then I had the three other ports going to the computers - 1 to my dad's computer, 2 to my desktop, and 3 to my brother's laptop.

Now we have it so that the cat5 cable is coming from the modem to the 'uplink' port of the router.  Then ports 1-3 are connected to our computers.

In both configurations, only my dad's computer seems to be working.

Thanks for the help thus-far.  Right now I'm really confused as to what's going on, but it sounds like it's not really an ubuntu issue since an XP machine ALSO doesn't work.

---

### Post by gilf on 2007-12-23
Yes it sounds like a non ubuntu issue.

Besides cabling,you might check DHCP leases for expiration, and also try resetting the router.

Also make sure the router isn't set to filter for only specific MAC addresses.

---

### Post by roastbeef on 2007-12-23
Turns out to be a comcast/router issue.  Mac cloning is correct - that's basically what we had to do.  Thanks for the help, sorry it turned out to be something stupid.  Good to know though that it wasn't a weird Ubuntu issue.

---

### Post by gilf on 2007-12-23
Glad you reported back, that may throw some light on other hard to pin down issues I've seen with similar symptoms.

---

