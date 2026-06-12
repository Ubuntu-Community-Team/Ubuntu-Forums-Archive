---
title: "dhcp only starts when router plugged in"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by phil79 on 2006-10-23
Can someone please explain this.....

My DHCP server will not start unless I have my router plugged in...but it ONLY starts if the router is also running DHCP...

If I try and start DHCP manually (router NOT running DHCP) in Ubuntu I get:

ubuntu:~>  sudo /usr/sbin/dhcpd3  eth0 -pf /var/run/dhcp3-server/dhcpd.pid -cf /etc/dhcp3/dhcpd.conf
Internet Systems Consortium DHCP Server V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Wrote 0 deleted host decls to leases file.
Wrote 0 new dynamic host decls to leases file.
Wrote 7 leases to leases file.

No subnet declaration for eth0 (0.0.0.0).
** Ignoring requests on eth0.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface eth0 is attached. **


Not configured to listen on any interfaces!


The eth0 works fine but just can't get DHCP to work unless the router is plugged in running DHCP...

](*,) 

Thanks

---

### Post by twistedtwig on 2006-10-23
to start / restart etc my dhcp server i use

/etc/init.d/dhcp3-server restart

not sure if either way is better or not though. are you sure your dhcp server is configured correctly?

---

### Post by phil79 on 2006-10-23
Not sure if it's configured properly...that's the problem :(

---

### Post by lloyd_b on 2006-10-23
Could you post the "dhcpd.conf" file?  It should be located in either "/etc" or "/etc/dhcp3" (not sure which).

Also, could you post the "/etc/network/interfaces" file?

Lloyd B.

---

### Post by netztier on 2006-10-23
> **phil79 said:**
> Can someone please explain this.....

No subnet declaration for eth0 (0.0.0.0).
** Ignoring requests on eth0.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface eth0 is attached. **


"0.0.0.0" looks like an unconfigured address on an interface. You're not actually trying to run a DHCP server on a box (or interface thereof) that is a DHCP client itself, are you?

I presume that the DHCP server refuses to start if it doesn't find an interface properly configured and in "up" state. 

If the possibly only (?) interface in that box is configured as DHCP-client, it won't reach "up" that state unless the router is plugged in and it's gotten a DHCP lease from the router's internal DHCP server, very much as you describe.

Possible solution: you'll have to configure the interface with a static IP - and don't forget to disable the router's DHCP server afterwards.

regards

Marc

---

### Post by phil79 on 2006-10-23
""0.0.0.0" looks like an unconfigured address on an interface. You're not actually trying to run a DHCP server on a box (or interface thereof) that is a DHCP client itself, are you?"

Aaaahh.......I think I see what you mean...errrrr.

I notice i do have dhcp client running:

dhcp      4677  0.0  0.0   2340   540 ?        S<s  19:35   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0


I want the dhcp server to run on this box - but as you say it is also a dhcp client itself.....so do I have to disable the dhcpclient and just assign a static address to my machine in dhcp.conf ???

It's a steep learning curve this. Thanks...

---

### Post by netztier on 2006-10-23
> **phil79 said:**
> 
I want the dhcp server to run on this box - but as you say it is also a dhcp client itself.....so do I have to disable the dhcpclient and just assign a static address to my machine in dhcp.conf ???


Basically, yes. You can leave dhcpclient installed, it should be enough to assign a static IP address to the interface to deactivate it.

Check what IP subnet your router's LAN interface has, and configure your machine with an address from that subnet. Let's assume your router has 192.168.1.1, with a subnet mask of 255.255.255.0 and has a DHCP pool setting for 192.168.1.33 - 192.168.1.62. 

Then your interface configuration should be outside this range, but within the same subnet. If the interface in question is **eth0**, your [FONT="Courier New"]/etc/network/interfaces[/FONT] should contain lines somewhat like this:

```
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

```

To keep the learning curve nice an flat, configure the address range (called "scope") of your new DHCP server to dole out addresses from a block that is not covered by the other DHCP server in the router. You can then switch either DHCP server on or off while playing around and still have DHCP service available for the users in your LAN, while avoiding the risk of having double IP addresses. 

regards

Marc

---

### Post by phil79 on 2006-10-24
Thanks for help Marc - I am nearly there - but when my laptop connects - it gets an ip address - but I can't see the internet.

So my question is:

Does it matter where I put individual machine static IP addresses ?

Do I put it *IN* the subnet definition or AFTER ??

subnet 192.168.1.0 netmask 255.255.255.0 {

range                      192.168.1.2 192.168.1.254;            
option broadcast-address   192.168.1.255;    
option routers             192.168.1.1;

host laptop {
                hardware ethernet xxxxx;
                fixed-address xxxx;
        }

)

# OR  CAN I PUT IT HERE ????
host laptop {
                hardware ethernet xxxxx;
                fixed-address xxxx;
        }

)


