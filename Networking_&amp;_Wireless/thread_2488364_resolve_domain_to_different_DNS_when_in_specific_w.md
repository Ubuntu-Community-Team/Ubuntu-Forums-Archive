---
title: "resolve domain to different DNS when in specific wifi network"
date: 2023-07-03
forum: Networking &amp; Wireless
---

### Post by dstaubsauger on 2023-07-03
Hi,

when connected to my home wifi, I want my laptop to resolve home-server.example.com to an IP in the local network. When connected to any other network, I want to use that network's DNS. The server is publicly reachable on the same domain through some levels of reverse-proxying through a VPN. My home router has a slow uplink and no public IPv4 address.

I'm using the standard Ubuntu NetworkManager setup. I realize I can set DNS overrides in NetworkManager's settings, but those are for DNS servers, not single domains. If running a DNS server on my laptop is the best way forward, what software would you recommend setting a single override like this?

Best regards

---

### Post by TheFu on 2023-07-04
DHCP reservations allow setting the DNS servers to be used with the DHCP information. That's handled in the router.  On the laptop, you'd just set the networking to use DHCP.  

All VPNs that I know have a way to set the DNS.  I know wireguard and openvpn both do.  Nebula Mesh networks can behave as their own DNS too.  Of course, if you are hosting your own VPN, then it would make sense to also host your own DNS.

---

### Post by ixeous on 2023-07-04
You could also put the IP address of your server in your local /etc/hosts file.  Then it will be the same IP everywhere you go.  The potential downside is if you are on a network with the same IP space as your server is on and not connected to your VPN, things can get confusing.

---

### Post by TheFu on 2023-07-04
> **ixeous said:**
> You could also put the IP address of your server in your local /etc/hosts file.  Then it will be the same IP everywhere you go.  The potential downside is if you are on a network with the same IP space as your server is on and not connected to your VPN, things can get confusing.

We can't just pick a random IP address on different networks. They don't work that way.  Perhaps you meant to say the VPN remote address for the remote server?  Not sure if that is clearer either.

---

### Post by ixeous on 2023-07-04
Right.  I understood that OP wanted to connect to a server in his private network when at that location, and then use some form of VPN to be able to connect to it when at other locations.  The host file would be the server's actual IP in the private network where it resides.  When connected via a VPN, the OP should be able to use the private IP space where the server resides. The gotcha being when connected to another WiFi network with the same IP space as the one where the server resides.

---

### Post by TheFu on 2023-07-04
Much clearer.

This is why we all need to pick strange private IP subnets for our different LANs at home.  So when/if we ever want to use a VPN, the routing can figure out where to send traffic, assuming that VPN split tunnels are allowed. I've never seen any businesses allow split tunnels, but home users do all sorts of crazy things.

---

### Post by ixeous on 2023-07-04
There are only so many to pick from.  Avoiding 192.168.0.x and 192.168.1.x will probably get you different from half of the other networks out there.  Beyond that it's a crapshoot.

---

### Post by TheFu on 2023-07-04
> **ixeous said:**
> There are only so many to pick from.  Avoiding 192.168.0.x and 192.168.1.x will probably get you different from half of the other networks out there.  Beyond that it's a crapshoot.

There are thousands of private IPs to pick from in each range. These are the ranges
[LIST]
[*]10.x.x.x/8  (10.0.0.0 - 10.255.255.254)
[*]172.16.x.x/12
[*]192.168.x.x/16
[/LIST]
Thousands of subnets, especially if using /24 subnets.
Just avoid the first 1 subnets in each of those ranges.  I'm using 
[LIST]
[*]172.21.21.x/24
[*]172.22.22.x/24
[*]10.66.66.0/24
[*]10.77.77.0/24
[*]10.88.88.0/24
[*]10.0.3.0/24
[*]192.168.123.0/24
[*]192.168.122.0/24
[/LIST]


I've seen 192.168.122.0/24 used elsewhere, but not any of the others. There are thousands.

---

### Post by ixeous on 2023-07-04
I use a 10.x.x.x/24. network and have run into conflicts.  It happens

---

### Post by TheFu on 2023-07-05
> **ixeous said:**
> I use a 10.x.x.x/24. network and have run into conflicts.  It happens

