---
title: "WIFI and wired connection driving me mad"
date: 2017-05-12
forum: Networking &amp; Wireless
---

### Post by schoon2 on 2017-05-12
Hi, 

I have both a wired and wireless connection (Ub14.04), and when I connect the wired my wifi internet stops working. I thought [this]("https://askubuntu.com/questions/913909/dual-wifi-and-wireless-problem/914155#914155") had solved it, but no. I'm not good at this networking stuff, so please be gentle.

Details:
I have 4 machines connected via a switch. Their wired connections are static IP  e.g.192.168.1.1, mask=24, gateway=192.168.1.254 , DNS server=10.0.0.10. 'Use this connection only for the resources on its network' checked for both Ipv4 and Ipv6.
Their wifi is automatic (DHCP).
Sometimes the WIFI internet works, sometimes it pauses then works, sometimes it does not work. Mostly it does not work.  It works fine when the wired is disconnected. Sometimes the wired keeps disconnecting.
My route tables are (2nd is wired disconnected):
```
ed@master:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
192.168.1.0     *               255.255.255.0   U     9      0        0 wlan0
```
```
ed@master:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     *               255.255.255.0   U     9      0        0 wlan0
```
TIA!

---

### Post by TheFu on 2017-05-12
You don't want both wifi and wired enabled at the same time, on the same subnet.  If that is your plan, rethink it.  You'll want to learn how networking works a lot more before attempting that (yes, it can be done, but is usually a terrible idea).
The easy answer is to put wifi on 192.168.1.x/24 and wired on 172.20.1.x/24.  That way, you'll never get confused over which network is being used.  Both are non-routable - meant to be used for internal LANs.  I don't understand the DNS server being on the 10.x.x.x network. You'll need a manual route entry to get there. That's find, but usually not something that happens in a home environment.

network-manager will fight if you want both wired/wifi running and both using DHCP. For non-trivial networking, purge network-manager and handle things manually.  Lots of ways to do that, but you'll need a better understanding of networking.

Please use 'code tags' when posting commands. Makes things easier to read and lines them up in a way we are used to seeing. No need to change the font either.

---

### Post by schoon2 on 2017-05-13
Thanks TheFu. I have to have a wired LAN (4 machines need to talk to each other )and a wireless WFI (for Internet).
Re formatting, sorry I could not see the code button and I selected all my text, selected a font but it all stayed the same. I am new to this site.

---

### Post by TheFu on 2017-05-13
So, 1 of the machines needs to be your "router."
In order for that to work, you need a LAN for all the machines and a WAN (wifi) for the router.  Since you probably don't control the wifi subnet, I assumed that was fixed.  The LAN subnet can be any **other** subnet that isn't routable. IT MUST BE DIFFERENT.  That is a key idea in routing.  Machines on the same subnet talk using "ethernet" (the protocol for directly connected, no-routing-needed, machines) and when a machine needs to talk outside the subnet, as known by the IP and netmask, then that traffic is sent to the "gateway" as specified in the network setup.  In most home/small networks, the gateway and router are the same machine.
Clear as mud?  If you want to understand this stuff - google "security now!" and find episode 25; *how the internet works*.  There are about 3 episodes there in a multi-part series that explains this stuff. Just look at the ep titles to see which you need. 25 is definitely the beginning.

---

