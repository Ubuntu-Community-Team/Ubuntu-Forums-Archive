---
title: "DHCP Server Setup Help"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by bundyxc on 2008-10-23
Please redirect me if I am posting in the wrong forum, I wasn't sure what topic was most relevant to my problem. I've installed all of the dhcp files on my server (mongoose) and my client (lemur), and can't get the connection to start.

I've configured dhcp.conf to the following settings, but have absolutely no idea if they are correct or not. My switch is showing network activity coming from mongoose, but not from lemur. 

option domain-name-servers 208.67.222.222, 208.67.220.220;
default-lease-time 86400;
max-lease-time 604800;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.1;
option domain-name-servers 192.168.1.1;
option domain-name "mongoose.local";
subnet 192.168.1.0 netmask 255.255.255.0
{
range 192.168.1.2 192.168.1.200;
}

I have two network cards, and my outbound card is set to a static IP of 192.168.1.1; Thank you all in advance.

---

### Post by tCarls on 2008-10-23
Hi, how about a few more details? What do you mean by "can't get the connection to start"? Could you post the output of dhclient?

One thing I notice: shouldn't the broadcast-address be 192.168.1.255?

---

### Post by Iowan on 2008-10-23
> **bundyxc said:**
> I have two network cards, and my outbound card is set to a static IP of 192.168.1.1; Thank you all in advance.The outbound card would be the one connected to the client? The other card is in a different subnet (IP address is NOT in 192.168.1.x)? Also, the client and server are connected to a hub or switch, or via crossover cable?

FYI, this is the subnet definition from my server's */etc/dhcp3/dhcpd.conf*. ```

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.10 192.168.1.25;
  option domain-name-servers 192.168.1.1; 
  option domain-name "mine";
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
#  default-lease-time 600;
#  max-lease-time 7200;
}
```

---

### Post by bundyxc on 2008-10-23
So this is in the right topic? I don't like screwing up organized things, and sure don't want to get noob-flamed for posting under the wrong category of support.

I can't get my client to find a DHCP offer from my server, and when I run my ifup command to start my network interface on the client, it will not find my DHCP server. I have made sure that my client is set to DHCP in my Network menu. Are there any more configurations that I need to do for my client?

My "outbound" card is connected to a switch, which is connected to only my server, and the client. The switch shows network activity from the server, but no such luck from the client.

My card connected to the internet is in a 192.168.x.x subnet, although I'm not sure what it is. I can't check right now, because I'm not with my computer. Would it be better to try running my DHCP server on a 192.168.3.x subnet, where I have absolutely no network activity?


> **tCarls said:**
> Hi, how about a few more details? What do you mean by "can't get the connection to start"? Could you post the output of dhclient?

One thing I notice: shouldn't the broadcast-address be 192.168.1.255?

I can post the output of dhclient on Monday, when I can check up on my server.

And I have no idea what the broadcast address should be. To be honest, I don't really understand the subnet, netmask, broadcast address, nor the gateway address. If you'd like to explain any, it would be appreciated, but it isn't necessary.

---

### Post by bundyxc on 2008-10-25
[24hr bump]

---

### Post by tCarls on 2008-10-25
> 
So this is in the right topic? I don't like screwing up organized things, and sure don't want to get noob-flamed for posting under the wrong category of support.

It probably should've gone under Networking and Wireless, but I don't think it's a big deal.

> 
My card connected to the internet is in a 192.168.x.x subnet, although I'm not sure what it is. I can't check right now, because I'm not with my computer. Would it be better to try running my DHCP server on a 192.168.3.x subnet, where I have absolutely no network activity?

Yes, they do need to be on different subnets.


> 
And I have no idea what the broadcast address should be. To be honest, I don't really understand the subnet, netmask, broadcast address, nor the gateway address. If you'd like to explain any, it would be appreciated, but it isn't necessary.


There's a pretty good book online by O'reilly that explains most of that. Also, here are a couple links to simple dhcp server setup help pages. They're not very detailed, but maybe they'll help.

[http://oreilly.com/catalog/linag2/book/index.html](http://oreilly.com/catalog/linag2/book/index.html)
[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)
[https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing](https://help.ubuntu.com/community/EasyWirelessToWiredConnectionSharing)

---

### Post by Iowan on 2008-10-25
It *might* not be the client, but the */etc/dhcp3/dhcpd.conf* settings.  Perhaps some of the options need to be inside the subnet definition.

---

### Post by bundyxc on 2008-10-27
Alright, I'm now with my server, so I'll be posting all the information that seems relevant. Forgive me if I post something that doesn't help at all. :)

> **/etc/dhcp3/dhcpd.conf]
ddns-update-style none said:**
> 

Here is my interface configuration for my network cards . eth0 is my card that I'm using for the server, set to a static IP. I'm receiving my internet through my eth1, is this a problem?

[QUOTE=ifconfig -a]
eth0      Link encap:Ethernet  HWaddr 00:11:5b:07:c8:33  
          inet addr:192.168.3.1  Bcast:192.168.3.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:60:08:9a:c6:18  
          inet addr:192.168.2.146  Bcast:192.169.2.255  Mask:255.255.255.0
          inet6 addr: fe80::260:8ff:fe9a:c618/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8950 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7165795 (6.8 MB)  TX bytes:641404 (626.3 KB)
          Interrupt:16 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53100 (51.8 KB)  TX bytes:53100 (51.8 KB)



After starting my server (which works just fine), my switch that connects the server and the client shows network activity from the server end, but has **never** shown any activity from the client.


Here are the only steps that I've taken toward configuring my network.

[LIST=1]
[*]I installed a clean version of Ubuntu 8.04 on both computers
[*]I did all of my updates on the server, I have not updated my client yet.
[*]I installed all of the DHCP packages on the server.
[*]I attempted to configure my "/etc/dhcp3/dhcpd.conf" on the server.
[*]I tried to bring the interfaces down, then back up on the server. It could not get a DHCPOFFER (shown below)
[/LIST]

Here's the output of the command ifup eth0 (which is the network card on the client). Note that I haven't configured *anything* on the client yet.

[QUOTE=ifup eth0]

There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCPClien V3.0.6
Copyright 2004-2007 Internet Systems Consortium
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp](http://www.isc.org/sw/dhcp)

Listening on LPF/eth0:00:a0:c9:a4:e3:ef
Sending on   LPF/eth0:00:a0:c9:a4:e3:ef
Sending on   Socket/falback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/QUOTE]

Anybody see any errors in this? I was sort of wondering where the 255.255.255.255 was coming from, seeing as how my netmask is 255.255.255.0, you know? I'm not a networking guru.. not even remotely, but that looks like the wrong number, maybe?

Now, I'm sure I made a mistake, because I haven't done *any* configurations on my client, and I'm assuming that this is wrong..

---

### Post by Iowan on 2008-10-27
I'd need to check my machine to be sure, but the 255.255.255.255 for DHCP request doesn't seem strange.```
option broadcast-address 192.168.2.1;
```This doesn't seem right - broadcast addresses are usually x.x.x.0 or x.x.x.255 (more common). Try */etc/dhcp3/dhcpd.conf* as:```
ddns-update-style none;
option domain-name-servers 208.67.222.222, 208.67.220.220;
default-lease-time 86400;
max-lease-time 604800;
option domain-name "mongoose.local";
subnet 192.168.3.0 netmask 255.255.255.0
{
range 192.168.3.20 192.168.3.50;
option broadcast-address 192.168.3.255;
}
```
Also, is "mongoose.local" the domain name, or the server hostname?

---

