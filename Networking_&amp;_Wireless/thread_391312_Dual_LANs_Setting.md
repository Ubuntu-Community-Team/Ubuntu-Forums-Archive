---
title: "Dual LANs Setting"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by mchan on 2007-03-23
I installed 6.10 as LAN router and have trouble in dhcpd.config
The environment Ubuntu is in a 192.168.1.xx network.

Like to use Ubuntu as dhcp server for 10.0.0.xx

eth0(WAN): 192.168.1.16 (internet connection from LinkSys router assigned )
subnetmask: 255.255.255.0
GW: 192.168.1.1 
DNS: 192.168.1.1 (ISP DNS ???)

eth1-eth8 (LAN): 10.0.0.xx
subnet Mask: 255.255.255.0
GW:10.0.0.1
DNS: (ISP DNS ???)

Can any one please provide suggestion?
Thank you in advance.

---

### Post by netztier on 2007-03-23
> **mchan said:**
> I installed 6.10 as LAN router and have trouble in dhcpd.config
The environment Ubuntu is in a 192.168.1.xx network.

Like to use Ubuntu as dhcp server for 10.0.0.xx


I'd like to ask the obvious question back: What is your motivation to cascade two routers? If it's just to play around and learn, ok. But to actually use it for a "working" environment, I don't see the benefit of having a router behind a router.

Then again, I have no clue about what you are trying to achieve, so I better shut up ;-)

> **mchan said:**
> 
eth0(WAN): 192.168.1.16 (internet connection from LinkSys router assigned )
subnetmask: 255.255.255.0
GW: 192.168.1.1 
DNS: 192.168.1.1 (ISP DNS ???)


Getting 192.168.1.1 as DNS is ok, since the Linksys router probably running a DHCP proxy service that will forward the requests to the ISPs DNS servers.

> **mchan said:**
> 
eth1-eth8 (LAN): 10.0.0.xx
subnet Mask: 255.255.255.0
GW:10.0.0.1
DNS: (ISP DNS ???)


Ehm.. you are running eight LAN interfaces in that Linksys router? Eight NICs? Well.. wouldn't two NICs (one internal, one external) and an internal 8-port switch have been a lot cheaper and easier to configure?

Because with 7 internal NICs, you'd have to either assign one distinct IP subnet per NIC and configure your DHCP server to listen to these 7 NICs, with a separate address pool per NIC. Good exercise, but somewhat missing the point. 

[INDENT][SIZE="1"]Sorry, making assumptions again, I still don't have the slightest idea what your network plans are...[/SIZE][/INDENT]

To explain, I take the liberty to assume that you intend to have one external NIC with DHCP client and one internal NIC with DHCP server for the clients on.

In **/etc/network/interfaces** on the Ubuntu router, we should have something like this:

```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
 address 10.0.0.1
 netmask 255.255.255.0
 broadcast 10.0.0.255

```
And with the help of DHCP, the **/etc/resolv.conf** on the ubuntu router should contain a line like this:
```

nameserver 192.168.1.1

```


Now, what your DHCP server (make sure it does NOT listen on eth0!) must tell it's clients is this:

[INDENT]IP address: 10.0.0.xxx
Subnet Mask: 255.255.255.0
Def.GW: 10.0.0.1 [SIZE="1"](i.e. the IP address on the internal NIC of your ubuntu router)[/SIZE]
DNS: 192.168.1.1 
[/INDENT]

However, with 192.168.0.1 as DNS, your DHCP clients will only be able to talk to the DNS proxy on the Linksys router (and thus resolve hostnames), *after* you have the routing feature on the Ubuntu router up and running. If the ubuntu router won't to NAT (this depends on the way you configure it), you'll have to add one static route on the Linksys router, too:

[INDENT]IP network: 10.0.0.0 
Netmask: 255.255.2550
Next hop: 192.168.1.16 [SIZE="1"](i.e. the external address of your Ubuntu router)[/SIZE][/INDENT]

best regards

Marc

---

### Post by mchan on 2007-03-30
Marc,
Thank you for your comment, I am trying to build a Router from a old PC that is a subnet from a internal network already.
For user accounting purpose, I want to create a second subnet, the suggestion that you provided work in subnet dhcp client assignment but no Internet, however, the Router eth0 is getting Internet access from Linksys router, but the eth1 is not talking to eth0, thus no access to Web.
Can you please provide some suggestion as how to bridge eth0 to eth1 (subnet 10.0.0xxx)
Regards, Michael

---

### Post by mchan on 2007-03-30
Marc, Please confirm the following :

// Now, what your DHCP server (make sure it does NOT listen on eth0!) must tell it's clients is this:

    IP address: 10.0.0.xxx
    Subnet Mask: 255.255.255.0
    Def.GW: 10.0.0.1 (i.e. the IP address on the internal NIC of your ubuntu router)
    DNS: 192.168.1.1
//

1. Where do I insert these comment?

