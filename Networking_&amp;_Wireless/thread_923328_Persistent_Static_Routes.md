---
title: "Persistent Static Routes"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by dwanders on 2008-09-18
I am using Ubuntu 8.04 - LTS 
My PC gets its IP address from a W2003K server in our network & this works fine, and my /etc/network/interfaces looks like this:

danderso@PC095:~$ more /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

danderso@PC095:~$ 

This works great to get me to our LAN & Internet access, however we also have some other subnets in the WAN that I need access to regularly, so I have tried appending to the /etc/network/interfaces :

#static routes
post-up route add -net 10.206.240.0 netmask 255.255.255.0 gw 10.206.201.75
post-up route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.206.201.1

rebooted and no static routes. 

I also tried appending :

#static routes
up route add -net 10.206.240.0 netmask 255.255.255.0 gw 10.206.201.75
up route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.206.201.1

to the /etc/network/interfaces

rebooted and no static routes. 

I realize that I could just add a little script somewhere and have it run each time I reboot, but I would rather stick to the standard way of adding static routes to a PC rather than hoking something up. Any assistance with this matter is appreciated.

---

### Post by dwanders on 2008-09-23
Nobody has experienced this? or something similar?

---

### Post by Iowan on 2008-09-23
Looks like something that should be in the routing table (**route**?) rather than **interfaces** file.  I'll try to check on it when I get home.

---

### Post by dwanders on 2008-09-23
Yes, they should be in the routing table, I am trying to add them to the table after the interface comes up. Any information you find will be greatly appreciated.

---

### Post by willca on 2008-09-24
A couple ways you can do this. If you want this routes to load only when you login and not other users...then put a script in your home directory and just run from there or depending on the window manager you use (Gnome, KDE, or fluxbox) there is an option under System / Preferences / Sessions something where you can specify programs to run upon login.

Otherwise if you want it systemwide...
edit /etc/staticroutes

example line..
net 192.168.1.0 netmask 255.255.255.0 gateway 192.168.2.1

---

### Post by dwanders on 2008-09-24
No joy - I created the file /etc/staticroutes root root rw-r--r-- 
and added the entries as suggested:

danderso@PC095:/etc$ more staticroutes 
net 10.206.240.0 netmask 255.255.255.0 gateway 10.206.201.75
net 10.0.0.0 netmask 255.0.0.0 gateway 10.206.201.1

Then I disabled networking (via right click on the network icon) waited a minute or two, and checked ifconfig & route both were empty echoing nothing back to the console. 

Re-enabled networking via the Icon and checked the routes 
danderso@PC095:/etc$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.206.201.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.206.201.74   0.0.0.0         UG    0      0        0 eth0
danderso@PC095:/etc$ 

I did write a script that I have been using to re-enable the routes after I log in - however I have not found a way to execute it with sudo privileges automatically (really have not looked into do it as I would rather set the static routes the way Ubuntu designers think it ought to be done - but at this point, I would rather have it automated :) )

I also have other PC's that I need to have it done on, and it should be global for the PC - not the user. I can only think it has something to do with the PC getting its IP Address from DHCP - maybe it ignores anything else assuming the DHCP server should set everything?

---

### Post by baskinsy on 2008-09-26
I'm experiencing the same problem.

I have a Ubuntu 6.06 server where adding

```
up route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.215.4.225 dev eth0
```

at /etc/network/interfaces makes the route permanent.

Adding the same on an Ubuntu 8.04 pc does nothing.

Which is the right way to add a permanent static route?

---

### Post by dwanders on 2008-09-26
I don't recall having the dev eth0 on the tail of my entry but I will try it to see if that gets it done. 

I too would like to know the "defacto" way to do it, and don't quite get why none of these approaches work.

---

### Post by dwanders on 2008-09-26
Just thought I would try it with the dev eth0:

Route table before change:
danderso@PC095:/etc/network$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.206.240.0    10.206.201.75   255.255.255.0   UG    0      0        0 eth0
10.206.201.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
10.0.0.0        10.206.201.1    255.0.0.0       UG    0      0        0 eth0
default         10.206.201.74   0.0.0.0         UG    0      0        0 eth0