There are some well-used 10/8 addresses to be avoided.  10.1.10.1/24 is one.  I'd avoid 10.1.1.1/24 too, but 10.1.238.1/24 will almost certainly be fine.
```
$ ipcalc 10.255.255.0/8
Address:   10.255.255.0         00001010. 11111111.11111111.00000000
Netmask:   255.0.0.0 = 8        11111111. 00000000.00000000.00000000
Wildcard:  0.255.255.255        00000000. 11111111.11111111.11111111
=>
Network:   10.0.0.0/8           00001010. 00000000.00000000.00000000
HostMin:   10.0.0.1             00001010. 00000000.00000000.00000001
HostMax:   10.255.255.254       00001010. 11111111.11111111.11111110
Broadcast: 10.255.255.255       00001010. 11111111.11111111.11111111
Hosts/Net: 16777214              Class A, Private Internet

```
There are 16 million IPs in that range.  Thousands of /24 subnets.  Pick something odd and chances are there won't be any conflicts, but the chance isn't zero, just really, really, small.

---

### Post by dstaubsauger on 2023-07-06
> **ixeous said:**
> Right.  I understood that OP wanted to connect to a server in his private network when at that location, and then use some form of VPN to be able to connect to it when at other locations. 

Almost. It seems I'm bad at explaining this. I already have the following working:

- A cloud server with a public IPv4 address, to which my domain points in public DNS.
- My home server, which runs Nextcloud with https on 443.
- A VPN connection between the two.
- The cloud server tunnels its public port 443 to the home server's port 443 via the VPN connection.

Using this setup, the nextcloud is accessible everywhere, from any client, without any specific setup required. The only downside: When I'm at home, on my own laptop, accessing the nextcloud hosted in the next room, the following happens:
- My laptop looks up my-nextcloud-server.example.com, which points to the public IPv4 of my cloud server.
- My laptop connects to the cloud server.
- My cloud forwards the tcp stream via vpn to the home server.
- This works, but everything goes through my slow uplink both ways.

What I want to happen:
- My laptop realizes it's in my home wifi
- Instead of looking up my-nextcloud-server.example.com in the public DNS, it resolves the address to the LAN IP of the home server next room.
- Whohoo, performance!

---

### Post by TheFu on 2023-07-06
So, I see 2 choices.
[LIST=1]
[*]Use nebula mesh vpn, which will route things locally when that route is cheaper.  Also, you can use the mesh from your client system and it will have a secure route regardless of where it is in the world, provided the client has UDP access to the lighthouse port. Nebula uses the most efficient route between systems.
[*]Setup split DNS, so there's an internal DNS that answers with the local IP and let normal public DNS systems answer for everything else.
[/LIST]

I assume your VPN has the server running on the VPS and the client is your nextcloud server?

You realize that there's not really any need for the entire world to have access to your VPS running the VPN, right?  Nextcloud really shouldn't be on the internet AND inside your home LAN, unless you segment that home connection off separate from all other systems at home and firewall between the LANs.

There is a flaw with nebula, if you use container-based services, then those containers will need to be privileged (running as root) so the nebula daemon can manage the tunnel connections.

I use a mix of all three of these things.  I have a DNS that works when I'm on the LAN.  When I'm away and not connected to the internet, my public webapps resolve to the static IPs for my domains, and if I'm connected to either VPN or Nebula Mesh, then I have direct access to the systems on the LAN.

My nextcloud instance is NOT available to the internet, except for about 30 seconds every 3 months when I get new LE certs.  LE will only issue certs if port 80/tcp is available. For internal only systems, I use acme.sh to spoof the domain, get the cert and install it on a reverse proxy.

I'm in the process of migrating to a new ISP, so things are a little iffy now.  Because I use unprivileged containers for some of my public services, I don't have a good solution. They won't run wireguard nor nebula.  

Just a few years ago, I moved those systems off full VMs to LXC containers to have a lighter footprint. Seems I will need to move at least 1 of those systems (my email gateway) back into a full VM. Sigh.  Lots of moving parts in my setup right now.

---

### Post by dstaubsauger on 2023-07-06
> **TheFu said:**
> 
I assume your VPN has the server running on the VPS and the client is your nextcloud server?


Yes.

> **TheFu said:**
> 
You realize that there's not really any need for the entire world to have access to your VPS running the VPN, right?

I regularly use the nextcloud to share the files with people, or to provide people with upload links when I want them to send me something. Having the nextcloud publicly accessible is needed for this to work.

> **TheFu said:**
> 
 Nextcloud really shouldn't be on the internet AND inside your home LAN, unless you segment that home connection off separate from all other systems at home and firewall between the LANs.


Could you elaborate on that? In what way would it be harmful for the same nextcloud instance to be reachable on two network interfaces (VPN and LAN)?

> **TheFu said:**
> 
Setup split DNS, so there's an internal DNS that answers  with the local IP and let normal public DNS systems answer for  everything else.


