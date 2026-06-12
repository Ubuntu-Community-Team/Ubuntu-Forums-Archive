---
title: "2 NICs / 2 Networks -- Question.."
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by pacini on 2007-11-23
Hi,
I've been trying to figure out how to solve my problem with no luck. I'm running 7.1 Server, here we go:

I have 2 networks, one connected to the internet (ETH0) for internet usage, and, another datalink to my ITSP running a local VOIP application (ETH1). Now, I have been reading about network split access but I wasn't able to get it to work. I have been getting a numerous number of dropped calls from my VOIP network 'cause packets were trying to access the internet network. Here's a lil' information on my network:

Information on my NIC setup:
ETH0 (Internet Side): running IP 192.168.7.7 gw 192.168.7.1 
ETH1 (Data Link Side): running IP 10.10.22.4 gw 10.10.22.1

route -n output:

192.168.7.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
10.10.22.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
0.0.0.0 10.10.22.1 0.0.0.0 UG 100 0 0 eth1
0.0.0.0 192.168.7.1 0.0.0.0 UG 100 0 0 eth0

 Your help is highly appreciated,
 Thanks.

---

### Post by rockdon on 2007-11-23
You have two default gateways in that route setup. I would start by deleting the route entry for the VoIP network, since you only want traffic to go to that network that is intended by its destination address. The default gateway is used when the local machine is unaware of how to route the packets in question to the destination network, it is trusted that when sending these packets to the default gateway IT will figure out how to get them where they need to go. 

delete this route entry : 0.0.0.0 10.10.22.1 0.0.0.0 UG 100 0 0 eth1

That would be where I would start, hope this helps.

---

### Post by pacini on 2007-11-23
> **rockdon said:**
> You have two default gateways in that route setup. I would start by deleting the route entry for the VoIP network, since you only want traffic to go to that network that is intended by its destination address. The default gateway is used when the local machine is unaware of how to route the packets in question to the destination network, it is trusted that when sending these packets to the default gateway IT will figure out how to get them where they need to go. 

delete this route entry : 0.0.0.0 10.10.22.1 0.0.0.0 UG 100 0 0 eth1

That would be where I would start, hope this helps.

  hrm, just tried that. But, on my datalink voip iface (eth1), I still could not reach my uplink (from my ISP). Will try to try this tonight when no one is using voice.. Thanks for your quick reply :)

---

### Post by pacini on 2007-11-24
Just an update, I still can't get the 2nd network to work :(

---

### Post by paddygman on 2008-02-25
Hey all i'm also having a similar issue,
I have a box which has eth0 outfacing to the web and eth1 facing to an internal network (which also has net)
Ideally i want the machine to be accessible by both.
The eth0 will mainly be used for internet access whilst the eth1 will mainly be used for internal file transfer and remote connection on the internal network.
Any one any ideas what i need to try, I've been reading posts on routing as above but still confused what i need to configure.
Any help appreciated.
Thanks.

config

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 13.13.13.10
gateway 13.13.13.1
netmask 255.255.255.0
network 13.13.13.0
broadcast 13.13.13.255

---

### Post by paddygman on 2008-02-27
Bump anyone have any ideas?
Thanks

---

### Post by The Cog on 2008-02-27
What's the problem? Can you not talk to other PCs on the internal network?

You don't need a default gateway on the eth1 network if your internet access is via eth0.

---

### Post by paddygman on 2008-02-27
nope even when i remove the default gateway on eth1 i still cannot connect to the 13.13.13.* subnet
Its drivin me nuts.
Any other ideas? I've had both nics working individually just not both simultaneously.
I'd like to be able to vnc to the box from either nic.

Thanks

---

### Post by Mr. C. on 2008-02-27
To pass packets from one network to the next, you need to enable ip_forwarding:

sudo echo "1" > /proc/sys/net/ipv4/ip_foward

then your system will route traffic between the two nets.  Each host on the LAN must specify the ubuntu box as its default gateway (since it handles traffic for all packets not destined for the attached network).

The above only enables forwarding for the current boot.  For setting up forwarding for each boot, eExamine etc/sysctl.conf and uncomment the lines:

#net/ipv4/ip_forward=1
#net/ipv6/ip_forward=1

MrC

---

### Post by The Cog on 2008-02-28
Can you post the output from the command **ifconfig**? We'll see if the interface is up and running. Maybe also **route -n**

Another useful test might be to use 
**sudo tcpdump -i eth1**
to print network packets while you try and ping somthing on 13.13.13 from another window.

---

### Post by paddygman on 2008-02-28
paddygman@RANDOM-SERVER:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0B:DB:45:78:FF  
          inet addr:82.41.9.174  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::20b:dbff:fe45:78ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4558586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:881749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:324027766 (309.0 MB)  TX bytes:141909323 (135.3 MB)
          Base address:0xe8c0 Memory:fe1c0000-fe1e0000 

eth1      Link encap:Ethernet  HWaddr 00:00:94:CB:E1:A2  
          inet addr:13.13.13.10  Bcast:13.13.13.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1156 (1.1 KB)  TX bytes:1156 (1.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0E:2E:37:0B:F0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:0E:2E:37:0B:F0  
          inet addr:169.254.5.236  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-37-0B-F0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


paddygman@RANDOM-SERVER:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
13.13.13.0      0.0.0.0         255.255.255.0   U     0      0        0 eth1
82.41.8.0       0.0.0.0         255.255.248.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan0
0.0.0.0         82.41.8.1       0.0.0.0         UG    100    0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 wlan0


As for network packets on that whilst ppinging, its not routing through that nic so nada happening!

---

### Post by The Cog on 2008-02-28
I think you have a cabling problem. ifconfig for eth1 is missing the word RUNNING, and I believe this is the word that comes and goes as the cable is plugged in and removed. Teh fact that both tx (transmitted) packets and rx (recieved) packets are zero supports the idea.

---

### Post by Mr. C. on 2008-02-28
Right - interface eth1 is not active currently (but it is configured).

There are also still two default routes.  The system has been configured to send all non-local packets to both eth0 and wlan0.  This will not work, period.  Disable wlan0.

Did you enable forwarding? If you're not sure, what is the output of :

```
sudo cat /proc/sys/net/ipv4/ip_foward
```

If it is 0, set it with:

```
sudo echo "1" > /proc/sys/net/ipv4/ip_foward
```

MrC

---

### Post by paddygman on 2008-02-29
Managed to repost same outputs a few times. Please ignore.

---

### Post by paddygman on 2008-02-29
Right i've disabled wlan0 from 
sudo ipconfig wlan0 down
I've tried
sudo ipconfig eth1 up
doesnt change the state to running
I've changed to root to enable forwarding as i couldnt from sudo but that still has had no affect.
It just doesnt appear to be running, dont know why.
when i enable the gateway on the eth1 my vnc connection drops.
Now i've to get off my seat again.
Any other suggestions please.
Thanks

---

### Post by Mr. C. on 2008-02-29
Let's step back.  You are trying to solve too many things at once, and each has dependencies on other things.

First, bring down all interfaces, and then bring up *only* eth1.  I don't recall if you have a GUI or not, where Network Mangler may be thwarting your desires.  If you have Network Manager, disable the interfaces from there, and don't try doing so behind its back with command line stuff.  Otherwise, use the command line.

With only eth1 up, does the interface show running, and can you ping another host on that network ?

If not, swap cables and try again.  Once you are sure eth1 works correctly, then let's move to the next step.  There's no point in trying to solve a routing issue, when one of the networks is down!

MrC

---