Changed Interfaces:
danderso@PC095:/etc/network$ more interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

post-up route add -net 10.206.240.0 netmask 255.255.255.0 gw 10.206.201.75 dev eth0
post-up route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.206.201.1 dev eth0

# The primary network interface

Disabled the networking
danderso@PC095:/etc/network$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

Enabled the networking 
danderso@PC095:/etc/network$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.206.201.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.206.201.74   0.0.0.0         UG    0      0        0 eth0
danderso@PC095:/etc/network$ 

Still missing static routes.
Back to the script =)

---

### Post by mips on 2008-09-26
Off topic.

---

### Post by dwanders on 2008-09-26
I suppose it is possible that I have missed something, but you are absolutely correct - this has to be done on all computers in the subnet. 

We are using MS Server 2003 with AD Which requires DHCP & DNS to have taken the place of WINS (absolutely great if you ask me) - any way, so my DHCP server is on a Windows server. Logically - if I had any static routs to add to my subnet - I would think My DHCP server should be capable of handing these out when it assigns an IP address but if the Windows server can do it, I have not found the steps for setting it up. So I have my normal subnet, and all my users want Internet, so DHCP hands out ip addresses with:

1 IP Address of the current subnet
2 Subnet Mask of the subnet 
3 Gateway --> which is going to the Internet 

Perfect every thing is groovy. Now my users also would like access to the Private WAN - rather than having everything get routed out through the default gateway (which would go to the Internet and never get resolved), I need to add a 1 static route to all my PC's  - so if they need the private WAN - things get routed correctly for them automatically. 

Add to that that we also wanted an Equipment LAN a second subnet routed off my Primary LAN. So I potentially have multiple gateways to use which require static routes and I would think I should be able to set them relatively simply. In windows, I use a login script that adds the routes every time the users log into the Domain. Since the Linux box is not really participating in the Domain/User Authentication of Windows, I need another approach for setting the static routes on the growing number of Linux boxes I am adding. 

