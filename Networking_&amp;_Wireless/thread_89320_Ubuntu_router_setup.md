---
title: "Ubuntu router setup"
date: 2005-11-12
forum: Networking &amp; Wireless
---

### Post by Ellias on 2005-11-12
Hello everyone,

I would very much like to set up a router on my home linux box. Let me describe my setup.

**192.168.0.1 (D-Link Router)----------- PC1
|
|
Switch------- PC2
|
|
Ubuntu Box (3 Nics) 
-eth2 192.168.0.102 External (going to switch)
-eth0 10.0.0.1 & eth1 10.0.0.2 Internal (connect to other PCs)

So far I have managed to get things working for one of them. Meaning that I have configured DHCP to assign the connecting computer on eth1 an IP, and successfully route traffic to eth2. DNS and IP forwarding are set up and I managed to get most of this information off of [www.aboutdebian.com](www.aboutdebian.com).

What I want is to get it working for both of them (eth0 and eth1) so that I can have something like this...

Internet+ other router + PCs
|
| (connecting to eth2)
Ubuntu Box
|
| (connections going from eth0 & eth1)
|
L Computer #1 (directly connected to Ubuntu, eth1)
|
L Computer #2 (directly connected to Ubuntu, eth0)

I want both computers to be able to resolve an IP, talk to eachother (aka ping) and connect to the internet. Like I said I have this working for eth1 but everytime I try and get it working for eth1 it stops working for eth0. What I did to try and get it to work for both was just mod my dhcp script to see eth1 (after I enabled the nic of course) and then I copied my portforwarding script (on [http://www.aboutdebian.com/proxy.htm](http://www.aboutdebian.com/proxy.htm) and just added the eth1 interface), however as this ends up making it work for eth1, it managed to make eth0 not work. I mean eth0 won't even resolve an IP via DHCP. So I deleted all of what I did and now I am back at square one with it working for eth1 only. 

Could someone help me try and get eth0 and eth1 to handout IPs to connecting computers and also forward thier traffic if need be to eth2 so that eth2 can forward it to the router and so fourth?

Thanks very much for the help, please let me know if there is anymore information I can provide.

---

### Post by mips on 2005-11-12
Ellias,

May I ask why you have such a complicated setup (So many different network segments?) as it can be simplified ?

Do you require a firewall facility between all these segments and the internet or just a simple router ?

Have a look here:  [http://ubuntuforums.org/archive/index.php/t-13137.html](http://ubuntuforums.org/archive/index.php/t-13137.html)

---

### Post by Ellias on 2005-11-12
Hello mips,

No reason really, I just want to teach myself how cause I thought it would be cool to do. All I want is for it to have basic router functionality, it does not have to be secure (yet) since I am not using it for anything really except to mess around with.

---

### Post by mips on 2005-11-13
Teaching yourself is a very good reason in  my book, nothing like expanding the mind ;)

Can you post all relevant configs here please, everything from eth interfaces to DHCP, DNS etc.

---

### Post by Ellias on 2005-11-13
This is my dhcpd.conf...
```

# A slightly different configuration for an internal subnet.
subnet 10.0.0.0 netmask 255.255.255.0 {
range 10.0.0.10 10.0.0.100; }
option subnet-mask 255.255.255.0;
option routers 10.0.0.1;
option domain-name-servers 10.0.0.1;
option domain-name "main.router.com";
option broadcast-address 10.0.0.255;
default-lease-time                      86400;   # 24 hours
max-lease-time                          172800;  # 48 hours

```

This is my dhcp3-server file...
```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"

```

This is what I have done to set up forwarding (the important parts are in bold)...

```

#!/bin/sh

#  IPTABLES  PROXY  script for the Linux 2.4 kernel.
#  This script is a derivitive of the script presented in
#  the IP Masquerade HOWTO page at:
#  www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html
#  It was simplified to coincide with the configuration of
#  the sample system presented in the Guides section of
#  www.aboutdebian.com
#
#  This script is presented as an example for testing ONLY
#  and should not be used on a production proxy server.
#
#    PLEASE SET THE USER VARIABLES
#    IN SECTIONS A AND B OR C

echo -e "\n\nSETTING UP IPTABLES PROXY..."


# === SECTION A
# -----------   FOR EVERYONE

# SET THE INTERFACE DESIGNATION FOR THE NIC CONNECTED TO YOUR INTERNAL NETWORK
#   The default value below is for "eth0".  This value
#   could also be "eth1" if you have TWO NICs in your system.
#   You can use the ifconfig command to list the interfaces
#   on your system.  The internal interface will likely have
#   have an address that is in one of the private IP address
#   ranges.
#       Note that this is an interface DESIGNATION - not
#       the IP address of the interface.
#   Enter the internal interface's designation for the
#   INTIF variable:

**INTIF="eth0"**


# SET THE INTERFACE DESIGNATION FOR YOUR "EXTERNAL" (INTERNET) CONNECTION
#   The default value below is "ppp0" which is appropriate
#   for a MODEM connection.
#   If you have two NICs in your system change this value
#   to "eth0" or "eth1" (whichever is opposite of the value
#   set for INTIF above).  This would be the NIC connected
#   to your cable or DSL modem (WITHOUT a cable/DSL router).
#       Note that this is an interface DESIGNATION - not
#       the IP address of the interface.
#   Enter the external interface's designation for the
#   EXTIF variable:
[B]
EXTIF="eth2"[/B]


# ! ! ! ! !  Use ONLY Section B  *OR*  Section C depending on
#  ! ! ! !   the type of Internet connection you have.


# === SECTION B
# -----------   FOR THOSE WITH STATIC PUBLIC IP ADDRESSES

   # SET YOUR EXTERNAL IP ADDRESS
   #   If you specified a NIC (i.e. "eth0" or "eth1" for
   #   the external interface (EXTIF) variable above,
   #   AND if that external NIC is configured with a
   #   static, public IP address (assigned by your ISP),
   #   UNCOMMENT the following EXTIP line and enter the
   #   IP address for the EXTIP variable:

#EXTIP="your.static.IP.address"



# === SECTION C
# ----------   DIAL-UP MODEM, AND RESIDENTIAL CABLE-MODEM/DSL (Dynamic IP) USERS

# SET YOUR EXTERNAL INTERFACE FOR DYNAMIC IP ADDRESSING
#   If you get your IP address dynamically from SLIP, PPP,
#   BOOTP, or DHCP, UNCOMMENT the command below.
#   (No values have to be entered.)
#         Note that if you are uncommenting these lines then
#         the EXTIP line in Section B must be commented out.

EXTIP="`/sbin/ifconfig ppp0 | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`"


# --------  No more variable setting beyond this point  --------


echo "Loading required stateful/NAT kernel modules..."

/sbin/depmod -a
/sbin/modprobe ip_tables
/sbin/modprobe ip_conntrack
/sbin/modprobe ip_conntrack_ftp
/sbin/modprobe ip_conntrack_irc
/sbin/modprobe iptable_nat
/sbin/modprobe ip_nat_ftp
/sbin/modprobe ip_nat_irc

echo "    Enabling IP forwarding..."
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "1" > /proc/sys/net/ipv4/ip_dynaddr

echo "    External interface: $EXTIF"
echo "       External interface IP address is: $EXTIP"

echo "    Loading proxy server rules..."

# Clearing any existing rules and setting default policy
iptables -P INPUT ACCEPT
iptables -F INPUT
iptables -P OUTPUT ACCEPT
iptables -F OUTPUT
iptables -P FORWARD DROP
iptables -F FORWARD
iptables -t nat -F

# FWD: Allow all connections OUT and only existing and related ones IN
[B]iptables -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT

iptables -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT[/B]

# Enabling SNAT (MASQUERADE) functionality on $EXTIF
**iptables -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE**

echo -e "       Proxy server rule loading complete\n\n"

```

That is my configuration so far and it works. Eth0 assigns an IP to the connceting computer, usually 10.0.0.99, and then if need be forwards the packets to eth2, which then if need be forwards them on to the internet.

Hope this helps! :)

---

### Post by mips on 2005-11-13
[QUOTE=Ellias]This is my dhcpd.conf...
# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"
[/QUOTE]

I will look at this in more detail later but for now you are only specifying 'eth0' for DHCP by the looks of the above...

---

### Post by Ellias on 2005-11-13
Yes, I know, in my previous configuration I specified both but it would only work for one of them. Perhaps, it is related to the way I am assigning IPs? 

Also, to avoid confusion, in my attempt to use both NICs  I included them in the dhcpd.conf and the dhcp-server file.

---

### Post by mips on 2005-11-14
I looked at dhcp stuff and it looks like you are assigning addresses from a single subnet 10.0.0.0/24 ?

**Please provide the IP Configuration info of your 3 NICs.**

Are you trying to assign 10.0.0.0/24 addresses to both NICs ? If this is the case then it is not possible. You cannot have two NIC's in the same IP subnet. Each NIC must have it's own IP Subnet ie. 10.0.0.0/24 and 10.0.1.0/24.

/24 denotes 255.255.255.0 subnet mask.

I would suggest you leave the IP tables stuff out for now and first just get the DHCP & DNS going on all NICs and make sure everything is functioning properly before you get into IP Tables.

[http://www.bind9.net/manuals-dhcp](http://www.bind9.net/manuals-dhcp)
[http://www.isc.org/index.pl?/sw/dhcp/](http://www.isc.org/index.pl?/sw/dhcp/)
[http://www.tldp.org/HOWTO/DHCP/x369.html#AEN382](http://www.tldp.org/HOWTO/DHCP/x369.html#AEN382)
Link Above: Look at 4.2. DHCP server configuration
[http://www.linux-mag.com/2000-04/networknirvana_01.html](http://www.linux-mag.com/2000-04/networknirvana_01.html)
Above Link: Very good article on DHCP, requires registration though but free.
[http://www.webmin.com/](http://www.webmin.com/)
Provides GUI based DHCP config and by the looks of things is available in Synaptic.

---

### Post by Ellias on 2005-11-14
Sorry for the confusion:

eth2: 192.168.0.102 (to internet)
eth1: 10.0.0.1 
eth2: 10.0.0.2

After doing some research I came to the same conclusion about subnets and dhcp, but I'm not exactly clear on 'why' that is? As in why is it not possible to have two nics hand out IPs on the same subnet? Don't ports on a router have the same functionality as far as being a device to connect to, to recieve an IP? I'm just a tad confused about that, I understand it in principal, just not in detail.

I will try a different config setting different subnets with the two NICs and get back to you with the results. Hopefully I will get some time tomarrow afternoon or the following days. 

Thanks for the help thus far!  

Elli

---

### Post by mips on 2005-11-14
[QUOTE=Ellias]Sorry for the confusion:

eth2: 192.168.0.102 (to internet)
eth1: 10.0.0.1 
eth2: 10.0.0.2

After doing some research I came to the same conclusion about subnets and dhcp, but I'm not exactly clear on 'why' that is? As in why is it not possible to have two nics hand out IPs on the same subnet? Don't ports on a router have the same functionality as far as being a device to connect to, to recieve an IP? I'm just a tad confused about that, I understand it in principal, just not in detail.
[/QUOTE]

Every interface can only 'belong' to one unique network, in theory you can create subinterfaces that belong to a different network but that is a different story alltogether. This is the case on any device, from the cheapest home routers to the mega$$$ Cisco Carrier Class routers as well.

These NICs on your PC are acting as gateways.

Lets just assume you 'can' have both NICs in the same network and lets just assume DHCP does work. Now lets say you have aa incoming packet from the internet and it is destined for one of the PC's on the local LAN 10.0.0.0 that could be any of the NICs. How does the router(pc) know which NIC to forward the packet out of ? It has no idea. Imagine the chaos on the internet if two big Tier1 ISPs configured their routers with the same network addresses. Both gateways would seem valid and your packets might end up in the right place or they might just get dropped. The same basically applies to two interfaces on the same device. You simply cannot perform routing if this was the case.

Does this explanation make sense ? If it doesnt let me know and I'l try and find something that explains it a little better than I do.

---

### Post by mips on 2005-11-14
Found this:

[http://www.unet.univie.ac.at/aix/aixbman/commadmn/tcp_interfaces.htm](http://www.unet.univie.ac.at/aix/aixbman/commadmn/tcp_interfaces.htm)
> **Implications of Multiple Network Interfaces on the Same Network**

Sometimes network managers feel the need to provide greater availability and performance by adding a second network adapter to a particular machine. For example, they may want to have two token-ring adapters attached to the same physical network. While it is possible to have more than one interface on the same network, in general this is not recommended for two reasons:

   1. Having two interfaces on the same network is a violation of TCP/IP architecture.

      In TCP/IP architecture, a host machine with two network adapters is defined as an IP router. Different network adapters must be attached to different physical networks. In the case of token-ring, TCP/IP addresses multiple rings bridged together as a single logical ring (as if it were a single physical ring).
   2. Having two interfaces on the same network can cause broadcast storms.

      Whenever an IP host sees traffic for a network whose IP address is different from its own network, it generates an Internet Control Message Protocol (ICMP) packet announcing this conflict. Since every host on the network sees the traffic that is misaddressed, every host generates ICMP packets. If the amount of misaddressed traffic is significant, the ICMP traffic can grow to the point that network performance degrades.

It is possible to avoid the broadcast storms created when multiple interfaces are connected to the same network. However, doing so is still a violation of TCP/IP architecture. The solution is to give the different interfaces different IP addresses on the same network. For example, you might have two token-ring adapters on the same network named tr0 and tr1. You must assign distinct IP addresses and names to tr0 and tr1. (TCP/IP architecture requires that each interface have a unique IP address and name; otherwise, unpredictable behavior will result.) For instance, you might give interface tr0 the IP address 10.10.10.1 and the name laurel.foo.bar.com, and interface tr1 the IP address 10.10.10.2 and the name hardy.foo.bar.com.

---

### Post by Ellias on 2005-11-14
Makes perfect sense, thank you. I will try and get around to the set-up as soon as my finals are over with (trimester college) and get back to you on the progress.

Thanks,

Elli

---

### Post by mips on 2005-11-15
Elias,

Have a look at the Webmin link above. Would allow you to setup DHCP and lots of other network parameters on the fly via a GUI.

---

### Post by Ellias on 2005-11-18
Alright, that Webmin application as helpful,  made some progress here...

Currently assigned IP addresses/setup...

Internet
|
D-Link Router= 192.168.0.1
|
Switch
|
Linux PC
eth2= 192.168.0.102
eth1= 192.168.2.1 --- PC 192.168.2.99
eth0= 192.168.1.1 --- PC 192.168.1.99

Here is my new dhcp.conf...

```

##########################################################
#
# DHCP CLIENT CONFIGURATION SETTINGS
#

# use ad-hoc style name server updating procedures
ddns-update-style ad-hoc;
option domain-name "jasons-dhcp-server.com";

#assign the remote dhcp server hostname/ip addresses
option domain-name-servers 192.168.1.1, 192.168.2.1;

##########################################################
#
# DHCP SERVER CONFIGURATION SETTINGS
#

# assign the defaul lease time (seconds)
default-lease-time 600000000;

# assign the max lease time (seconds)
max-lease-time 720000000;

# eth0 subnet configuration
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.2 192.168.1.99;
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.1;
}

# eth1 subnet configuration
subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.2 192.168.2.99;
  option routers 192.168.2.1;
  option broadcast-address 192.168.2.1;
}


```

Of the dhcp3-server file...

```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0 eth1"

```

Now, dhcp works! However, that's only half the battle. I want the connecting PCs to be able to access the internet. After troubleshooting a bit I have found that when pinging 192.168.0.1 I can only get as far as eth2 (192.168.0.102). 

I have tried enableing ip forwarding and proxy arp on all the interfaces and adding routes but to no avail.

Here are what my routes are currently...

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth2
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth2

```

I am very grateful for your help. :D

---

### Post by Ellias on 2005-11-19
Update: After some more troubleshooting, I have determined that when I ping the main router (192.168.0.1) the packet is forwarded by eth2 onto 192.168.0.1, it's just that when 192.168.0.1 responds to the request the packet goes to 192.168.0.102 (eth2), and then gets dropped.

So my question is, how do I get incoming requests to direct themselves to the actual sender, instead of the exiting interface (eth2)? 

That seems to be my hitch for now, please help!

---

### Post by mips on 2005-11-20
The current behaviour seems correct. The packet should be routed to Eth2. When Eth2 receives the packet it should do an ARP cache lookup to find the MAC address for the PC's IP address as you need a physical hardware address to forward the ethernet frames to.

Show us your IP tables and other relevant config changes you have done.

---

### Post by Ellias on 2005-11-20
My apologies, I seem to have misunderstood my troubleshooting techniques. Above I mentioned that the packet was routed from 192.168.0.1 (router) to 192.168.0.102 (eth2). This is not correct, what happens when I send a ping request from any computer behind my linux box is that it gets to the computer but then when it goes back to the router 192.168.0.1, it has no idea what to do with the IP (for example) 192.168.1.98, so the packet is dropped. 

I am pretty sure what I need is a script or something that will mask out-going requests from the internal network of 192.168.1-2.*'s to have the 192.168.0.102 IP. Then the router will get this back to eth2 and then eth2 will take off the mask and send it to the correct recipent?

Here is a look at my IP tables now... pretty much nadda

```

Chain INPUT (policy ACCEPT) 
target     prot opt source             destination

Chain FORWARD (policy ACCEPT) 
target     prot opt source             destination

Chain OUTPUT (policy ACCEPT) 
target     prot opt source             destination

```

Here are some other files that may be of importance...

host.conf
```

order hosts,bind
multi on

```

resolv.conf
```

search rochester.rr.com
nameserver 192.168.0.1

```

hosts.allow, not anything really...
```

# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5), hosts_options(5)
#                   and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8), rpc.mountd(8) and
# /usr/share/doc/portmap/portmapper.txt.gz for further information.
#

```

hosts.deny, not much again
```

# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5), hosts_options(5)
#                  and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper. See portmap(8)
# and /usr/doc/portmap/portmapper.txt.gz for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID

```

---

### Post by mips on 2005-11-20
No need to apologies. I will have a look at this in the morning. In the meantime connect to your router via the web interface and lets have a look at its routing table as well.

I'm not sure I understand you 100% but I'm gonna assume that when the packet gets to 192.168.0.1 it has no idea of how to forward it to 192.168.1.98 ??? Is that what you are saying ?

If that is the case then you simply need to configure 2 static routes on the router for networks 192.168.1.0 & 192.168.2.0.

The router will only have routes for directly connected networks on its LAN & WAN ports as well as a default route. It does not know how to get to your two LAN's behind the Linux box I assume.

Another option would be to run NAT in order to convert all your addresses behind the Linux box to 192.168.0.xxx addresses.

Bit late here, hope I got that right....

---

### Post by Ellias on 2005-11-21
```

Dynamic DHCP Client List  
Host Name IP Address MAC Address Expired Time  
JASONS-COMPUTER 192.168.0.101 00-11-D8-**-**-** Nov/28/2005 
192.168.0.102 00-04-76-**-**-** Nov/28/2005 
jason-laptop 192.168.0.103 00-0F-1F-**-**-** Nov/28/2005 
MRCOMPUTER 192.168.0.100 00-E0-18-**-**-** Nov/28/2005 

```

192.168.0.102 is the linux box of course.

> 
I'm not sure I understand you 100% but I'm gonna assume that when the packet gets to 192.168.0.1 it has no idea of how to forward it to 192.168.1.98 ??? Is that what you are saying ?


Yup, exactly. It doesn't know about that address, so the packet is dropped.

> 
If that is the case then you simply need to configure 2 static routes on the router for networks 192.168.1.0 & 192.168.2.0.


I thought of the exact same solution, unfortunately a quick call to D-Link tech suport and I confirmed that my router did not support static routes :(

> 
The router will only have routes for directly connected networks on its LAN & WAN ports as well as a default route. It does not know how to get to your two LAN's behind the Linux box I assume.


Absolutely.

I think my only option is to run a NAT. Unfortunately I have no clue how to do this, much less with my configuration. Any ideas?

---

### Post by mips on 2005-11-21
What model D-Link router do you use ???

It would probably be easiest to translate all addresses to 192.168.0.102 using different ports.

I have only configured NAT on Cisco routers, never Linux so I'm at a loss.

I have however found some reading material for you ;)

[http://www.aboutdebian.com/proxy.htm](http://www.aboutdebian.com/proxy.htm)
[http://www.bolthole.com/solaris/firewall.html](http://www.bolthole.com/solaris/firewall.html)
[http://lists.debian.org/debian-firewall/2002/01/msg00061.html](http://lists.debian.org/debian-firewall/2002/01/msg00061.html)
[http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/)
[https://wiki.ubuntu.com/ThinClientHowtoNAT](https://wiki.ubuntu.com/ThinClientHowtoNAT)
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

Maybe have a look at Webmin to simplify NAT.

---

### Post by Ellias on 2005-11-21
It's a DI-604

[http://www.dlink.com/products/?pid=62](http://www.dlink.com/products/?pid=62)

I'll look into the reading when I get the chance thanks so much. :)

---

### Post by Ellias on 2005-11-21
[http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/]("http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/")

That is exactly what I needed! I was able to combine and modify two of the example scripts and it works! Here is the final script I got...

```

#!/bin/sh
#
#firewall-iptables
FWVER=0.76
#
#               Initial SIMPLE IP Masquerade test for 2.6 / 2.4 kernels
#               using IPTABLES.
#
#               Once IP Masquerading has been tested, with this simple
#               ruleset, it is highly recommended to use a stronger
#               IPTABLES ruleset either given later in this HOWTO or
#               from another reputable resource.
#
#
#
# Log:
#       0.76 - Added comments on why the default policy is ACCEPT
#       0.75 - Added more kernel modules to the comments section
#       0.74 - the ruleset now uses modprobe vs. insmod
#       0.73 - REJECT is not a legal policy yet; back to DROP
#       0.72 - Changed the default block behavior to REJECT not DROP
#       0.71 - Added clarification that PPPoE users need to use
#              "ppp0" instead of "eth0" for their external interface
#       0.70 - Added commented option for IRC nat module
#            - Added additional use of environment variables
#            - Added additional formatting
#       0.63 - Added support for the IRC IPTABLES module
#       0.62 - Fixed a typo on the MASQ enable line that used eth0
#              instead of $EXTIF
#       0.61 - Changed the firewall to use variables for the internal
#              and external interfaces.
#       0.60 - 0.50 had a mistake where the ruleset had a rule to DROP
#              all forwarded packets but it didn't have a rule to ACCEPT
#              any packets to be forwarded either
#            - Load the ip_nat_ftp and ip_conntrack_ftp modules by default
#       0.50 - Initial draft
#

echo -e "\n\nLoading simple rc.firewall-iptables version $FWVER..\n"


# The location of the iptables and kernel module programs
#
#   If your Linux distribution came with a copy of iptables,
#   most likely all the programs will be located in /sbin.  If
#   you manually compiled iptables, the default location will
#   be in /usr/local/sbin
#
# ** Please use the "whereis iptables" command to figure out
# ** where your copy is and change the path below to reflect
# ** your setup
#
IPTABLES=/sbin/iptables
#IPTABLES=/usr/local/sbin/iptables
DEPMOD=/sbin/depmod
MODPROBE=/sbin/modprobe


#Setting the EXTERNAL and INTERNAL interfaces for the network
#
#  Each IP Masquerade network needs to have at least one
#  external and one internal network.  The external network
#  is where the natting will occur and the internal network
#  should preferably be addressed with a RFC1918 private address
#  scheme.
#
#  For this example, "eth0" is external and "eth1" is internal"
#
#
#  NOTE:  If this doesnt EXACTLY fit your configuration, you must
#         change the EXTIF or INTIF variables above. For example:
#
#            If you are a PPPoE or analog modem user:
#
#               EXTIF="ppp0"
#
#
EXTIF="eth2"
INTIF="eth1"
INTIF2="eth0"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"
echo "   Internal Interface:  $INTIF2"

EXTIP="192.168.0.103"
echo "   External IP:  $EXTIP"

#======================================================================
#== No editing beyond this line is required for initial MASQ testing ==


echo -en "   loading modules: "

# Need to verify that all modules have all required dependencies
#
echo "  - Verifying that all kernel modules are ok"
$DEPMOD -a

# With the new IPTABLES code, the core MASQ functionality is now either
# modular or compiled into the kernel.  This HOWTO shows ALL IPTABLES
# options as MODULES.  If your kernel is compiled correctly, there is
# NO need to load the kernel modules manually.
#
#  NOTE: The following items are listed ONLY for informational reasons.
#        There is no reason to manual load these modules unless your
#        kernel is either mis-configured or you intentionally disabled
#        the kernel module autoloader.
#

# Upon the commands of starting up IP Masq on the server, the
# following kernel modules will be automatically loaded:
#
# NOTE:  Only load the IP MASQ modules you need.  All current IP MASQ
#        modules are shown below but are commented out from loading.
# ===============================================================

echo "----------------------------------------------------------------------"

#Load the main body of the IPTABLES module - "iptable"
#  - Loaded automatically when the "iptables" command is invoked
#
#  - Loaded manually to clean up kernel auto-loading timing issues
#
echo -en "ip_tables, "
$MODPROBE ip_tables


#Load the IPTABLES filtering module - "iptable_filter"
#  - Loaded automatically when filter policies are activated


#Load the stateful connection tracking framework - "ip_conntrack"
#
# The conntrack  module in itself does nothing without other specific
# conntrack modules being loaded afterwards such as the "ip_conntrack_ftp"
# module
#
#  - This module is loaded automatically when MASQ functionality is
#    enabled
#
#  - Loaded manually to clean up kernel auto-loading timing issues
#
echo -en "ip_conntrack, "
$MODPROBE ip_conntrack


#Load the FTP tracking mechanism for full FTP tracking
#
# Enabled by default -- insert a "#" on the next line to deactivate
#
echo -en "ip_conntrack_ftp, "
$MODPROBE ip_conntrack_ftp


#Load the IRC tracking mechanism for full IRC tracking
#
# Enabled by default -- insert a "#" on the next line to deactivate
#
echo -en "ip_conntrack_irc, "
$MODPROBE ip_conntrack_irc


#Load the general IPTABLES NAT code - "iptable_nat"
#  - Loaded automatically when MASQ functionality is turned on
#
#  - Loaded manually to clean up kernel auto-loading timing issues
#
echo -en "iptable_nat, "
$MODPROBE iptable_nat


#Loads the FTP NAT functionality into the core IPTABLES code
# Required to support non-PASV FTP.
#
# Enabled by default -- insert a "#" on the next line to deactivate
#
echo -en "ip_nat_ftp, "
$MODPROBE ip_nat_ftp


#Loads the IRC NAT functionality into the core IPTABLES code
# Required to support NAT of IRC DCC requests
#
# Disabled by default -- remove the "#" on the next line to activate
#
#echo -e "ip_nat_irc"
#$MODPROBE ip_nat_irc

echo "----------------------------------------------------------------------"

# Just to be complete, here is a partial list of some of the other
# IPTABLES kernel modules and their function.  Please note that most
# of these modules (the ipt ones) are automatically loaded by the
# master kernel module for proper operation and don't need to be
# manually loaded.
# --------------------------------------------------------------------
#
#    ip_nat_snmp_basic - this module allows for proper NATing of some
#                        SNMP traffic
#
#    iptable_mangle    - this target allows for packets to be
#                        manipulated for things like the TCPMSS
#                        option, etc.
#
# --
#
#    ipt_mark       - this target marks a given packet for future action.
#                     This automatically loads the ipt_MARK module
#
#    ipt_tcpmss     - this target allows to manipulate the TCP MSS
#                     option for braindead remote firewalls.
#                     This automatically loads the ipt_TCPMSS module
#
#    ipt_limit      - this target allows for packets to be limited to
#                     to many hits per sec/min/hr
#
#    ipt_multiport  - this match allows for targets within a range
#                     of port numbers vs. listing each port individually
#
#    ipt_state      - this match allows to catch packets with various
#                     IP and TCP flags set/unset
#
#    ipt_unclean    - this match allows to catch packets that have invalid
#                     IP/TCP flags set
#
#    iptable_filter - this module allows for packets to be DROPped,
#                     REJECTed, or LOGged.  This module automatically
#                     loads the following modules:
#
#                     ipt_LOG - this target allows for packets to be
#                               logged
#
#                     ipt_REJECT - this target DROPs the packet and returns
#                                  a configurable ICMP packet back to the
#                                  sender.
#

echo -e "   Done loading modules.\n"



#CRITICAL:  Enable IP forwarding since it is disabled by default since
#
#           Redhat Users:  you may try changing the options in
#                          /etc/sysconfig/network from:
#
#                       FORWARD_IPV4=false
#                             to
#                       FORWARD_IPV4=true
#
echo "   Enabling forwarding.."
echo "1" > /proc/sys/net/ipv4/ip_forward


# Dynamic IP users:
#
#   If you get your IP address dynamically from SLIP, PPP, or DHCP,
#   enable this following option.  This enables dynamic-address hacking
#   which makes the life with Diald and similar programs much easier.
#
echo "   Enabling DynamicAddr.."
echo "1" > /proc/sys/net/ipv4/ip_dynaddr


# Enable simple IP forwarding and Masquerading
#
#  NOTE:  In IPTABLES speak, IP Masquerading is a form of SourceNAT or SNAT.
#
#  NOTE #2:  The following is an example for an internal LAN address in the
#            192.168.0.x network with a 255.255.255.0 or a "24" bit subnet mask
#            connecting to the Internet on external interface "eth0".  This
#            example will MASQ internal traffic out to the Internet but not
#            allow non-initiated traffic into your internal network.
#
#
#         ** Please change the above network numbers, subnet mask, and your
#         *** Internet connection interface name to match your setup
#


#Clearing any previous configuration
#
#  Unless specified, the defaults for INPUT and OUTPUT is ACCEPT
#    The default for FORWARD is DROP (REJECT is not a valid policy)
#
#   Isn't ACCEPT insecure?  To some degree, YES, but this is our testing
#   phase.  Once we know that IPMASQ is working well, I recommend you run
#   the rc.firewall-*-stronger rulesets which set the defaults to DROP but
#   also include the critical additional rulesets to still let you connect to
#   the IPMASQ server, etc.
#
echo "   Clearing any existing rules and setting default policy.."
$IPTABLES -P INPUT ACCEPT
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD
$IPTABLES -t nat -F

echo "   FWD: Allow all connections OUT and only existing and related ones IN"
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
$IPTABLES -A FORWARD -j LOG
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF2 -m state --state ESTABLISHED,RELATED \-j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $INTIF2 -m state --state ESTABLISHED,RELATED \-j ACCEPT
$IPTABLES -A FORWARD -i $INTIF2 -o $INTIF -m state --state ESTABLISHED,RELATED \-j ACCEPT
$IPTABLES -A FORWARD -i $INTIF2 -o $EXTIF -j ACCEPT
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP


echo "   Enabling SNAT (MASQUERADE) functionality on $EXTIF"
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

echo -e "\nrc.firewall-iptables v$FWVER done.\n"

```

Mips, I owe ya for hanging in there with me. Thanks for your consistent help and answering my questions. I've learned so much by doing this!

---

### Post by mips on 2005-11-22
Ellias, only a pleasure, I learned some along the way as well.

I have an idea, why dont you make a "HOWTO-Ubuntu internet router, Firewall,DHCP,DNS,NAT".

I think others will benefit. You know all the steps from the beginning, you have all the output files as examples. Just dont forget the small and obvious things we take for granted, the details are important.

---

### Post by unlotto on 2007-03-24
[COLOR="Silver"]Am I the only one who is having problems with port 443 and ssl connections?
Theres also a number of webpages that seem inaccessible or extremely slow (most likely related). Among these would be hotmail, ati.com, quicktime.com.

I run a webserver on port 80. I have a 2-nics setup (and have therefore disabled the $INTIF2 forwarding rules.

the added forward+prerouting rule is as follows:
```

$IPTABLES -t nat -A PREROUTING -p tcp -i eth0 -d $EXTIF --dport 80 -j DNAT --to 192.168.1.1:80
$IPTABLES -A FORWARD -p tcp -i eth0 -d 192.168.1.1 --dport 80 -j ACCEPT

```[/COLOR]

update: It turns out one of the gateways of my ISP is at fault.

---

