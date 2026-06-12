---
title: "IPv6 openvpn remote connection problem Help!"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by Alfie O'mega on 2010-02-05
I am trying to connect to my office over a VPN and am having trouble with it. 

The VPN appears to be using IPv6, something I know absolutely nothing about. 

All responses greatly appreciated.  Thanks very much in advance.

Al

---

### Post by ikt on 2010-02-05
> **Alfie O'mega said:**
> The VPN appears to be using IPv6, something I know absolutely nothing about. 

Are you absolutely 100% certain about that? 

I'm sorry I can't help you further but using ipv6 for vpn is still fairly advanced.

---

### Post by Alfie O'mega on 2010-02-05
As a matter of fact, anybody know how to actually browse IPv6 addressed websites, or if there are any?

Thanks,

Al

---

### Post by ikt on 2010-02-06
> **Alfie O'mega said:**
> 
As a matter of fact, anybody know how to actually browse IPv6 addressed websites, or if there are any?


I'm also interested in this.

[http://ipv6.internode.on.net/](http://ipv6.internode.on.net/)

> Accordingly, all downloads of data from the Internet via IPv6 is metered, regardless of whether a given site is available on an 'unmetered' basis to ADSL customers using IPv4.

Ah so I can't do it anyway :(

---

### Post by Alfie O'mega on 2010-02-06
Well.  We are descending into the realm of curiouser and curiouser.  

I'm speaking to you from the depths of a Windows box.

Currently I am connected via an IPv6 address through a Taredo tunnel, according to ipconfig and seem to be browsing the Internet just fine, although I don't feel any different on IPv6.  

Here is what happens with Ubuntu.   

I start up in normal ipv4 mode, until the IPv6 address kicks in, at which time Firefox, supposedly ipv6 enabled, then won't resolve to anything.  I'm quite unclear about how to access the resources on my company's network though, assuming I'm actually connected to that at the moment. 

Am not sure because those addresses apparently allow anybody to connect to me, perhaps just by putting in the address.  Ikt, did you connect to me yesterday?  I came across what I think was your blog--two vids on it, correct?--in the course of trying to sort this out yesterday, and can't remember if I got the ip out of the log or was searching for it.   

Wireshark lists a number of ipv6 addresses that apparently tried to connect to the number above and Nmap traces the links okay, but it's all quite a mystery how to make ipv6 work, what the ultimate benfit is, how to properly do security--I've got a shadow localhost running for example, so two ips named 127.0.0.1 resolve to localhost and I can't seem to block the ports on the one, which appears to be udp6.

At the moment I'm going to go figure out how to turn it off on Ubuntu so I can at least flick it on and off at will.  

Ipv6 is clearly a very powerful element, but it's going to take some brain power to figure out how and why to use it. 

Al

---

### Post by pranky on 2011-02-23
I've been using IPv6 now on Ubuntu for 6 months.  I use Miredo on my laptop out and about (very similar to Windows Teredo) and gogonet's client on the server for the network.  

IPv6 has built in IPsec, and shorewall6 can be configured o allow certain ip prefixes through, so you may no longer need the requirement for vpn anymore in plenty of setups.  IPv6 is still in infancy with usage, but Ubuntu Server 10.04 has allowed me to setup dual stacked website, irc chat (backend for a website), email and plenty more.  

Teredo on the Windows machine doesn't work properly (some applications can use it) de to the way the Windows DNS works.  I believe it is more in place for things like NAT traversal of remote assist ad such like and more for dedicated Microsoft products.  Miredo sets up and ipv6 tunnel, and allows full useage including DNS lookups which Windows prevents.  

Facebook's faster, BitTorrent is faster, and everything else is becoming future proof :)

---

### Post by lemming465 on 2011-02-25
> IPv6, something I know absolutely nothing about. 
Hey, you are trying to learn.  That puts you one up on not only most end-users of the internet, but even most professional IT staff, sad to say.

The internet protocols per se, both v4 and v6, live at layer 3 in the 7 layer ISO network reference model, where packet delivery and forwarding and routing happen. v4 uses 32 bit addresses to identify hosts, v6 uses 128 bit addresses.  At layer 2 we use the same IEEE 802.whatever link-layer stuff such as ethernet, wifi, wimax, etc.  At layer 4 we still use UDP, TCP, SCTP, etc.  At the application layer 7, we still use HTTP, SMTP, DNS, etc.  As some people say, "96 more bits, no magic".  It's like the conversion from analog TV to digital TV: new equipment all around, and mostly the same content.

```
anybody know how to actually browse IPv6 addressed websites
```
To browse them by raw address, put that in square brackets [], e.g. *host [www.kame.net](www.kame.net)* will show you a v6 address you can reach directly as *[http://[2001:200:dff:fff1:216:3eff:feb1:44d7]/](http://[2001:200:dff:fff1:216:3eff:feb1:44d7]/)*.  If a host only has v6 addresses such as ipv6.google.com or has both v4 (A) and v6 (AAAA) addresses in DNS, then what happens depends on your DNS server and firewall.

> ... or if there are any?
Currently the [statistics]("http://bgp.he.net/ipv6-progress-report.cgi") at ipv6.he.net suggest that only about 2% of the Alexa top 1 million web sites have IPv6 addresses.  So, on average, not yet.  However, a lot of the very top sites such as Google, Youtube, Facebook, Netflix, and CNN are already dual-stacking with both v4 and v6 accessibility.  Except on the [June 8th world IPv6 test day]("http://isoc.org/wp/worldipv6day/"), in 2011 you will mostly have to access them using alternate names such as ipv6.google.com, [www.v6.facebook.com](www.v6.facebook.com), ipv6.netflix.com, ipv6.cnn.com, and so on.  The alternate names is because large web sites see about 0.2% clients with broken or misconfigured IPv6 transport, especially older Mac's, and neither they nor the ISP's want to cope with the millions of support calls about gear they don't own and can't fix.

> ... Teredo tunnel, according to ipconfig and seem to be browsing the Internet just fine, although I don't feel any different 
IP address selection in getaddrinfo(3) is complicated; there are multiple RFC's and at least 18 rules, with all sorts of subtle interactions between address scopes, preferences, lifetimes, protocols, etc.  Plus you can tune it by editing */etc/gai.conf*.  Oversimplified, there are 3 basic issues in the ordinary case of a client with a single IPv4 address and a single global scope unicast IPv6 address (the one starting with "2"; ignore the special ones starting with "F").

(1) If the destination only has one kind of address, v4 or v6, you have to use your address from the same family, v4 or v6. Otherwise you can't talk to it, e.g. ipv6.google.com is unreachable if you have only a v4 address.

(2) If the destination has both A (v4) and AAAA (v6) addresses, prefer native sources to tunneled sources.  In the case of a typical home PC with a private RFC-1918 address getting NAT44 translation at your firewall or router, this will be preferred to a tunneled 6to4 address (2002::/16 v6 prefix) or tunneled Teredo address (2001:0::/32 v6 prefix).

(3) If it's dual-stack native all around, believe in the future and prefer IPv6.  

Visting a dual-stack site with address feedback such as ipv6.he.net will tell you whether you are in case (2) or (3) if you are uncertain.

>  ...the IPv6 address kicks in, at which time Firefox, supposedly ipv6 enabled, then won't resolve to anything
That's probably either a DNS or a firewall issue, not actually a Firefox issue.  You can explore this at the command line with ping, ping6, host, and dig. To help you diagnose this we'd need to see stuff like ```
ip address show
ip -4 route show
ip -6 route show
sudo iptables -L
sudo ip6tables -L
cat /etc/resolv.conf
```
and to know more about the network topology upstream of you.

For example, a lot of corporate networks block IPv6 over IPv4 tunnels by disallowing encapsulation protocols such as 41 (IP in IP) and 47 (GRE), plus blocking the default Teredo server port of 3544/UDP.  A lot of home networks are using wimpy wifi routers or broadband modems stuck in the dark ages where only protocols 1,6,17 and if you are lucky 2 (ICMP, TCP, UDP, IGMP) got implemented, in which case Teredo's UDP encapsulation is their only hope.

For Firefox specifically, you can control v6 versus v4 behaviors by going into *about:config, * filtering on *dns*, and adjusting the *network.dns.disableIPv6* toggle and the *network.dns.ipv4OnlyDomains* blacklist.

```
it's all quite a mystery how to make ipv6 work
```
The most prominent differences from IPv4 are: bigger addresses, fixed-size 40-byte IP packet headers, fixed sized /64 subnets at the vlan, and new roles for ICMP, multicast, and DHCP.  Broadcast doesn't scale, so IPv6 does link-local layer 2 address conversion using multicast ICMPv6 *neighbor discovery* rather than v4's ARP (address resolution protocol).  ICMPv6 *router advertisements* are now required (they were optional and rarely used in v4), and tell you which network prefixes are on-link, where the gateways are to go upstream, and flag bits in the RA's control whether or not you do DHCPv6.  Since windows XP, Mac OS 10.6 and below and some other stuff has trouble with DHCPv6, most current deployments of IPv6 use *stateless address autoconfiguration* directly off the RA's.  

In that SLAAC case, there are several possible strategies to pick a 64-bit host part to combine with the 64-bit prefix from your router to get your full 128-bit IPv6 address.  You can use an IEEE EUI-64 mapping from your 48-bit ethernet address, a privacy address that picks 62 of the 64 bits at random, a cryptographic address that hashes an RSA public key, a static address, etc.  Linux and MacOS do the EUI-64 thing by default, Windows 7 does the privacy thing by default, but all of them let you pick the other ways if you insist.

The best way to make IPv6 work is to be on a recent OS such as windows 7 or ubuntu 10.10, upgrade all your wifi routers and broadband modems to support both v4 and v6 (e.g. DOCSIS-3, DSL-X), and wait for your ISP to offer native v6.  If your ISP offers *6rd* first, that is almost as good as native.

Enthusiasts who don't want to wait for their ISP can play with 6in4 point to point tunnels from tunnelbroker.net, sixxs, or gogo6 in the interim.  For tunnelbroker.net you will need to cut and past a few commands they'll provide at the command line.  Sixxs and gogo6 can use the *tunnel setup protocol* implemented by the gogoc client.  I don't recommend 6to4, and Teredo is only for masochists.  If you must try 6to4, I like the "tun6to4" script from ISP anyweb in New Zealand.  On Ubuntu or Fedora, Teredo is provided by the "miredo" package; on Ubuntu that's controlled by a START_MIREDO variable in /etc/default/miredo, and you bounce it by *sudo /etc/init.d/miredo {start|stop}*.

> what the ultimate benefit is
There are three main ones so far: the ability to continue growing the size of our global internet, the ability to innovate again after we abolish NAT, and better support for mobile devices roaming between networks.

As there are 7 billion people using 5 billion cellphones (only 10% smartphones so far), plus billions more computers, broadband routers, etc. and a looming "internet of things", the 4 billion addresses of IPv4 just aren't enough anymore.  It turns out to be **cheaper** (for users and ISPs both), **better** (more supported protcols), and **faster** (both raw packet latency network performance and time to deploy) to switch to v6 than to linger on v4 and be forced into multiple additional layers of carrier NAT.

The IPv4 exhaustion trajectory is roughly: late 1980's move to classful routing; 1993 move to CIDR routing; 1994 introduce resuable private addresses and NAT; February 2011 IANA ran out of v4 /8's; summer 2011 APNIC runs out and goes to a policy of issuing at most v4 /22's (1024 IP's) to ISPs; fall 2011 ARIN and RIPE and LACNIC run out; 2012 most ISP's run out.  That makes 2013 the likely *year of the IPocalypse*, when new v4 is unavailable, but v6 not yet universal.  Existing v4 folks will be fine for a while, but new users and new applications will be increasingly IPv6 only, so if you don't have v6 in 2014, expect be cut off from some interesting parts of the internet.  Universal world-wide availability of v6 is probably 2015, 99% v6 traffic is probably 2017, tier-1 ISP's turning off v4 routing is probably 2020 (legacy v4 will tunnel over v6), and the last IPv4 device lingering on some intranet will finally be decommissioned around 2036.

You care about IPv6 in 2011 if you have Asian customers, Asian supply chains, mobile customers, or governement contracts. ISP and hosting providers should already have started work on v6; businesses should be v6-enabling their border services such as web and e-mail.  Consumers may sit on their hands until 2013 waiting for the availability, quality, and prices of new dual-stack v4+v6 capable wifi and broadband gear to improve. Note that all of the 4G smartphone rollouts in North America are already *dual-stack-lite*, meaning they have only native v6.  If you want to get to the legacy v4 internet from a fast smartphone, expect to tunnel a private v4 address over v6 transport to a carrier NAT44 device, and forget about gaming, voip, or multimedia performance.

Abolishing NAT is more subtle: a large installed base of NAT devices completely prohibits protocol innovation, and thus requires expensive work-arounds as a substitute.  Consider the trouble Skype has with NAT firewalls, for example; that's why they have to have "supernodes".  A NAT-less IPv6 internet will allow you to use more protocols, and has more flexibility for the future.  This particularly matters for the future of streaming multimedia, which is expensive for ISP's to deliver over v4.  In a NAT44 world, newer transport protocols such as SCTP and bandwidth saving features like multicast tend to be unsupported for decades at a time and thus effectively unusable.

> how to properly do security
IPv4 and IPv6 are both packet-switched internetwork protocols, where autonomous systems (roughly, ISP's) use BGP (border gateway protocol) to exchange backbone routes.  The threat models are basically identical.  So you want basically the same firewall rules, intrusion detection, flow logging, etc for both protocols.  Finding feature parity on IPv6 protection devices may be a challenge for the next few years, alas, but conceptually, you may treat them similarly.

If you block or allow inbound TCP connections to port 80 on IPv4, do the same on IPv6 too.  On Linux you will be using ip6tables in parallel with iptables, at bottom.  If you have private RFC-1918 v4 addresses, substitute RFC-4193 FC00::/7 *unique local* v6 addresses.  Remember there is no NAT66, so plan on either using proxy servers or firewalled global unicast v6 addresses in place of any existing NAT44.

If you are worried about IPv4 DHCP server spoofing at layer 2, then you should also worry about DHCPv6 and ICMPv6 RA spoofing.  RA spoofing is a particular concern on wireless networks, as neither 802.1x nor SEND (secure neighbor discovery) are yet widely deployed as countermeasures.

You will have to pay attention to IPv6 tunneling technologies (6in4, 6to4, ISATAP, Teredo, ...) during the v4 to v6 transition period, roughly 2009-2015.  Yes, it already started.  In general on R&D networks you want to allow tunneling, to maximize v6 access; on secure networks you want to block it instead.  After all, if you aren't doing native v6 yet, you probably aren't ready to cope with tunneled v6 either.  And if you are doing native v6, it will perform better, filter better at your firewalls, and have better visibility in your network monitoring than tunneled v6, so both your users and your security staff will be happier if you block tunneling anyway.

See [RFC-4890]("http://tools.ietf.org/html/rfc4890") for advice on properly filtering ICMPv6 - full block and full allow are equally inappropriate - and [NIST special publication 800-119]("http://csrc.nist.gov/publications/nistpubs/800-119/sp800-119.pdf") for 180 pages of deeply technical general IPv6 security advice.

---

