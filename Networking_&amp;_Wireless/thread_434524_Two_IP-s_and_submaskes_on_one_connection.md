---
title: "Two IP-s and submaskes on one connection?"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by Indrek on 2007-05-06
Hi, I want to setup my IPTV Stream parallel with Internet Connection
IPTV Streamings are coming from:
IP: 10.22.93.245
Subnet: 255.255.254.0
and Internet comes:
IP: 192.168.1.64
Subnet: 255.255.255.0
and their both have same gateway: 192.168.1.254

*I've posted ips, because their safe and it gets better to understand.*

Problem is: How do i get these both work with ONE Network card?

---

### Post by netztier on 2007-05-06
> **Indrek said:**
> Hi, I want to setup my IPTV Stream parallel with Internet Connection
IPTV Streamings are coming from:
IP: 10.22.93.245
Subnet: 255.255.254.0
and Internet comes:
IP: 192.168.1.64
Subnet: 255.255.255.0
and their both have same gateway: 192.168.1.254

*I've posted ips, because their safe and it gets better to understand.*

Problem is: How do i get these both work with ONE Network card?

In this case, it is not necessarily a given that you actually need two IP addresses. It is only the case if the IPTV sender is on the same LAN as your "receiver" (which, as I understand it, is your PC). On the same LAN meaning "connected to the same Hub/Switch" or connected to the same VLAN (virtual LAN) if we're talking about about some larger network setup here.

If however the router (which has the IP address that you configure as your "default gateway") knows a path to the 10.22.92.0/23 network and can forward packets to & from that network and your 192.168.1.0/24 network, you won't need a second IP address. That's the most basic and "designed for" fuction of a router: forward packets between different IP networks.

I take it that you are using 192.168,1.64 as your IP address currently. Can you succesfully **ping** 10.22.93.245, or do a **traceroute** for this IP address? If yes, there should be no need for a second IP address. 

Now there's another possible case:  there are **two** routers, one with 192.168.1.254 giving access to the Internet, one with 192.168.1.xxx giving access to the 10.22.93.92/23 network. Now here, you don't need a second IP address, but just a **static route** that says that  "network 10.22.93.92 with netmask 255.255.254.0 is reachable via 192.168.1.xxx". The default route is nothing else than a static route, it just says that "network 0.0.0.0 with mask 0.0.0.0 is reachable via <default gateway's IP address>".

We'll need a bit more information about the network topology. Having to use multiple addresses from different subnets on one broadcast domain (i.e. on the same LAN or VLAN) is a sign of "bad network design" or of "kludging things together", most of the time. And it will always lead to more difficulties, once it comes to name resolution, broadcast traffic and troubleshooting.

Oh it *can* be done, and its not "illegal" from a technical point of view, but it's generally not advisable. So let us know what you know about the networks(s) you are using, an we'll try to find a solution.


best regards

Marc

---

### Post by hartz on 2007-05-06
I am sure there is some way to do it through a GUI, but it is very easy to do from a command-line, so I will show you the commands to use.

First enter this command to display your existing IP configuration:

```
ifconfig -a
```

The output will be similar to this:

```
hartz@linwarg:~$ ifconfig -a
[COLOR="Red"]eth0[/COLOR]      Link encap:Ethernet  HWaddr 00:0F:EA:81:DE:1A  
          inet addr:[COLOR="Blue"]192.168.24.20[/COLOR]  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20f:eaff:fe81:de1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:675171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:510162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:764955989 (729.5 MiB)  TX bytes:65485228 (62.4 MiB)
          Interrupt:16 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:0F:EA:82:27:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22404 (21.8 KiB)  TX bytes:22404 (21.8 KiB)
```


Note the parts that I have highlighted in RED and BLUE:  The RED is your interface name.  You will want to add a second IP address to this interface.

So assuming that you currently have a 10.* address, to add the 192.168.* address, you would use a command like this:

```
ifconfig [COLOR="Red"]eth0[/COLOR] add [COLOR="Blue"]192.168.1.5[/COLOR] netmask 255.255.255.0
```

Similarly if you currently have the 192.168 address, if you want to add an extra address in the 10.* range, the command would look like this:

```
ifconfig [COLOR="Red"]eth0[/COLOR] add [COLOR="Blue"]10.22.93.5[/COLOR] netmask 255.255.254.0
```

I picked an address of X.X.X.5 in both cases, but use whatever applies to your network, remembering that you have to have a unique address in the same range, given the subnet mask, as the other directly attached systems that you want to connect to.  After doing this, re-run the ifconfig -a command to check that it is set up correctly - you should see something like this:

```
hartz@linwarg:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:81:DE:1A  
          inet addr:192.168.24.20  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20f:eaff:fe81:de1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:675171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:510162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:764955989 (729.5 MiB)  TX bytes:65485228 (62.4 MiB)
          Interrupt:16 Base address:0x2000 

[COLOR="Magenta"]eth0:0    Link encap:Ethernet  HWaddr 00:0F:EA:81:DE:1A  
          inet addr:10.30.20.10  Bcast:192.168.24.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x2000[/COLOR] 

eth1      Link encap:Ethernet  HWaddr 00:0F:EA:82:27:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22404 (21.8 KiB)  TX bytes:22404 (21.8 KiB)
```

A new "virtrual" interface with a :0 has been added onto the physical interface.  By implication you can add several virtual interfaces (I'd have to look up what the maximum is and I'm too lazy).

As far as the default gateway is concerned, you can check it with this command:

```
netstat -r
```

And the output will look similar to this:

```
hartz@linwarg:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.30.20.0      *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
192.168.0.0     *               255.255.0.0     U         0 0          0 eth0
[COLOR="DarkOrange"]default         firewall        0.0.0.0         UG        0 0          0 eth0[/COLOR]
```

The line the reads "default" indicates your default router. 

 I hope this helps.

---