//
However, with 192.168.0.1 as DNS, your DHCP clients will only be able to talk to the DNS proxy on the Linksys router (and thus resolve hostnames), after you have the routing feature on the Ubuntu router up and running. If the ubuntu router won't to NAT (this depends on the way you configure it), you'll have to add one static route on the Linksys router, too:

    IP network: 10.0.0.0
    Netmask: 255.255.2550
    Next hop: 192.168.1.16 (i.e. the external address of your Ubuntu router)
//

1. Can I also used my ISP's DNS 1/2 as DNS gateway?
2. How do I set the NAT on Ubuntu?
3. Do you mean the Application (Port forwarding) or something else (Advance Routing/Ststic   routing)? 
4. If I am using the Linksys static routing table, 
    Do I use eth1 IP address (10.0.0.11), I cannot enter "10.0.0.0" into the box?
FYI: When I click "save", the entry showed the IP address of eth1 of Ubuntu
5. Do I use the eth0 IP address as the gateway (Static IP assigned by Linksys 192.168.1.16)?
Thank you in advance,
regards, Michael

---

### Post by Mr. C. on 2007-03-30
Mchan,

I think you confusing a number of distinct concepts, and it would be worth your while to spend a little time sorting them all out.  I would recommend that you not try to tackle everything at once, but instead focus on getting one component to work at a time.  You seem to want to learn this stuff, but your questions feel almost random, jumping from topic to topic.  In my experience, this typically means misunderstandings.

I am understanding you want:

1) to build a router to route between two (or more) distinct subnets
2) to configure a DHCP server to provide internet addresses to one or more of those subnets

If this is correct, I will suggest better understanding of the following:

1) basic IP requirements for an interface (eg. IP address, netmask, broadcast, gateway)
2) subnets (i.e. distinct physical networks)
3) DNS servers
4) IP forwarding (routing) traffic from one subnet to another
5) DHCP server configuration, and its limitations

Spend some time reading the Notes, Course work, and Lab work here:

