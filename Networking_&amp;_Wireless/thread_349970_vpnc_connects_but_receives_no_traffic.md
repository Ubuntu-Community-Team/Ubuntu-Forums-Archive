---
title: "vpnc connects but receives no traffic"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by greg101 on 2007-01-30
I'm running Ubuntu 6.10 and can connect normally to Internet hosts (http, ssh, etc.), but am having difficulty getting vpnc to work.

I start vpnc with "sudo vpnc", enter the IDs and passwords when prompted, receive the connection banner from the VPN gateway, and get the message that vpnc started in the background.

However, when I try to ping hosts through the tunnel I get no responses back and the NIC's LED doesn't show any activity.  Very occasionally I can get a response from one of the name servers through the tunnel, but that's rare.  ssh to a host through the tunnel also gets no responses and no NIC activity; netstat shows a socket in SYN_SENT state.

iptables -L -v shows no rules (ACCEPT policy on INPUT, FORWARD and OUTPUT chains).

If I add one rule to each chain to accept all packets (sudo iptables -A INPUT -j ACCEPT, etc.) the behavior changes somewhat: now the NIC shows activity when I send pings, but I still get no responses back, ssh still doesn't connect, etc.

This same workstation was able to connect to the VPN previously when it was running Windows 2000 with the Cisco VPN 4.x client.

netstat -nr shows:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.xx.x   192.168.0.1     255.255.255.255 UGH   0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 tun0

ifconfig shows:
eth0      Link encap:Ethernet  HWaddr 00:40:05:3B:3A:04  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:5ff:fe3b:3a04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12029487 (11.4 MiB)  TX bytes:429486 (419.4 KiB)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1828 (1.7 KiB)  TX bytes:1828 (1.7 KiB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.33.137.1  P-t-P:10.33.137.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1390  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1500 (1.4 KiB)  TX bytes:2352 (2.2 KiB)

Plenty of messages in the forum indicate vpnc works well, so it seems like I missing something -- any hints are welcome.

Thanks,

Greg

---

### Post by kylemallory on 2007-05-21
Anything?  I'm having this same problem.  7.04, vpnc w/ Cisco... It connects, but then nothing, no traffic.

---

### Post by linuksamiko on 2007-06-05
Same here I can connect but no traffic is being routet through the tunnel. I realy need vpnc, how to get it working?

---

### Post by shutterbc on 2007-06-07
I recall not having a problem under Edgy with vpnc (though sometimes I had to mess with the default gateway).  Now I wish I documented how I did this the first time.

Others have noted a known issue where if you connect successfully and then disconnect, the next connection will fail to route properly.  The workaround is to try to connect and use the wrong password (so it fails), then connect again.  Here's a link to the mailing list post:

[http://osdir.com/ml/network.vpnc.devel/2006-12/msg00002.html](http://osdir.com/ml/network.vpnc.devel/2006-12/msg00002.html)

---

### Post by bthawabi on 2007-06-20
Any luck finding out what the problem really is? I have the same exact problem, connected but no communications back from the server.

---

### Post by VorDesigns on 2007-06-20
Same problem, tunnel up but no packets flowing,
Messing with the routes didn't work for me when I tried to point to the VPNServer gateway, I get errors.

Part or the problem may be the similiarities between the remote LAN and mine but I'm not sure.

---

### Post by bthawabi on 2007-06-20
I have found some other entries in the forum discussing this issue. Here are the links that I found but won't be able to test them until I get back from work tonight. This might be an issue with the Firestart firewall loaded by default with Ubuntu.

Setting firestarter:
[http://ubuntuforums.org/showthread.php?t=85369](http://ubuntuforums.org/showthread.php?t=85369)

An even better source for setting up Firestarter:
[http://ubuntuforums.org/showthread.php?t=80076](http://ubuntuforums.org/showthread.php?t=80076)

One more resource:
[http://www.ces.clemson.edu/linux/nm.shtml](http://www.ces.clemson.edu/linux/nm.shtml)

If anyone gets lucky with any of those links, please say which one took care of the problem. So far this is my only lead

---

### Post by zachflanders on 2007-06-20
I've noticed some very strange things with my vpn connection.

My network manager says there is a connection, but I don't get any information unless  run:

```

chmod 755 vpn.sh
sudo ./vpn.sh start
```

while requesting information.  I usually open firefox, request a website, and then run the commands in the terminal.  If I just run the commands without requesting information at the same time, it doesn't work.  I have to do this everytime I reboot my computer.  I can't explain why, computers are pretty much just magic boxes for me.  I dont even know what a vpn is or tunnels are.

I hope this helps in some way!  Good luck

---

### Post by bthawabi on 2007-06-25
It seems that VPNC cannot connect to all types of cisco hardware, well, it is expected, but this was my problem. Using the cisco vpn client worked fine for me

---

### Post by linuksamiko on 2007-07-02
The thing is, that I WAS able to connect to the network with former versions of (k)ubuntu using kvpnc.
But with the new network-manager (n-m) you can't use this anymore so I stick with the Plug-In for the n-m. I think that it has something to do with the n-m. This is actually driving me crazy. I need this but I don't want to connect with the proprietary cisco-stuff (but I will if it doesn't work within the next month becaus then I have to rely on this).

---

### Post by rimoth on 2007-07-02
Try using vpnc through the terminal vpnc-connect. Sorry I'm new and gnome google the command

---

### Post by linuksamiko on 2007-07-11
i tried it over the console but no differents. It connects just fine. I even get the log-in message from the server (this is a little message provided by the admins)

But maybe "route" helps a little:

```

Destination        Router                Genmask               Flags   Metric Ref    Use Iface
any.IP.47.43    192.168.101.1   255.255.255.255       UGH         0      0        0 eth1
192.168.101.0   *                        255.255.255.0       U            0      0        0 eth1
default                *                 0.0.0.0             U            0      0        0 tun0

```

The route looks fine to me but I still don't know why I don't get on the internet using vpnc. Maybe one of you has an idea.

---

### Post by gabe_rosser on 2007-07-17
Sorry, I can't help here - just plead the same as you!  Exactly the same problem here.  route gives this:

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.76.27.246   192.168.2.1     255.255.255.255 UGH   0      0        0 eth0
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         *               0.0.0.0         U     0      0        0 tun0

```

No problem on Ubuntu 6.10 - this thing worked 'out-of-the-box'.

---

### Post by linuksamiko on 2007-08-26
There is something new I found out:
When I start the tunnel (I tryed both ways over network-manager and over terminal), I can still ping other computers, nslookup works fine and I can connect to yahoo-Messenger but not to other messenger services. So the tunnel seams to work just fine. Only the most importent thing "HTML-routing" is dead.

Had anyone else luck with the tunnel-problem?

---

