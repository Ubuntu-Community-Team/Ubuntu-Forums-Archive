---
title: "enable two NICs"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by xdevel2000 on 2008-08-10
Hi, I'm new and I want to know how to enable 
the two NICs I have.

I have one NIC linked to a router into a LAN
another NIC directly connected to Internet.

I noticed that network manager enable only one NIC at
time eth0 or eth1 but I want both enabled how do I that?

Thanks.

---

### Post by SpaceTeddy on 2008-08-11
If you want more than one nic enabled you will need to configure this manually in the config files itself. How do you want them to be configured ? dhcp ? static ? and which one do you want to configure... A little more info would be nice. 
In general, this is rather simple - use this command to edit the network settings of your network:
```
gksu gedit /etc/network/interfaces
```

in this file, add the appropriate lines on what you want to do with what device. For example, if you want eth0 to be static, use this:
```

auto eth0
iface eth0 inet static
	address 192.168.0.1
	netmask 255.255.255.0
	network 192.168.16.0

```
which would bring up eth0 at boot time to have the specified, static ip.

or, if you want eth0 to be configured via dhcp, use this:
```

auto eth0
iface eth0 inet dhcp

```

once that is done, you'll need to restart (it can be done without, but that is a little more work on the console).
If, by any chance, you break your network entirely - just remove all added lines from the given file and network manager will pick the devices up again and let you configure them. 

Yet - the real question is, what do you want to accomplish ?

---

### Post by Iowan on 2008-08-11
> **SpaceTeddy said:**
> ```

auto eth0
iface eth0 inet static
	address 192.168.0.1
	netmask 255.255.255.0
	network 192.168.[COLOR="Red"]16[/COLOR].0

```

Sorry to nitpick... should that have been 102.168.0.0?

My nickel's worth - Though it might be possible to have both NIC's assigned via DHCP, it's usually easier to have at least one static - in particular the one acting as "Server".  I suspect the internet connection will be via DHCP.  If the router assigns addresses, the other NIC *might* work via DHCP, but if it is acting as gateway, it becomes a moving target.  Sounds like you want to use the machine to share internet connection.

---

### Post by xdevel2000 on 2008-08-11
Ok, I try to clarify better...

I have 2 routers:

The first that goes to internet and my ISP give me via DHCP an IP and it is
linked to eth0;

The second that is for my LAN and it releases via DHCP other IP for my computers. One of this ip is assigned to eth1;

So I want that both the NIC being connected so with one I navigate in internet and with the other I navigate in my LAN.

Thanks.

---

### Post by Iowan on 2008-08-11
In that case, Enabling DHCP for both *should* work. Using **SpaceTeddy**'s example: ```
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
``` (There should already be a LO" line in there)

---

### Post by xdevel2000 on 2008-08-11
before to make that must I remove NetworkManager applet? 

I noticed that /etc/network/interfaces in my ubuntu is empty...

mybe because NetworkManger does manage the NICs?

---

### Post by SpaceTeddy on 2008-08-11
no - network manager can be left on the computer. It will not pick up any device that is listed in the /etc/network/interfaces, as that file has priority over network manager. Any device not listed in this file will be managed my network manager (as it has no configuration :) )

However - you might not want to issue dhcp leases on the internal network to the machine, as this would mean it gets two default gateways - which is not a good idea. A machine must always only have one default gateway.

PS: yes, the network should have been 192.168.0.0 (i forgot to change that from my example - sorry :)

---

### Post by mborges on 2008-08-13
Hello.

This solved half my problem. Thanks.

I have the exact same issue: 2 NICs, one (172.16.1.10 by DHCP and NOT always the same) for the internal network (web based application on 172.16.1.1, files shared, printers shared, etc) and another (10.200.1.1 by DHCP and NOT always the same) to access the internet. 
But to make the work i have to configure the route table to make all requests to the 172.16.xxx.xxx go thru the first one and all other thru the second one.
Usually i work this way with Windows XP.

Now you guys solved the first problem: enabling both NICs.
The second problem is the route table... how do i do this in ubuntu 8.04?

Thanks in advanced,

MAB

P.S. I'm a beginner in ubuntu/linux in general and not a native English speaker, sorry for any inconvenience.

---

### Post by TherapyQuestionMark on 2008-08-13
Bump!

Same problem :D

---

### Post by Iowan on 2008-08-13
A li'l off-topic (should probably start a new thread),but...
start with **man route**. Perhaps it will provide the necessary information to set up your routing table.

---

### Post by SpaceTeddy on 2008-08-14
for directly attached Network you do not need to add the appropriate routes - that is done automatically when the interface is activated.

if you need to add a route nonetheless - here is the (temporary) command to do so (you'll need to adjust it to your networks)

```
sudo route add -net 192.168.130.0 netmask 255.255.255.0 dev eth0
sudo route add -net 192.168.130.0 netmask 255.255.255.0 gw 192.168.0.1
```

the first command tells a router that a network is directly attached to a network card. Im this case, the 192.168.130.0/24 network is found on the network card eth0
the second command tells the router that a router who knows more about the network can be found at the given ip. In this case, the computer with the ip 192.168.0.1 knows where to find the 192.168.130.0/24 network (this only works if the 192.168.0.0/24 network is directly attached to the computer. as a gateway, you can ONLY reference networks that the router can access directly)

Also, i'd suggest you read up on the route command (there are examples in the suggested man page) and also make sure that you understand how routes work before you frustrate yourself with trying the given command and not getting to to work 

hope it helps :)

---

### Post by mborges on 2008-08-14
Thanks a lot both of you: Iowan and SpaceTeddy.

I will read the man pages to learn a bit more about how routing works under ubuntu linux.

Thanks for the examples and the path to take.

Best regards,

MAB

---

### Post by xdevel2000 on 2008-08-16
Sorry for the late to try it. 

Well, I done that but I don't understand because I must manually do:
ifup eth0
ifup eth1
Why?

---

### Post by SpaceTeddy on 2008-08-16
is the line
> auto eth0 eth1 
found in your /etc/network/interfaces ? the iface only configures the network card - the auto brings it up upon boot.

Hope it helps :)

---

### Post by xdevel2000 on 2008-08-16
Yes all is wrote right!

Again, excuse me but I have also this problem:

If I ifdown eth1 and leave alone eth0 (directly connected to internet)
It doesn't work I can't navigate, and so on...

Why?

It seems as only via eth0 I can do networking?

What's problem?

Thanks

---

### Post by SpaceTeddy on 2008-08-17
i'd need your interface and routing information to answer that question. Answering this generally is kinda impossible :)

run these commands and post the output here:
```
route -n
ifconfig
cat /etc/resolv.conf
```

let's see what we can figure out :)

---