[http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

These materials should help clarify some concepts, and make your task much more rewarding.

MrC

---

### Post by mchan on 2007-03-30
Mrc,
Thank you for your comment and the link of resource,
Your guess is right that we want to provide one internet connection to different subnets, we have done it on a linksys (192.168.1.xx) to SMC (10.0.0.xx) router with static IP (192.168.1.xx) assigned to SMC.
However, we got stuck in the following when tried using the Ubuntu:
I use a Linux work station with 2 / 4 port PCI NIC
we set eth0 as dhcp client  from Linksys (192.168.1.xx) in according to the guided instruction, the linksys allow Internet access and assigned lan IP.
we try to set eth1-eth8 as the router ports acted as a subnet DHCP server with static ip assigned by Linksys but use subnet 10.0.0.xx on eth1-eth8. it did not worked
We got stuck on the eth1(We do not know how to assign Linksys (static) IP address or should we set it as DHCP?:
When we assigned static IP address to eth1 (10.0.0xx) and connect work station to eth1 port, client PC can received subnet ip 10.0.0.xx, and we can ping from router to other computers in either 192.168.1.xx network or 10.0.0.xx network through this Ubuntu router (DHCP) station, however, we cannot ping the gateway using this 10.0.0xx work station. 
IP forwarding is not seem to work in this Ubuntu, and we do not have any idea where to obtain these information or guide.
Any suggestions will be greatly appreciated.
regards,
Mchan

---

### Post by netztier on 2007-03-31
> **mchan said:**
> 
we try to set eth1-eth8 as the router ports acted as a subnet DHCP server with static ip assigned by Linksys but use subnet 10.0.0.xx on eth1-eth8. it did not worked


Here's an error. You need only **two** NICs or NIC ports, one for the internal LAN, one for the external LAN. You only need seven internal NICs if you want to connect seven different internal Subnets, such as 10.0.0.0 /24, 10.0.1.0 /24, 10.0.2.0 /24, 10.0.3.0 /24, 10.0.4.0 /24 etc. [COLOR="Gray"]( "/24" is an abbreviation for "subnet mask 255.255.255.0")[/COLOR] You'll live a happier life ;-) using a 8-port 10/100Mbps switch connected to the internal NIC, it's faster, a lot cheaper and configuration of the ubunitu router is a lot easier to understand and maintain.

[COLOR="Gray"](Technically, you cold group the seven internal NICs into a bridge group and give that bridge group the IP address of the "internal" NIC. But this misses the point by two miles.** Strongly discouraged**.)
[/COLOR]
> **mchan said:**
>  We got stuck on the eth1(We do not know how to assign Linksys (static) IP address or should we set it as DHCP?:

Set the external NIC (eth0) to DHCP and connect it to the linksys router. 

This is the configuration information the external NIC eth0 will obtain via DHCP from the Linksys router:

[INDENT][SIZE="2"]IP address: 192.168.0.xxx
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.0.1
DNS Server: 192.168.0.1[/SIZE][/INDENT]

Configure the internal NIC eth1 like this:
```
auto eth1
iface eth1 inet static
 address 10.0.0.1
 netmask 255.255.255.0
 broadcast 10.0.0.255

```

Nota: **No gateway** setting for the internal NIC! Reason: per system, there can only be **one** default route, and in this case, your ubuntu router has already learnt that one via DHCP. Check the routing table with **netstat -nr** or **route**. Now you should see something like follows. Note the default route (Destination 0.0.0.0, Mask 0.0.0.0) how it points to 192.168.0.1 via eth0. the 10.0.0.0/255.255.255.0 network however is "directly connected" via eth1.

```
user@ubuntu-router:~$ **netstat -nr**
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
[COLOR="Red"]0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0[/COLOR]
10.0.0.0        0.0.0.0		255.255.255.0   U         0 0          0 eth1

```

> **mchan said:**
> 
When we assigned static IP address to eth1 (10.0.0xx) and connect work station to eth1 port, client PC can received subnet ip 10.0.0.xx, and we can ping from router to other computers in either 192.168.1.xx network or 10.0.0.xx network through this Ubuntu router (DHCP) station, however, we cannot ping the gateway using this 10.0.0xx work station. 

That's expected. Each computer - having dual NICs or not - has to look at it's routing table to determine the interface it has to send the IP packet through. If the routing table does not contain an entry that matches the packet's destination address, it will be discarded with a "no route to host" error. This also applies to a router, be that a Linksys, SMC or Ubuntu-based device.

Now if you have only one NIC in the computer, this are not difficult: if the IP packet destination address is on the same subnet, it just sends it out that interface. Period. If the destination address is on a different subnet... eh. what do we do with that? There wont' be any matching entry in the table so we're stuck. 

Not quite. Default routing comes to the rescue: it's the "last" entry in the table, and if there was no match with the previous entries, it'll use this one. So the packet is sent to the gateway address of the default route (and we silently hope that the computer that receives it will know where to send it).

This happens on *every* system talking TCP/IP and it happens in *both directions* independently! 

Lets have an example, based on your network. We have the following players:

[LIST][COLOR="Red"][*] Linksys Router, has a WAN NIC (address from ISP, unknown) and a LAN-NIC with 192.168.0.1[/COLOR][COLOR="Navy"][*] a PC connected to the Linksys Router, has obtained 192.168.0.10 via DHCP from the Linksys.[/COLOR][COLOR="DarkGreen"][*] our Ubuntu router. Has it's eth0 connected to the Linksys and has obtained 192.168.0.11 for it. Has it's eth1 connected to another switch and has 10.0.0.1 configured statically for it. It runs a DHCP server that gives out 10.0.0.xxx addresses to clients on the network at eth1.[/COLOR][COLOR="DarkRed"][*] a PC on the "inside" network has it's eth0 connected to the switch and has obtained 10.0.0.25 as address from the Ubuntu router's DHCP server.[/COLOR]
[/LIST]

The task is to send an ICMP Echo Request Packet (also known as "ping") from 10.0.0.25 to 192.168.0.10. Here's what happens:

[LIST][COLOR="DarkRed"][*] packet gets prepared. Destination is 192.168.0.10, source is 10.0.0.25
[*] routing table is consulted: We have one route for 10.0.0.0/255.255.255.0 going out through eth0. No match. Is there a default route? yes. So we match it against this one. It says that the gateway is 10.0.0.1, which is eth1 of our Ubuntu router.
[*] we formulate the packet to go to the eth1 MAC-address of our Ubuntu router and send it out through eth0. Destination is still 192.168.0.10, source is still 10.0.0.25[/COLOR]
[COLOR="DarkGreen"][*] the ubuntu router receives the packet on eth1. All it looks at is the destination address.
[*] the destination is matched against the routing table. we have an entry for 192.168.0.0/255.255.255.0 going out through eth0. We send out the packet to 192.168.0.10, out of eth0[/COLOR]
[COLOR="Navy"][*] now on the system with 192.168.0.10, the packet is properly received. It is a ping request which gets processed by the ICMP functions in the TCP/IP implementation. The function defines that a reply packet must be sent.
[*] reply packet gets prepared. Destination is 10.0.0.25, source is 192.168.0.10
[*] routing table is consulted. We have one route for 192.168.0.0/255.255.255.0 going out through eth0. No match.
[*] we don't have a route to 10.0.0.25 or any 10.* networks. That's bad.
[*] ah, but we have a default route: 0.0.0.0/0.0.0.0 is reachable via the gateway at 192.168.0.1, and that we know to be reachable via  eth0. That's convenient, let's send it there.
[*] packet gets formulated (source 192.168.0.25, destination 10.0.0.25) and is sent to the MAC-address of the Linksys Router's  LAN-Interface[/COLOR]
[COLOR="Red"][*] on the Linksys Router, the packet is received on the LAN interface. All it looks at is the destination address (still 10.0.0.25)
[*] the destination is matched against the routing table. We have an entry for 192.168.0.0/255.255.255.0, going out through the LAN interface. No match. No entry for 10.0.0.0/255.255.255.0. Bad. Ah. but we have default route, pointing to some IP address at our ISP, going out through our WAN interface, so let's send it there....[/COLOR]
**[*] Oh sh*t.. the reply packet's gone to the Internet! it should've gone to the 192.168.0.11 address on eth0 of the ubuntu router!**
[/LIST]

In this scenario, you might omit the part with the intermediate 192.168.0.10 system altogether - the problem is the same when you ping the Linksys Router. The Linksys does not (yet) know that  10.0.0.0/255.255.255.0 can be reached via eth0 (192.168.0.11) of the ubuntu router.

> **mchan said:**
> 
IP forwarding is not seem to work in this Ubuntu, and we do not have any idea where to obtain these information or guide.

I beg to differ. I bet that IP forwarding *does* work. But you still need to add a **static route** to the Linksys router. You **must** tell it that 10.0.0.0/255.255.255.0 can be reached via 192.168.0.11, which is eth0 of your ubuntu router. Check the Linksys' web-based configuration. You should be able to add a static route there.

That is what one could call "classic IP routing". I suggest you read the documents by MrC (they're good!), and in parallel, you can learn and understand what is going on in your network. Once you've gained the in-depth understandig, you'll know exactly how your network is operating - troubleshooting will become easy

[INDENT][SIZE="1"]A side note: 
If however your Ubuntu router is configured to do *NAT/PAT* (Network Address Translation/Port Address Translation), which is also known as "IP Masquerading" or "IP Hiding", it will mangle the source IP addresses on the IP packets it sends out of eth0.

To devices on the network connected to eth0, every packet will look as if it came from 192.168.0.11 itself, even if originally, they come from some 10.0.0.xxx address. These systems will believe that they're "talking to" just another 192.168.0.yyy address on their LAN, and they will never need to forward a packet to the default gateway, and no routing problems seem to occur.

This NAT/PAT is the **standard** way the common broadband routers from Linksys, NetGear, SMC etc are operating. That's why you can cascade them one behind the other and things just "seem to work" - where in reality, a whole lot of complicated things are going on behind the scenes. NAT/PAT is not trivial!
[/SIZE][/INDENT]

Best regards

Marc

---

### Post by mchan on 2007-03-31
Marc,
Thank you for all of these detailed instruction, I am working with a co-op students doing this project for building a router in providing 5GHz wi-fi signal to a community, with your instruction and advices, it is clear for us to move forward with this core router project as the heart of our wi-fi APs in a remote cell site for affordable access.
I will detailed this project and send you a detailed installation method for future forum help so all ubuntu users can benefit in this. this is the power of networking at best.
BTW, Can you please tell me if ChilliSpot  can used in Ubuntu or you have better suggestion? 
regards,
Michael

---

### Post by netztier on 2007-03-31
> **mchan said:**
> 
Thank you for all of these detailed instruction, I am working with a co-op students doing this project for building a router in providing 5GHz wi-fi signal to a community, with your instruction and advices, it is clear for us to move forward with this core router project as the heart of our wi-fi APs in a remote cell site for affordable access.


5GHz? You mean Wireless LAN as per IEEE 802.11a? What about 802.11b/g (2.4Ghz) support? In Switzerland (and generally in Central Europe) where I live, 802.11a supporting hardware has not been common throughout the last years. It was available, yes, but not commonly. Here, setting up a (public) WLAN with 802.11a only would miss the point completely. I don't now what the WLAN market in your country looks like, though.

Now if you consider hooking up a whole bunch of WLAN access points to your Ubuntu based router, the idea with the eight internal NICs doesn't seem so "wrong" after all. I apologise for repeatedly pointing out this idea as a "mistake". Like this, you can connect multiple access points per internal LAN segment, let's say 4-5 APs and one IP subnet per building, each connected to it's own internal NIC (eth1 - eth8) of the Ubuntu router.

> **mchan said:**
>  BTW, Can you please tell me if ChilliSpot  can used in Ubuntu or you have better suggestion? 

No, I don't have any better suggestion - I didn't even know that ChilliSpot existed. I've been (though not very eagerly) looking for such an open source solution that could replace the Windows based Cisco BBSM server I run for that purpose at work. But it's nearing it's EOL, and I have to find an alternative, thank you for pointing me to ChilliSpot!

At work, I run a WLAN that covers almost our entire building. A few dozen guests, contractors and the customers of a conference centre in our building use it ervery day. There's always at least 20 people online, and they are connecting through that Cisco BBSM captive portal that does roughly the same thing I think that ChilliSpot can do. It seems to be available for Debian, so if you read it's documentation carefully and make sure that you meet it's package dependencies, you might be able to make it work by simply installing it's .deb package.

The problem we had however was not with the portal, but with the SOHO-class xDSL router we used to connect to the Internet (it was a ZyXEL Prestige 650 at the time). Every so often, up to twice week, we had to reset it because it would not allow new connections to be established. We suspected that this was because it's NAT/PAT table had overflown and it needed a reset. Especially with file sharing, Skype and the like, the number of simultaneous connections increases very much, compared to normal HTTP surfing and POP/IMAP mailing.

The more clients the network had, the more often a reset was necessary. Finally, together with the change from xDSL to Cable, I replaced the ZyXEL box by a Cisco 2691 router with IOS 12.4. And the problem was fixed, once and for all.

What I suggest is this: If you're building a large environment and you expect a lot of simultaneous customers, dont' use a small SOHO-class router to do the NAT/PAT for the Internet access. Instead, consider hooking up the Ubuntu router's external NIC eth0 directly to the ISP connection and let the Ubuntu machine to the NAT/PAT and firewalling job. You'll have to run iptables and configuration will become more complex - but the config basics as they have been suggested in this thread will remain the same. You can start off with the Linksys remaining in place and then changing it later.

best regards

Marc

---

### Post by mchan on 2007-04-01
Marc,
I assume that you are located in Central Europe, I like to visit there when I got a chance. Just to let you know that 5 GHz and 2 GHz are compatable with dual LAN  PCI  module but the 5GHz (802.11 A has more channels than 802.11G/B) and with IEEE RFC in place, the 5 GHz simply have better throughput in Video on demand speed up to 108 mbp with directional antenna and better quality in Video Conference.
The market in North America is good with 5GHz, our intention is to provide remote regions another Broadband option other than dominated by Cable (15KM per headend repeater  or 1000 househlods) where ADSL only good within 18000 feet of range.
We currently using ADSL and Fiber to all of our core routers, FYI, we only use the linksys as a simulated Internet Access. The Project that I assigned to this student is for the University of Victoria Co-op program, and I am putting him right into the fire so he can get the hands on experience, and I am much appricated your comment and technical knowledge.
As to your comment in regarding to replace the Cisco, the DD-WRT for X86 is also one of the best hot spot firmware which allow Captive portal and walled garden feature.
If you are comfortable with BSD, PFSense also good, and during our last co-op assignment with SFU, my 4th year co-op student showed me that it is harder to config compared to dd-wrt (Debian) by a 2nd year co-op student. I am not yet tried the ChiliSPot yet.
BTW. The 4 port router broad I am using for this core router is from Mikrotik, we are using it to send out wireless signal using 900MHz (54Mbp) for NLOS regions and backhaul, and 5 GHz for IPTV and 2 GHz for WLAN purpose.
I hope this will generate some interest for your group in your regions.
I like to take this opportunity to express my thanks to you and your group offer this forum. 
One side note, what do you think of the opportunity for us to make a Ubuntu desktop CD with all packages installed to compete MS as alternative.
I like to offer this Ubuntu Desktop version for people in SOuth Africa and Latin America, China and India etc but not sure that I can do this alone.
I installed Ubuntu along with all the packages even firmware cutter and NDIS wrapper and NDIS GTK for a linksys PCMCIA card which not supported by UBUNTU, I am totally blow away from this OS packages, but for the average PC users, I think it is a little too much but if we can water down the packages and allow the typical useful packages, I believe it willknock off MS if we can use this OS to expand the users base and make Broadband universal access affordable.
Please comment.
Michael

---

### Post by mchan on 2007-04-02
Marc,
Currently we have internet access from eth0, received dhcp address from Linksys DHCP server as192.168.1.102 ,and we can use eth0 to eth1. However, we dont have access to any website through my browser of my laptop through eth1 port, DHCP assigned 10.0.0.xx address as intended and we can ping outside (domain and public IP) using dos.
Can you please look at this file,
Thank you in advance.
Michael 
/////////////////////////////////////////////////////////////////
Config file:
//////////////////////////////////////////////////////////////////


#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style ad-hoc;

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers 10.0.0.1;

default-lease-time 600000000;
max-lease-time 720000000;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}
# eth1 subnet
subnet 10.0.0.0 netmask 255.255.255.0 {
	range 10.0.0.100 10.0.0.200;
	option routers 10.0.0.11;
	option broadcast-address 10.0.0.255;
	}
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
This is the ip routing table
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
root@citiwidecorerouter:~# netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.0.0        0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
This is the Network Interface file:
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
 address 10.0.0.11
 netmask 255.255.255.0
 ////////////////////////////////////////////////////////////////
Linksys Static Route:
////////////////////////////////////////////////////////////////////
destination ip: 10.0.0.0
sub mask: 255.255.255.0
gw: 10.0.0.1? (should we set this to 10.0.0.11 as our eth1)

---

### Post by netztier on 2007-04-03
> **mchan said:**
> Marc,
Currently we have internet access from eth0, received dhcp address from Linksys DHCP server as192.168.1.102 ,and we can use eth0 to eth1. However, we dont have access to any website through my browser of my laptop through eth1 port, DHCP assigned 10.0.0.xx address as intended and we can ping outside (domain and public IP) using dos.


Sounds good. Basic IP connectivity seems to be there. But I think you have a DNS problem.

> **mchan said:**
> 
/////////////////////////////////////////////////////////////////
Config file:
//////////////////////////////////////////////////////////////////


For future copy&paste of config file excerpts, please use the [C0DE]...[/C0DE] tags available. Just mark the text and use the button with the # sign from the toolbar. It makes reading so much easier.


> ```
...
# option definitions common to all supported networks...
option domain-name "example.org";
[COLOR="Red"]option domain-name-servers 10.0.0.1;[/COLOR]

default-lease-time 600000000;
max-lease-time 720000000;
...
```

Ah. So your DHCP server is telling it's clients that they should use the DNS that is running on your Ubuntu router at the IP address 10.0.0.1. I don't think you mentioned that there would be a DNS running on your Ubuntu router, or did you? Besides.. who is 10.0.0.1 anyway? Your configuration doesn't have that IP address on any of the interfaces ;-)

Here, you'll have to tell which IP address your clients should be using as DNS, and that will have to be ... well up to you to find out what your ISPs DNS servers are. ;-). To start, you can tell the clients to use the DNS proxy function on the Linksys router, so you give them the "option domain-name-servers 192.168.1.1;". It's perfectly ok to assign a DNS server that is in some other subnet, it doesn't have to be local.

Another thing: In the place where you configured this, is becomes "global" parameter, it will be the same value vor all DHCP scopes/ranges you'll define, for every subnet this DHCP server is going to serve. This can be ok, depending on the intended network topology. 

> ```
# eth1 subnet
subnet 10.0.0.0 netmask 255.255.255.0 {
	range 10.0.0.100 10.0.0.200;
	[COLOR="Red"]option routers 10.0.0.11;[/COLOR]
	option broadcast-address 10.0.0.255;
	}
```


However I am sure that you can add the "option domain-name-server ...." also in this section, so that different subnets can get different values. You can define a list of IP addresses (it's better if there's two or more!). If you'll be running multiple client subnets, you can even round-robin the sequence of the addresses, so the DNS load your clients generate can be distributed a bit to the DNS servers. 

In extenso: 
clients on eth1 get a sequence of <IP of DNS A>;<IP of DNS B>;<IP of DNS C>
clients on eth2 get a sequence of <IP of DNS B>;<IP of DNS C>;<IP of DNS A>
clients on eth3 get a sequence of <IP of DNS C>;<IP of DNS A>;<IP of DNS B>

But that's for later - I assume that you are still testing things, so 192.168.1.1 is good enough for now.

About [COLOR="red"]option routers:[/COLOR] is 10.0.0.11 the actual IP address of eth1 on your ubuntu router?          [COLOR="SeaGreen"]ah.. I just checked the config file below, yes it is.[/COLOR]

> ```
root@citiwidecorerouter:~# netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.0.0        0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
```

Looks goot to me. First and second entries are so-called **directly connected** routes, while the last one is the **default route**.

> This is the Network Interface file:
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
 address 10.0.0.11
 netmask 255.255.255.0
```

Yepp,  makes perfect sense - although I think consistently choosing the first IP address in the subnet for the router is better. **Suggestion:** use 10.0.0.1 for the router, and don't forget to adapt the "option routers" statement in the DHCP server configuration!

> ```
Linksys Static Route:
destination ip: 10.0.0.0
sub mask: 255.255.255.0
[COLOR="red"]gw: 10.0.0.1[/COLOR]?
``` (should we set this to 10.0.0.11 as our eth1)

Error here. If ever you configure so-called **static routes**, you must make sure that the address you configure as "next hop" or "gateway" is reachable **directly**. When forwarding the packet along a static route, the router must be able to determine which of it's interfaces to use as egress port (right: with the help of it's own routing table). Such an egress port however is always part of a "directly connected" network - and therefore any "next hop" for a static route must be part of (one of) the directly connected network(s). That is - of the right one of the (possibly multiple) connected networks, of course.

**What you'll have to enter here is: 192.168.1.102.** The Linksys should send packets destined for 10.0.0.0/255.255.255.0 to 192.168.1.102. The problem now might be that tomorrow, eth0 of your ubuntu router may get assigned another IP address via DHCP - bad luck!

;-) Not quite, of course. Two ways out of this (pick any):
[LIST][*][COLOR="Navy"] on the Linksys Router, configure a "static DHCP lease" or a "DHCP reservation" (can't remember their terminology), so that eth0's MAC address will always obtain 192.168.1.102.[/COLOR]
[*][COLOR="DarkGreen"] on eth0, also do a static IP configuration, making sure that the address you use is *outside* the address block that the Linksys DHCP-Server uses for it's clients. You could use 192.168.1.10, for example. This would then look like this: 
```
auto eth0
iface eth0 inet static
 address 192.168.1.10
 netmask 255.255.255.0
 gateway 192.168.1.1 (yes, here, you need a gateway entry!)
```
and now, since the DHCP client program won't do this automatically anymore, you have to modify your /etc/resolv.conf manually to read:
```
 nameserver 192.168.1.1 
```
And of course, you'll have to change the static route on the Linksys for 10.0.0.0/255.255.255.0 to use 192.168.1.10 as next hop, not .102 anymore.[/COLOR]
[/LIST]


Best regards

Marc

---

### Post by mchan on 2007-04-03
Marc,
Please confirm the following scripts I based on your suggestion,
Thank you in advancel.
Michael

###
   option domain-name "example.org";
#option domain-name-servers 10.0.0.1; <Changed to 192.168.1.1>

###
# eth1 subnet
subnet 10.0.0.0 netmask 255.255.255.0 {
	range 10.0.0.100 10.0.0.200;
	option routers 10.0.0.11;
	option broadcast-address 10.0.0.255;
        option domain-name-servers 10.0.0.1; <Changed to 192.168.1.1>
	}
###
(Network Interface)

eth0
iface eth0 inet dhcp
###
auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1 (yes, here, you need a gateway entry!)


auto eth1
iface eth1 inet static
address 10.0.0.11
netmask 255.255.255.0
option domain-name-servers 10.0.0.1; <Changed to 192.168.1.1>

###
modify: /etc/resolv.conf manually
see:
nameserver 192.168.1.1

###
(Linksys Static Route)
Linksys Static Route:
destination ip: 10.0.0.0
sub mask: 255.255.255.0
gw: 10.0.0.1? <192.168.1.102 or Static eth0 IP address of 192.168.1.xx>

---

### Post by netztier on 2007-04-03
> **mchan said:**
> Marc,
Please confirm the following scripts I based on your suggestion,
Thank you in advancel.
Michael

###
   option domain-name "example.org";
#option domain-name-servers 10.0.0.1; <Changed to 192.168.1.1>

###
# eth1 subnet
subnet 10.0.0.0 netmask 255.255.255.0 {
	range 10.0.0.100 10.0.0.200;
	option routers 10.0.0.11;
	option broadcast-address 10.0.0.255;
        option domain-name-servers 10.0.0.1; <Changed to 192.168.1.1>
	}
###


Please use **QUOTE-** and   **CODE**-tags, so the reader can clearly identify what is part of a config file and what isn't. Please write the config file excerpts as precisely as you would write them in the file. I know - Ididn't always follow that rule myself, my bad. 

The "option domain-name-servers <ip-address>" ist *either* in the global part *or* in the interface-specific part of your configuration. I would not add it in both since this will cause confusion when troubleshooting; I suggest you use it in the interface/subnet-specific part only.

So the excerpt of the DHCP server config file will be:

```
# eth1 subnet
subnet 10.0.0.0 netmask 255.255.255.0 {
	range 10.0.0.100 10.0.0.200;
	option routers 10.0.0.11;
	option broadcast-address 10.0.0.255;
        option domain-name-servers 10.0.0.1; <Changed to 192.168.1.1>
	}
###
```

> **mchan said:**
> 
(Network Interface)

eth0
[COLOR="Red"]iface eth0 inet dhcp[/COLOR]
###
auto eth0
[COLOR="DarkGreen"]iface eth0 inet static[/COLOR]
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1 (yes, here, you need a gateway entry!)


So you're changing from DHCP to static in the 192.168.1.0-LAN, good. Of course, you need to remove the comment I added in (... ) on the "gateway ..." line. If you go static for **eth0**, you have to remove [COLOR="Red"]iface eth0 inet dhcp [/COLOR], you can't have both of these mutually exclusive statements in /etc/network/interfaces.

> **mchan said:**
> 
auto eth1
iface eth1 inet static
address 10.0.0.11
netmask 255.255.255.0
[COLOR="Red"]option domain-name-servers 10.0.0.1; <Changed to 192.168.1.1>[/COLOR]


Now you're confusing things. "option domain-name-servers..." is part of the DHCP server configuration, not of /etc/network/interfaces. That makes it look like this:

```

auto eth0
 iface eth0 inet static
 address 192.168.1.10
 netmask 255.255.255.0
 gateway 192.168.1.1

auto eth1
 iface eth1 inet static
 address 10.0.0.11
 netmask 255.255.255.0

```

> **mchan said:**
> 
###
modify: /etc/resolv.conf manually
see:
nameserver 192.168.1.1


Correct. 


> **mchan said:**
> 
###
(Linksys Static Route)
Linksys Static Route:
destination ip: 10.0.0.0
sub mask: 255.255.255.0
gw: 10.0.0.1? <192.168.1.102 or Static eth0 IP address of 192.168.1.xx>


The next hop for this static route is now of course 192.168.1.10, since eth0 of your Ubuntu Router now is 192.168.1.10.

best regards

Marc

---

### Post by mchan on 2007-04-04
Mac,
We finally got this dhcp server working perfectly with all 8 NIC ( total of 8 diff. subnet from 192.168.3.xx - 192.168.11.xx) Each nic port assinged ip addresses within the subnets

i hope these info. will guide the next person who is new to this type of setup in ubuntu router! 

Here are the codes:

command: /etc/default/dhcp3-server
```

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1 eth2 eth3... ... eth8"
[\CODE]

command: /etc/dhcp3/dhcpd.conf
[code]
ddns-update-style ad-hoc;

option domain-name "example.org";
option domain-name-servers (dns of your isp); ie. 199.xx.xx.xx, 123.xx.xx.xx

default-lease-time 600000000;
max-lease-time 720000000;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

#eth1 subnet
subnet 192.168.4.0 netmask 255.255.255.0 {
        option subnet-mask 255.255.255.0;
        range 192.168.4.100 192.168.4.150;
        option routers 192.168.4.11;
        option broadcast-address 192.168.4.255;
}
#eth2 subnet
subnet 192.168.5.0 netmask 255.255.255.0 {
        option subnet-mask 255.255.255.0;
        range 192.168.5.100 192.168.5.150;
        option routers 192.168.5.11;
        option broadcast-address 192.168.5.255;
}

...so on up to eth8 subnet 

```
command: /etc/network/interfaces

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp //this could also be static assigned by adminstrator

auto eth1
iface eth1 inet static
        address 192.168.4.11
        netmask 255.255.255.0

auto eth2
iface eth2 inet static
        address 192.168.5.11
        netmask 255.255.255.0

auto eth3
iface eth3 inet static
        address 192.168.6.11
        netmask 255.255.255.0
...so on up to eht8

```

restart the network
restart dhcp3-server

Note 1: We spent many days on this project, so we did not have enough time to test the other cases; if you are interested, you could try this and reply post XD

Alternatives changes:
- eth0 to static IP
-set static route in linksys router (setup/advance routering)
-Torture test-we have not done test on performance using different laptops or workstations in different subnets simunltaneously.

Note 2: I used newiest version webmin 1.3.3.0 to act as my reference in the configuration.I also used the following command to read the result of my configuration through the webmin GUI: /etc/dhcp3/dhcpd.conf

Thanks for your guidance!

mchan

---

### Post by mchan on 2007-04-04
Marc,
Here is an update on our test using dual LANs at the same time pulling video off You Tube.

Core Router setting:
2.4 GHz P4 / 512 Ram
2 /4 port MikroTik PCI NIC

WAN / LAN Setting:
WAN ISP IP
Linksys LAN (2 servers / 4 workstations / 2 wireless aps / 6 wi-fi clients)
Core Router 8 / Subnet LANs ( 1 client / per NIC-2 NIC only )

(Test :
Both Clients download video files from YouTube at the same time

Result:
Smooth images 
Trailer1- (Did Hard 4)
Trailer2- Chinese movie clip from some site (We picked these 2 trailers because it is popular due to both trailers and its drawing power for real time distrbution from diferent audiences)

---

### Post by mchan on 2007-04-05
Can someone please provide some input of installation of ChiliSpot in a same box that runs the core router,
I am not sure if I can install ChiliSpot in a same box where I am runing it as a router with multiple subnets.

[https://help.ubuntu.com/community/WifiDocs/ChillispotHotspot](https://help.ubuntu.com/community/WifiDocs/ChillispotHotspot)

I installed a remote radius server along with Mysql etc in a different box in a remote IP address network, and like to use the UBUNTU router along with the ChiliSpot as a log-in splash greeting page to authenticate wireless users through remote AAA server.
Radius / MySQL in IP address: 139.142.xxx.xxx
ChiliSpot / Ubuntu Router Address: 154.24.xxx.xxx

Any advice welcome.

MC

---

### Post by mchan on 2007-05-24
Please take note the following ports must open for HotSpot access 

Chilli Config file on port forward:
*  Open port 443/TCP at least to the 192.168.182.0/24 subnet: Apache HTTPS port.
    * Open port 3990/TCP at least to the 192.168.182.0/24 subnet: port of Chillispot web server.
    * Open port 1812/UDP to 127.0.0.1 (probably all ports are already open to localhost): this is the port FreeRadius listens to, and Chillispot connects to it using that.
    * Open port 67/UDP to the VPN (probably the tun0 interface): this is used by Chillispot DHCP server to get requests for IP address registration. 

Also watch for the traffic load, the best torture test is using different wireless and wired PCs to log-in at the same time, during our test on the load balance, the actual x86 (800MHz) with 256MB seems to have no trouble but the Linksys router just hanged there, we have to log-in one at a time. (this most likely will be the environment in a hotspot) I do not foresee anytime will be all users log-in at the same time. but it is a good test for traffic management.

Mchan

---

