---
title: "DHCP request using dhclient3, configuration help"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by geoscope on 2007-03-03
For 3 years now I've had a single pc connecting to the internet using a Speedstream 5100 DSL modem. It is a PPPoE device but has ppp onboard, which means I have never had to setup pppoe under linux. I've used FC2,3,4, Mandriva and now Ubuntu 6.06 on the orginal computer. The modem works out of the box. The modem uses the 192.168.0.1 IP address.

Recently I decided to add another computer at home, and set it up as a 2nd desktop and also as a router, iptables firewall, and NAT. The "new" computer has 2 nics and I have the 2 PCs connected with a crossover RJ45 cat5e cable. Let me state now that I have never done networking/routing with Linux, and am a network newbie.

I installed gentoo linux on the "new" Pentium 3 computer following the instructions at: [http://www.gentoo.org/doc/en/home-router-howto.xml](http://www.gentoo.org/doc/en/home-router-howto.xml)
```

	dhcpcd for it's dhcp client
	netmasq to provide DNS and dhcp server for the second computer
	iptables for routing and packet filtering, packet forwarding etc.
	WAN on eth0, 3com 3c905c 10/100
	LAN on eth1, intel 82557 Ethernet Pro 100

```

I found that because the modem uses 192.168.0.1, I could not bind the LAN nic to that IP, or it masked the outbound connection (the modem itself, I would guess) from the WAN nic. After setting the LAN IP to 192.168.1.1, the router pc can reach the internet and both network cards seem to be identified and functional (IP addresses assigned).

```
# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:02:57:DA:C9  
          inet addr:69.224.XXX.XXX  Bcast:69.224.151.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2ff:fe57:dac9/64 Scope:Link
          UP BROADCAST NOTRAILERS RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8007 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6953 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5357305 (5.1 Mb)  TX bytes:905045 (883.8 Kb)
          Interrupt:5 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:A0:C9:0F:2A:D3  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:c9ff:fe0f:2ad3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:105678 (103.2 Kb)  TX bytes:1062 (1.0 Kb)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

However, I can't get the Ubuntu box to obtain an IP from the gentoo box.

```
Ubuntu box (AMD64 3000+, running i386 kernel) has
		dhclient3 for it's dhcp client

```

All other networking settings and programs are the default as they were installed by Ubuntu 6.06. Although I have been using Ubuntu for over a year now, I can safely say I now know far more about how the gentoo box is configured after just one week (if you know gentoo, you know what I mean). 

I can't seem to get dhclient3 on the Ubuntu 6.06 box to properly request an IP address or connect to the internet. I can't make sense out of the /etc/dhcp3/dhclient.conf file, and it's man pages are more obtuse than most I've read. Given my inexperience with Linux networking, my questions are:

1. Does a network dhcp request have to be sent to 192.168.0.1, or will 192.168.1.1 work if I get the configuration setting right?
2. Can anyone tell me how to tell dhclient to make it's request to 192.168.1.1 rather than attempting 192.168.0.1 and failing?
3. Does anyone have an example **dhclient.conf** file they can post that is a bit more concise than the default one installed from Ubuntu packages?
4. Does **/etc/network/interfaces** have anything to do with resolving my problem? (please don't mind the pun, I haven't slept in 36 hours)
5. Should I try to set the router LAN to another IP, such as 192.168.0.2?
6. Is there any other information I can provide to help you help me?
7. How long do you think it's going to  take me to just switch the 2nd computer over to gentoo too? **j/k**

Thank you in advance for any help or useful comments you can provide.

---

### Post by Mr. C. on 2007-03-03
1. Does a network dhcp request have to be sent to 192.168.0.1, or will 192.168.1.1 work if I get the configuration setting right?

DHCP clients attempt to locate an IP by broadcasting a request on the LOCAL LAN.  As long as your DHCP server and DHCP client on the same physical LAN, things are good.

See my week 7 lecture notes and labs: [http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php) ( from some courses I used to teach ).

2. Can anyone tell me how to tell dhclient to make it's request to 192.168.1.1 rather than attempting 192.168.0.1 and failing?

Again, see 1.  The dhcp client will only make a request from the local LAN by default.  You can look at files /etc/dhcp3, such as /etc/dhcp3/dhclient.conf.


3. Does anyone have an example dhclient.conf file they can post that is a bit more concise than the default one installed from Ubuntu packages?

The dhclient.conf file I have is mostly commented out.

4. Does /etc/network/interfaces have anything to do with resolving my problem? (please don't mind the pun, I haven't slept in 36 hours)

As long as the interface is up, that's fine.


5. Should I try to set the router LAN to another IP, such as 192.168.0.2?

There is something in your config that doesn't make sense to me.  Your ipconfig shows eth0 as having IP 69.224.151.181 (which I presume is your public IP).  Yet, you say that your modem provides a private 192.168.0.1 address.  If this is the case, your eth0 and modem are on different networks.  This is no good.  You either have to disable your NAT function on your modem, or put your eth0 in the 192.168.0/24 network (eg. 192.168.0.2).


6. Is there any other information I can provide to help you help me?

I'll take a little presumption:  read about IP at the site above, esp. Lecture 2.

7. How long do you think it's going to take me to just switch the 2nd computer over to gentoo too? j/k

Hmm.? !

By the way, you should get a switch between your PCs instead of a cross-over cable.  There are too many issues with direct cabled connections, that switches resolve.

Hang in there - i'll help you through!
MrC

---

### Post by geoscope on 2007-03-04
Ok some extra info:
First on the modem. I can access the modem and read it's settings via [http://192.168.0.1/](http://192.168.0.1/)
which provides the following info (I've masked some info wherever you see <>). I doubt you need any of that specific info to help me, but if you do, I'd rather PM it than post it for the world to see.

```

		Connection Information

DSL			UP
Connection		UP
User ID			<email address>
Connected at		6144 Kbps (downstream)
			640 Kbps (upstream)
IP Address		69.nnn.nnn.NNN
IP Gateway		69.nnn.nnn.254
DNS Servers		68.nn.nnn.1  <fqdn>
		68.nn.nnn.1  <fqdn>
Mode			PPP on the modem (Public IP for LAN device)
Timeout			Never

		Modem Information
Modem Name		SpeedStream
Model			5100
Serial Number		<sn>
Software Version	1.0.0.36
MAC Address		<mac>
First Use Date		2004/04/05 19:34:02 GMT

		Local Network
Modem IP Address	192.168.0.1
Ethernet Status		Connected

```

There are also button links on the left side of the browser screen that provide extra configuration options and info. I'm hesitant to change anything here. If I bork anything I know it'd take a service tech to get the modem working again.

Under "Connection Configuration" (requires a Modem Access Code to access the settings, which can be modified):

```

VPI		0
VCI		35
Protocol	PPPoE	(also has the option for PPPoA)
Max MTU		1492
ATM Encapsul.	LLC	(or VC-Mux)

A very limited number of applications require that the public IP address assigned to the modem be used by the local LAN device.
Let LAN device share Internet address?	
	No, use private IP address.
	Yes, use public IP address.	X (This option set, and is why the modem has IP 192.168.0.1)

```

Note that to the ouside network, the modem's IP is 69.nnn.nnn.NNN, gateway 69.nnn.nnn.254. For this reason I am thinking of the modem being basically a 1 port (plug) router/modem.


Another page in the modem config is [http://192.168.0.1/ppplocation.htm](http://192.168.0.1/ppplocation.htm)
and the first option is set (by radio button)
```

			PPP Location
			WARNING

Changing these settings may interfere with your ability to connect to the Internet.

X	**PPP is on the modem.** This is the normal mode for this modem when connected to a single computer. In this mode, the PPP session is initiated from the modem. Gateways and routers should work in this mode but their configuration may have to be changed to do so (e.g., you may need to have the gateway/router IP address changed to 192.168.1.1).
 	
	**PPP is on the computer.** This mode is normally used if you need to run a PPPoE client on your PC. This mode can be used with a gateway or router which initiates a PPPoE session. To return to the DSL modem user interface you will need to directly connect your PC to the modem without any gateway or router between the modem and the PC.

	**Bridged Mode (PPPoE is not used).** This mode must be used if you are connecting to a non-PPPoE network.

```


[http://192.168.0.1/statistics.htm](http://192.168.0.1/statistics.htm) then has a lot of information, some repetitive, some are connection packets/errors. I include relevant portions below. (I hope the tables post nicely.)

```

IP Interfaces **(this is the MODEM)**
Address		Netmask		Name
192.168.0.1	255.255.0.0	eth0

```
```

Routing Table **(again the modem, not any of the NICs in the connecting PC.)**
Destination 	Netmask 	Gateway 	Interface
127.0.0.0	255.0.0.0	127.0.0.1	lo0
192.168.0.0	255.255.0.0	192.168.0.1	LAN
Default Gateway	-		69.nnn.nnn.nnn	PPPoE
69.nnn.nnn.nnn	255.255.255.255	69.nnn.nnn.nnn	LAN

```
```

LAN Information
Modem IP Address	192.168.0.1
Modem NetMask		255.255.0.0
DHCP Address		192.168.1.64

```
```

Devices on LAN
IP Address	MAC Address	Name	Status
69.nnn.nnn.nnn	<mac>		-	active

```

**Now this last item is how/where my PC is getting the 69.XXX.XXX.XXX address you were questioning before.**
The IP and the MAC match my PCs eth0.

If I understand right what is happening, the modem allows me to connect to my ISP as though I were part of a LAN, and my computer is using a dhcp client to request an IP. If this is true I too am confused why I access the modem as 192.168.0.1, when modem and computer **BOTH** get a 69.XXX.XXX.XXX IP from my ISP. I only know that if set either of my NICS to 192.168.0.1 manually, then the PC can't request or receive webpages. (It appears setting one of the NICS to that IP "hides" the modem.) At first I DID set eth0 manually to 192.168.0.2, and it worked at first (to the internet)... but after one or two reboots, and restarting the eth0 and eth1 services a few times, it stopped.

I just re-verified that setting eth0 to 192.168.0.2 and restarting the net.eth0 service caused the browser to stop resolving addresses with the "Unable to connect" page showing up.

Here are the copies of my /etc/hosts, /etc/host.conf and /etc/conf.d/net files.

```

#/etc/hosts
127.0.0.1 pent3.bowyer.home pent3 localhost
#playing with some settings below, but currently not using anything but loopback above
#192.168.0.2 pent3

```
```

# /etc/host.conf:
# $Header: /var/cvsroot/gentoo/src/patchsets/glibc/extra/etc/host.conf,v 1.1 2006/09/29 23:52:23 vapier Exp $
# The  file /etc/host.conf contains configuration information specific to
# the resolver library.  It should contain one configuration keyword  per
# line,  followed by appropriate configuration information.  The keywords
# recognized are order, trim, mdns, multi, nospoof, spoof, and reorder.

# This keyword specifies how host lookups are to be performed. It
# should be followed by one or more lookup methods, separated by
# commas.  Valid methods are bind, hosts, and nis.
order hosts, bind

# Valid  values are on and off.  If set to on, the resolv+ library
# will return all valid addresses for a host that appears  in  the
# /etc/hosts  file,  instead  of  only  the first.  This is off by
# default, as it may cause a substantial performance loss at sites
# with large hosts files.
multi on

```
```

#/etc/conf.d/net
# This blank configuration will automatically use DHCP for any net.*
# scripts in /etc/init.d.  To create a more complete configuration,
# please review /etc/conf.d/net.example and save your configuration
# in /etc/conf.d/net (this file :]!).

#default system WAS working
#config_eth0=( "192.168.0.2" )

#### Internet Working ####
#eth0 is my Internet link
config_eth0=( "dhcp" )
#eth1 is my network link
config_eth1=( "192.168.0.3 broadcast 192.168.0.255 netmask 255.255.255.0" )

```

The /etc/conf.d/net file also supports the following option which I am not using, could it be of help?
routes_eth1=( "default gw XXX.XXX.XXX.X" )


**All of the above is the modem and the gentoo PC now connected directly to the modem by eth0.**
One slight improvement, after changing the gentoo eth1 config to

config_eth1=( "192.168.0.3 broadcast 192.168.0.255 netmask 255.255.255.0" )

in the /etc/init.d/net file, I don't block my access to the internet when eth1 is up. Still no joy getting the Ubuntu pc to connect, though.

As for the Ubuntu box, which WAS previously connected directly to the modem, I can't copy/paste the output of lspci or ifconfig, but ifconfig wasn't reporting an IP assigned to **it's** eth0. I'll try to type in the ifconfig output manually..... (I was also mucking about trying to change the hostname, but have reverted back to the hostname I was originally using. 

I just reran ifconfig in the Ubuntu machine and saw that it does report an IP address, but in IPv6... Hmmm, I have no idea if that might be the issue, I know I enabled IPv6 in the gentoo kernel at compile time, but haven't done anything else to setup use of IPv6 on the router box... and after previously reading the dhclient man pages, I know that it is dhclient pulling an IP out of it's reserve of cached addresses. The Ubuntu box is using onboard 3Com 3c940 10/100/1000Base-T Ethernet... 

On the Ubuntu box, running
```

#ping 192.168.0.3
conect: Network is unreachable.

```

Interesting result, after attempting the ping above, I had to stop the eth1 service on the gentoo box before previewing this post... it responded right after I stopped the service.

Does that provide enough information to help figure out what is happening here?

---

### Post by geoscope on 2007-03-04
On a side note, I took a couple networking courses at a local CC back in '98.It was in a Windows environment, but we covered OSI 7-layer and ABCDs. I remember just enough for you link to be a good refresher. I don't think we covered netmasking and I know we didn't learn about IPv6, which probably postdate the courses.

So, I have *some* idea what is going on, but not enough. As near as I can narrow down the problem I'm having, it could be one of about 3 or 4 things.

1. dhclient configuration on the Ubuntu box. (I *think* the setup of dhcp using dhcpcd (as a client) and netmasq (dhcp and DNS services) on the gentoo box is set up right. Although, iptables setup (for NAT, IP forwarding and drop packets) might be interfering.)

2. The use of IPv6 on the Ubuntu box.

3. Local LAN vs ISP LAN conflict in setting the gentoo box IP. (But as I understand it, when a PC has more than one NIC, setting an IP is specifically establishing the device -- eth0 eth1 -- IP, not the PC itself. IE, it is eth0 that is being licensed the 68.XXX.XXX.XXX IP by my ISP, not the PC itself, and eth1 can be in the 192.168.XXX.XXX for the local network.)

3. Kernel IP configuration options on the gentoo box. (Learning more about kernel config and recompiling the kernel is preferably a last option to explore.)

If it is an IPv6 vs IPv4 issue (my intuition is telling that is what is happening), can I get the ubuntu box (AMD64, with 1000base-t) to use IPv4 instead of IPv6? I'm not at all sure why IPv6 is being used, whether is is just a Ubuntu default, or a requirement because of the hardware in that PC.

If you are willing to help, I'd rather wait for your input to this and the last post before exploring further... anything else I'd try would be reckless at this point, and I be likely to mess up something fierce...

---

### Post by Mr. C. on 2007-03-04
Ok, all very good information.

I can see where you're having some confusion.

First... you most likely DO NOT need the setting:

  Yes, use public IP address.	X (This option set, and is why the modem has IP 192.168.0.1)

and your comment there isn't correct.  This setting allows INTERNAL LAN devices to see the PUBLIC WAN address as internal.  In all likelihood, you do not need this.  Disable it.  This is what's setting that extra route in your route table that you were unsure about.  Non of your internal boxes will ever use that address.

Lets clarify some details:

1) WAN Address (public, how people access you):

2) LAN1 address for modem <-> routing pc (gentoo linux, if i recall correctly.  this address is private, ONLY accessible to the modem/routing pc)

3) LAN2 address for routing pc <-> to single-nic'd pc (ubuntu, IIRC, this address is private, ONLY accessible from your your single-nic'd PC and routing pc).

The WAN address is :  69.224.151.181.
Its provided to you, and you don't need to worry about it.  Only outsiders need / use it.

The LAN address is set to 192.168.0.1, as shown in your details.  However, it shows a netmask of 255.255.0.0.  This means that the entire address range from:

    192.168.0.0 to 192.168.255.255 

belongs to that LAN.  You cannot use any address inside that range for your LAN2.  The shorthand address for this network is 192.168/16 (16 bits for network, 16 for hosts).

Therefore, you must pick a different LAN2 network.  Let's change it to a different range of private addresses altogether so that you can better debug and see what's happening in your routing tables.

LAN2 will be 10.0.0.0/8.  This means IPs 10.0.0.0 to 10.255.255.255.  You can chose the IP address you desire from this range for the nic connected to LAN2 on your routing PC.  Its conventional to use the .1 address, so pick 10.0.0.1.  Assign this IP to your LAN2 nic on the routing PC.  Your netmask for this network is 10.255.255.255.

And change your DHCP configuration to give out IP address in the range, of say, 10.0.1.1 to 10.0.1.254.  These are within the network, and will help you to see things better as you debug.  

The single nic'd PC (ubuntu) has a gateway of 10.0.0.1.  Where does it get this?  From your DHCP server on the routing PC that you configured.  This means all traffic from the 10.x.x.x network MUST go to the 10.0.0.1 NIC to be forwarded.

Now, since you want to route on your routing PC, you must add a route to move traffic from the 10/8 network to all other locations.  Your routing system *know* its own interfaces and how to get to both the 10/8 network and the 192.168/16 network, because it is directly connected.  What it needs to be told is where to forward all *other* traffic.  And that will be to the gateway address if your router (from your internal systems point of view - this is 192.168.0.1 - the modem's LAN interface.

What I would suggest is first, remove DHCP from the equation.  Assign static IPs to all interfaces as described above; then and only then when all things are working, work on the DHCP server.

Make sense?
MrC

---

### Post by geoscope on 2007-03-04
> **Mr. C. said:**
> 
Lets clarify some details:

1) WAN Address (public, how people access you):

2) LAN1 address for modem <-> routing pc (gentoo linux, if i recall correctly.  this address is private, ONLY accessible to the modem/routing pc)

3) LAN2 address for routing pc <-> to single-nic'd pc (ubuntu, IIRC, this address is private, ONLY accessible from your your single-nic'd PC and routing pc).

The WAN address is :  69.224.151.181.
Its provided to you, and you don't need to worry about it.  Only outsiders need / use it.


I knew the above. 

> 
The LAN address is set to 192.168.0.1, as shown in your details.  However, it shows a netmask of 255.255.0.0.  This means that the entire address range from:

    192.168.0.0 to 192.168.255.255 

belongs to that LAN.  You cannot use any address inside that range for your LAN2.  The shorthand address for this network is 192.168/16 (16 bits for network, 16 for hosts).


That the modem set the netmask to cover the whole range of addresses I missed. Thanks for pointing that out. I am sure that is why every time my eth1 has been actively trying to use an address in that range, that the modem quit responding.

At this point between other reading I've done, and your suggestion to switch from the 10.0.0.0 private network from the 192.168.0.0 private, I now have the following.

/etc/conf.d/net
```

config_eth0=( "dhcp" )
#is the default gateway to the modem necessary?
#routes_eth0=( "default gw 192.168.0.1" )
config_eth1=( "10.0.0.1 netmask 255.0.0.0 broadcast 10.0.0.255" )

```

/etc/dnsmasq.conf
```

dhcp-range=10.0.1.1,10.0.1.254,72h

```

While I think of asking, is there any good reason not to give a device on an internal LAN an infinite lease? I'm given it a try now....


THANK you MR C! Both computers are now happily surfing the web. Now it's on to making sure the firewalling works and setting up the NFS mounts.

---

### Post by Mr. C. on 2007-03-04
I'm glad things are working - congratulations!

> **geoscope said:**
> 
```

config_eth0=( "dhcp" )
#is the default gateway to the modem necessary?
#routes_eth0=( "default gw 192.168.0.1" )
config_eth1=( "10.0.0.1 netmask 255.0.0.0 broadcast 10.0.0.255" )

```

There is one problem here.  10/8 networks has a broadcast address of 10.255.255.255.  Think about it: you want to send to ALL hosts on the subnet, so ALL hosts parts must be 1.  Again, see: [http://cis68c2.mikecappella.com/files/cis68c2/02-lecture-datadelivery.pdf](http://cis68c2.mikecappella.com/files/cis68c2/02-lecture-datadelivery.pdf)

> **geoscope said:**
> 
While I think of asking, is there any good reason not to give a device on an internal LAN an infinite lease? I'm given it a try now....

No, not in your environment.  Your choice.  You certainly would have trouble of you had more systems that leases available!  But there's no real advantage to an overly long lease.  I actually use DHCP with static-leases (bind MAC address to an leased IP address - gives you the dynamic stuff like DNS servers, etc. but also maintains the IP if possible).

> **geoscope said:**
> 
THANK you MR C! Both computers are now happily surfing the web. Now it's on to making sure the firewalling works and setting up the NFS mounts.

Fantastic!  And, you're welcome!
MrC

---