The laptop seems to get an IP address but can't see the internet (the PC running the DHCP server - my main PC - can see the internet)

Thanks.

---

### Post by netztier on 2006-10-24
> **phil79 said:**
> Thanks for help Marc - I am nearly there - but when my laptop connects - it gets an ip address - but I can't see the internet.


I for myself have never configured a dhcpd on linux, but the excerpt from the config file you showed looks almost reasonable to me. [COLOR="DimGray"][SIZE="1"](Tip: put "code" tags around config-file text, with the **#**-Button) from the "toolbar")[/SIZE][/COLOR] 

I discourage to dole out the entire block of 192.168.1.2 - 192.168.1.254 to the DHCP clients. Rather use a smaller block, (for example 192.168.1.100-149),  and leave some addresses for fixed-IP configurations, such as your DHCP Server, maybe a WLAN access point or a print server you might want to add to your LAN later. 

Again: the range for "dynamic addresses" in your subnet MUST NOT overlap with any static addresses. The fixed IP address of your DHCP server should be *outside* this range of dynamically assigned addresses.

> **phil79 said:**
> 
The laptop seems to get an IP address but can't see the internet (the PC running the DHCP server - my main PC - can see the internet)

Well, I'd even risk a bet here that the laptop *can* reach the internet. It just doesn't know about any DNS server(s).
 
Before changing anything, try sending a ping to *198.133.219.25*, then try sending a ping to *[www.cisco.com](www.cisco.com) *(which is the same) and I bet you get some error message saying that that was an unknown hostname. And voilà: the laptop has no DNS server configured.

Probably, your router runs a DNS proxy function on its LAN interface (192.168.1.1), so you'll need to add the DHCP option for DNS-Servers (see documentation for your DHCP server on how to do that) with that same address. 

The best way to get it done right: 
[LIST]
[*]deactivate (temporarily) your own DHCP server, 
[*]activate the router's DHCP service, 
[*]obtain an IP address and check which DNS server(s) it has told your laptop to use. Read the contents of [FONT="Courier New"]/etc/resolv.conf [/FONT]on Linux, or do an [FONT="Fixedsys"]ipconfig /all [/FONT] on a Windows command prompt to see the configured DNS servers. 
[*]write down this/these address(es) ...
[*]... add it/them to the DHCP options of your own DHCP server
[*]deactivate the router's DHCP
[*]reactivate your own DHCP server 
[*]reboot your laptop or have it renew it's DHCP lease
[/LIST]


If the router doesn't do DNS-proxy, you have a problem, but also some possibilites and lot of opportunities to learn:

[LIST]
[*]find out the IP addresses of your provider's DNSs and configure them in the DHCP options. [COLOR="DimGray"]([SIZE="1"]If your internet link is not permanently "up", this will cause a connection every time a host tries to resolve a name, can become very costly on ISDN or dialup access).[/SIZE][/COLOR]
[*] use someone else's DNS servers and configure them in the DHCP Options. [COLOR="dimgray"][SIZE="1"](possible, but not recommended, and same as above applies)[/SIZE][/COLOR]
[*] setup an internal caching-only/forwarding DNS server on the DHCP server machine and configure it's IP-address in the DHCP options. Configure the DNS service to foward your queries to your provider's DNSs.
[/LIST]


If you really want to learn about networking and DNS and stuff, the third option from above is the way to go - but that's advanced stuff and a lot of things have to be considered. 


regards

Marc

---

### Post by O.H.Dog on 2006-10-30
I just had this problem with a new Debian install. The automatic configuration had put the interface names in all upper case in the file:

/etc/default/dhcp3-server

Specifically:

INTERFACES="ETH0 ETH1"

For my machine the correct line is:

INTERFACES="eth0 eth1"

---