As I said at the start, I am very sure my approach and thinking could be totally off on this topic - so please enlighten me :) I can take it :( - how should it be set up :confused: so I do not need to add static routes to my PC's?

---

### Post by dwanders on 2008-09-26
While I was reading this (before the Forum Crash!) I did notice that if I had enough money, I could probably resolve all this with a single 8 or 16 port Cisco router to handle all my adjoining subnets - but here things are built cheaply and slowly and are typically built out of necessity as the need arises. Being so Ad hoc - it never fits in that neat little box of networking should be's that we would all love to work on and administer. :lolflag:

---

### Post by mips on 2008-09-27
Off topic.

---

### Post by baskinsy on 2008-09-27
> **mips said:**
> I'm not sure I'm following this. I don't see why you would have to configure static routes on your linux box, it simply makes no sense to me. If this is the case then it would have to be done on all the computers in the network.

Seeing you are in a LAN/WAN environment this would be the domain of routers to perform this function. All you should have is an ip, default gateway (router) & dns addresses. The router(s) in the network should take care of the rest, if they don't you have a severely disfunctional network. The router should have a routing table with all the networks in it and where the traffic should go.

This is not always the case. I want the static route for special reasons that is not necessary to explain here (for example to route traffic outside of a VPN tunnel when the default gateway is through the tunnel).

The problem is that on Ubuntu 8.04 and three more distributions based on it there is no clear way how to configure permanent static routes and nobody can answer this question.

On Opensuse, arch, debian, gentoo and lots of other distributions there is a specific way (sometimes the same) to do that.

P.S. I'm not starting a distro war, but this issue is something fundamental about networking with linux because it is something that is working for years and years and it is the first time that i'm experiencing such a problem with a linux distribution.

---

### Post by mips on 2008-09-27
Off topic.

---

### Post by dwanders on 2008-09-27
mips, while I appriciate your offer - I honestly done think there is a problem with my design. All I was trying to say is that not all networks (in fact I would bet a rare few) are perfectly designed to fit into what is considered to be the ideal set up. Especially here in the real world where we can rarely throw money at every problem to find a solution. 

Besides, we are getting off topic as baskinsy was also trying to say - the question here is about static routes. There should be a way in Ubuntu to assign static routes when the interface is brought up. And I do not believe the steps given work (at least not with my install). And I do not experience this with my RedHat ES4 servers, or my Digital unix servers.

---

### Post by baskinsy on 2008-09-28
Ok good news!!!!

The problem is with the NetworkManager.

Adding 

```
up route add -net 10.0.0.0/8 gw 10.215.4.225 dev eth0
```

works perfect as soon as you disable the NetworkManager or have a manual configuration. Although the last seems to fail sometimes.

---

### Post by mips on 2008-09-28
> **dwanders said:**
> 
Besides, we are getting off topic as baskinsy was also trying to say - the question here is about static routes.

Apologies.

---

### Post by dwanders on 2008-09-30
Adding these lines to my /etc/interfaces did not seem to make a difference. 

# The loopback network interface
auto lo
iface lo inet loopback

up route add -net 10.206.240.0/24 gw 10.206.201.75 dev eth0
up route add -net 10.0.0.0/8 gw 10.206.201.1 dev eth0

Kinda similar (using CIDR) to how RH does it with it /etc/sysconfig/ .... stuff 

So I am getting the feeling I just need to find some method that works for me (like adding the command to the end of some other boot up scripts) since we do not have a standard way of adding static routes to an Ubuntu server.

---

### Post by dwanders on 2008-09-30
You said the problem was with Network Manager, what can I use besides it to take my interface up and and down?

---

### Post by willca on 2008-10-07
sudo ifdown eth0
sudo ifup eth0

---

### Post by dwanders on 2008-10-07
when I try that, first I check to see what interface is running:

danderso@PC095:/etc/network$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:a0:8c:18:7d  
          inet addr:10.206.201.144  Bcast:10.206.201.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fe8c:187d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6399999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4518479 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2287236515 (2.1 GB)  TX bytes:1932796336 (1.8 GB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2312613 (2.2 MB)  TX bytes:2312613 (2.2 MB)

So then I try your command:

danderso@PC095:/etc/network$ sudo ifdown eth0
ifdown: interface eth0 not configured

---

### Post by zeeple on 2009-01-02
FYI:  I just got this working myself today.

The answer to this will not be found by reading the man page for the route command, unfortunately.  Since I have struggled with this I happen to know a little bit about how this works in ubuntu and other distros as well.  The reason you will not find the answer in the route man page is because this is handled differently depending on the distribution.

What is gathered together in RedHat's /etc/sysconfig dir is mostly in /etc/network in ubuntu so that is the best place to look first when you need to manually edit some networking or interface properties.  And as to the very specific static-route file that you get in other distros, this does not exist anywhere in ubuntu.  Rather, to add a static route in ubuntu you add it to the interfaces file immediately under the interface block that will be affected by it, as such:

```

root@isengard:/etc/network# more interfaces 
auto lo
iface lo inet loopback


iface eth0 inet static
address 10.80.80.1
netmask 255.0.0.0
gateway 10.44.65.1

# static routes
up route add -net 10.10.11.0/24 gw 10.0.0.1 dev eth0
up route add -net 10.10.12.0/24 gw 10.0.0.1 dev eth0

auto eth0

```

Remember a couple of things though.  If you add these routes simple using the route command, you will lose them next time your networking is restarted, machine is rebooted, etc.  Also, if you go this route to make them permanent (or static) then you need to restart networking to make use of the new routes, via:

```

sudo /etc/init.d/networking restart

```

If you get an error saying something to the effect that the interfaces file could not be read then you are dealing with either a syntax problem or a placement problem. Be careful to place the static routes under the interface you want them to affect.

---

### Post by dwanders on 2009-01-04
I don't think there is a problem with adding static routes to static IP address, and yes you do add them just as you have shown (or any of the others listed in this post seem to work as well) if you are manually assigning an IP Address. However - if you let DHCP assigned the address, then the static routes are ignored and we have not yet found a way to get the static routes to work with the DHCP assigned address. Short of running a script after your connection is made.

---