So, if I understand correctly, this means that I need to run a DNS server somewhere (my laptop? my home router?). What DNS server software can you recommend for this?

---

### Post by ixeous on 2023-07-06
I use option number 2 that theFu describes.  I have a server with a hostname that is resolvable via public DNS - myserver.example.com.  Everywhere in the world outside of my home, myserver.example.com resolves to the public IP.  On my home DNS server, I have an entry for myserver.example.com that resolves to my internal private IP.  The ability to do that depends on what you are using for DNS internally.  I have a system that runs dnsmasq for my internal DNS and DHCP so I just needed to add an entry in the dnsmasq conf file.  I'm not aware of any consumer grade routers that allow that level of DNS configuration, but they might exist.

---

### Post by TheFu on 2023-07-06
> **dstaubsauger said:**
> I regularly use the nextcloud to share the files with people, or to provide people with upload links when I want them to send me something. Having the nextcloud publicly accessible is needed for this to work.


I don't trust php webapps to be secure on the recommendations of our corporate security team.  Because of this, I don't allow php-based webapps to be accessible over the internet, without a full VPN or at least using an ssh SOCKS proxy setup. Obviously, I trust the security team.

> **dstaubsauger said:**
> Could you elaborate on that? In what way would it be harmful for the same nextcloud instance to be reachable on two network interfaces (VPN and LAN)? When your nextcloud instance gets hacked, and you should plan for it to be hacked, then the attacker will have access to the entire subnet were it sits. If you have any other non-hardened systems on that same subnet, they get it all. That could be bad, especially if you don't have multi-layered security.

> **dstaubsauger said:**
> 
So, if I understand correctly, this means that I need to run a DNS server somewhere (my laptop? my home router?). What DNS server software can you recommend for this?

The DNS needs to be inside your LAN.  There's lots of different DNS solutions.  

Some people use a pi-hole to do both DNS blocking AND as their local DNS.  Others run DNS on the same system they run DHCP on.  Others enable DNS on their router (which I think is a terrible idea).  Routers should do 2 things.  Routing and firewalls.  Not DNS. Not DHCP. Not VPNs, Not fancy graphing. Not wifi. I run 2 pi-hole systems in side an LXC container each on 2 physically separate systems.  Primary and backup DNS.

**AND NEVER, NEVER, EVER, hook up shared storage to a router.  There are different opinions on that.  ** That's just asking to be hacked and have all those files shared world-wide.

When it comes time to trust things, do your research and look up how many times that solution has been cracked.  Most people see the check box for a feature and assume is it secure.  That just isn't true.

For me, it comes down to the more software is running on a device, then the more likely there will be critical bugs and I'm not willing to risk my entire network by using a WAN gateway/router for extra duty just because it has a feature.  

Of course, if you have an old router that isn't being used as your primary WAN interface and want to enable all the features while it is 100% inside your LAN, great. Go crazy. Heck, one of my old routers has a DNLA server on it, which I might be talked into using if I get desperate.  But in general, routers should do routing and firewalling, nothing else.  K.I.S.S. [https://en.wikipedia.org/wiki/KISS_principle](https://en.wikipedia.org/wiki/KISS_principle)

My WAN router runs OPNsense on a low-powered, x86_64 AMD system that uses 12W of power.  OPNSense can do all sorts of fancy things, but mine just does routing and firewalling.  It does split my home network into multiple, physically separate, subnets too.  I prefer physical separate networks over VLAN tagging.  VLANs are "suggestions", not mandates.

I really like the nebula mesh overly networking because it provided encrypted channels per service between systems that need access to those services.  A few banks use this so they don't have to worry about insiders without proper credentials even having access to systems they shouldn't know exist. It is a very powerful idea, the overlay, mesh, encrypted, authenticated, network.

---

### Post by SeijiSensei on 2023-07-07
How many client workstations are supporting? If it's fewer than 255, I'd stick the 192.168/24 "Class-C" subnets. 

Not sure what kinds of conflicts you're reporting. There are no public machines in 10/8. Are the conflicts within your local network? 

You might be able to resolve this problem by editing /etc/systemd/resolved.conf. You can put your local DNS in the "DNS=" line, then add public DNS servers like 8.8.8.8 or 1.1.1.1 in the "FallbackDNS" line. Then run "sudo systemctl restart systemd-resolved".

> **TheFu said:**
> I don't trust php webapps to be secure on the recommendations of our corporate security team.

Aside from prejudice, what's their problem with a language that powers millions of websites? I write in PHP. I've never had security problems. Or is their concern about the writers of those webapps?

---

