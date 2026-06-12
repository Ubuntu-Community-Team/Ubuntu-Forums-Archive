---
title: "setting up linux router"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by ubiwankanubi on 2007-03-12
I'm trying to setup an ubuntu router with the instructions here:
[http://www.netscape.com/viewstory/2006/07/01/how-to-setup-your-ubuntu-computer-to-be-a-router/?url=http%3A%2F%2Fubuntulinuxhowto.blogspot.com%2F2006%2F06%2Fsetup-your-computer-to-be-router.html&frame=true](http://www.netscape.com/viewstory/2006/07/01/how-to-setup-your-ubuntu-computer-to-be-a-router/?url=http%3A%2F%2Fubuntulinuxhowto.blogspot.com%2F2006%2F06%2Fsetup-your-computer-to-be-router.html&frame=true)

but i can't get get dhcp to start. here's my dhcp config file:

option domain-name-servers 192.168.1.1;
option broadcast-address 192.168.1.255;
option subnet-mask 255.255.255.0;
option routers 192.168.1.1;
default-lease-time 600;
max-lease-time 7200;
subnet 192.168.1.0 netmask 255.255.255.0 {
	option domain-name-servers 192.168.1.2;
	option broadcast-address 192.168.1.255;
	option subnet-mask 255.255.255.0;
	option routers 192.168.1.1;
	range 192.168.1.50 192.168.1.51;
	}

also trying to start it from the command line i get this:
 sudo /usr/sbin/dhcpd3 eth0
Internet Systems Consortium DHCP Server V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Wrote 0 leases to leases file.
Listening on LPF/eth0/00:08:02:d6:71:38/192.168.1/24
Sending on   LPF/eth0/00:08:02:d6:71:38/192.168.1/24
Can't bind to dhcp address: Address already in use
Please make sure there is no other dhcp server
running and that there's no entry for dhcp or
bootp in /etc/inetd.conf.   Also make sure you
are not running HP JetAdmin software, which
includes a bootp server.

says something is using the service. how can I find what it is?

---

### Post by Mr. C. on 2007-03-12
You either have the dhclient running or the server is already started.  It would hardly make sense for your own DHCP server to obtain its own IP address from itself.

See which programs are listening on the DHCP socket:

```
lsof -i | grep dhclient
```

MrC

---

### Post by ubiwankanubi on 2007-03-12
nothing running when trying   lsof -i | grep dhclient 

also tried:
 sudo /etc/init.d/dhcp3-server restart
Internet Systems Consortium DHCP Server V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
 * Stopping DHCP server                                                  [fail]
Internet Systems Consortium DHCP Server V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
 * Starting DHCP server:                                                 [fail]

---

### Post by Mr. C. on 2007-03-12
You'll have to look through your logs to see what the error messages are.  Check /var/log/syslog.

MrC

---

### Post by ubix on 2007-03-13
While you opened a thread about setting up a Linux router, you are discussing a different subject, namely the **dhcpd**. Though you may eventually want to provide a DHCP services from your router, I believe you should address the DHCP question in a different thread. Routing itself has nothing to do with any name and/or IP services such as DHCP or DNS. For starters, at the beginning you should use the **/etc/hosts** instead, and figure out if your network interfaces are configured properly, if your Linux lets the traffic to be sent from one interface to the other, i.e. if kernel is compiled with router settings etc.

---

### Post by Mr. C. on 2007-03-13
Perhaps the OP doesn't fully understand a few of these concepts, but that's ok, its his/her question.  Perhaps a simple change in subject would suffice.

---

### Post by ubix on 2007-03-13
I would humbly ask forgiveness, and insist s/he opens a new thread, and comes back when problems outside routing are resolved. It would be desirable though that the link to the new thread be posted here. We may want to follow both threads.

---

### Post by ubiwankanubi on 2007-03-13
ok, so with this knowledge, how can i get eth0 to pass packets to eth1?
i have eth1 connected to the internet, and eth0 connected to another computer. sorry if i was talking about something different. i'm very inexperienced in this matter.

> **ubix said:**
> While you opened a thread about setting up a Linux router, you are discussing a different subject, namely the **dhcpd**. Though you may eventually want to provide a DHCP services from your router, I believe you should address the DHCP question in a different thread. Routing itself has nothing to do with any name and/or IP services such as DHCP or DNS. For starters, at the beginning you should use the **/etc/hosts** instead, and figure out if your network interfaces are configured properly, if your Linux lets the traffic to be sent from one interface to the other, i.e. if kernel is compiled with router settings etc.

---

### Post by Mr. C. on 2007-03-13
You need to turn on forwarding in the kernel:

```
echo 1> /proc/sys/net/ipv4/ip_forward
```

and be sure your route tables are setup correctly:

```
netstat -rn
```

MrC

---

### Post by ubix on 2007-03-13
Before we start shooting ones and zeros into **/proc/sys/net/ipv4/...** files, and perhaps even compiling your router's kernel, please tell us how are your two computers connected. [list]
[*] via router-switch?
[*] via switch?
[*] directly with wires?
[*] do you have any kind of wireless connection?
[*] do you have any devices like modems, routers, switches, and how are they connected?
[/list]Here  is a [diagram]("http://koti.mbnet.fi/~keiky/misc/linux/router/imgs/ethernet_lan.png") of a most common and the simplest network layout allowing more computers to access  the Internet simultaneously. It shows the position of the switch in relation to other equipment.  The above image ([diagram]("http://koti.mbnet.fi/~keiky/misc/linux/router/imgs/ethernet_lan.png")) is from the page: [Building a Linux Router]("http://koti.mbnet.fi/~keiky/misc/linux/router/lnx_router.html"), which I suggest you read for an easy introduction to what you attempted to discuss here.

However, "Linux Router" and the "Switch" on the diagram are implemented here as two devices, which is a more elaborate setup than most of home users need. Namely, these two devices can be purchased as a single device, which acts as a router and a switch at the same time. Unless you want to learn how to build a router, or how networking functions on a lower level, than a regular user ever needs to know, I doubt that just because you could turn an old PC into a router, you will dismiss a much easier and far more elegant solution with a router-switch. The learning curve here is a very seep one. Also considering the time and efforts you'll need to employ the costs of doing it yourself in comparison to an off-the-shelf solution are prohibitive. Of course, if you mix different type of network types such as wireless and wired networks it appears that no solution is easy. 

Here are some additional web pages that may be helpful:[list]
[*] [http://en.wikipedia.org/wiki/Router](http://en.wikipedia.org/wiki/Router)
[*] [Wireless router-switch]("http://www.mobileplanet.com/p.aspx?i=104078")
[*] [Combo Wireless router-switch]("http://www.newegg.com/Product/Product.asp?Item=N82E16833127158)[/list]  From the above list of different types of routers, you should get an idea what is available in computer stores. If you can tell which product from this list would best suite your needs, you are well prepared to embark on this project. You should also have a better understanding between which choices you are deciding, namely, off the shelf solution should provide you with the solution immediately - i.e. here's your router for the cost of a few hours of work. Compare this with ten if not hundred of times more expensive solution calculated in man hours of learning and work, of course depending on your experience.

---

