---
title: "IPv6 ordered allocation &amp; Dynamic Hosting"
date: 2019-09-17
forum: Networking &amp; Wireless
---

### Post by Anquietas on 2019-09-17
Hello friends,

I have a complex situation here, to which I partly found a solution, but let's just say I want to view all the possible angles, so I am asking for your opinions, so this e-mail is a looooong e-mail, so bare with me :)

I want to ask only experts to help me ! Please ! If you are unsure of what is being said here, please do not try to offer solutions.
I want help of professionals, who _DO_ understand these things. Thank you !

So, here goes:

I have a Linux router&services server (PC) at my home. This PC runs Linux (Ubuntu Server) and routes my Internet access and also hosts websites, e-mail, VPN, and so on...

My ISP provides Fiber connection with PPPoE connection, Dynamic IP address, up to 1 Gb/s bandwidth. It also provides dual-stack IPv4 and IPv6 and Prefix Delegation.

Having said this, the following scenario occurs:

1. IPv4:
--------
My ISP provides me 1 public IPv4 address which is Dynamic, so it changes at every new connection (powerloss, intentional disconnect, server restart, and so on...)
Naturally, behind the Server (Router) I will use Private Addresses (192.168...) and Iptables->NAT->Masquerade them to the current Public IPv4 of the PPP Interface (ppp0) or whatever is called, when I successfully dial-out.
I would have used SNAT, but for SNAT I need a fix IP address. So I use MASQUERADE.
(Q0: Is it possible to SNAT to a dynamic IP address ? to spare MASQUERADE an extra lookup of the dynamic ip on ppp0)

So no problem here, so far.


2. IPv6:
--------
Here is a little bit of problem, as my ISP provides Prefix Delegation with a dynamic class.
Let's call this example class: "2001:db8:a:b::/64".

Q1: Upon connecting with "pon isp" (pppoeconf), how does my IPv4 and IPv6 addresses get assigned to my PPP interface ? Is there some internal mechanism or using DHCP ?

Also, my ISP provides the prefix delegation, so that every IPv6-enabled device on my internal LAN will try to get the Prefix Delegation and try to form its own IPv6 address using EUI-64 Mechanism. (Stateless (SLAAC)).

Q2: I want to use an ORDERED Ip address assignment mechanism. So, instead of "2001:db8:a:b:1234:12FF:FE34:5678" (SLAAC generated address), I want the following:
"2001:db8:a:b::1/64", "2001:db8:a:b::2/64", "2001:db8:a:b::3/64".
So, similar to "192.168.0.1", "192.168.0.2", "192.168.0.3", I want to ORDERLY assign addresses, but using the dynamic prefix given by my ISP.

So, if the ISP changes the class to: "2001:db8:a0:b1::/64" for example, I want to be able to address my devices like this: "2001:db8:a0:b1::1/64", "2001:db8:a0:b1::2/64" and so on...

So, regardless of what dynamic IP (IPv4) and Class (IPv6) I obtain from my ISP, on my local side I want to use fixed addresses (In IPv4 is easy by using fixed private addresses, but in IPv6 I don't know how to allocate fix host-side addresses)


I hope I made myself clear until now :)
Okay, let's say I resolve the addressing part. Every device has it's private IPv4 address (using MAC-based DHCP) and every device has it's IPv6 address derived from the dynamic network part and the stable host part, so everything is OK, we go to the next chapter:


3. Dynamic DNS Hosting:
-----------------------
My server also hosts some websites, e-mail, vpn and so on...
Yeah, I know, having a Dynamic IP does not really help the hosting business... :(
And no, I do not want to pay twice (double price) for my Internet subscription to get a static IP, both IPv4 and IPv6....

My ISP offers me a Dynamic DNS service on-the-fly, without software clients needed, but only for their dynamic IPv4 address assigned. They left out IPv6 :(

So, I need to get a real dynamic DNS service which operates on both IPv4 and IPv6.

I heard of some major players in this field: dynu.com, he.net, dyndns, afraid.org, no-ip, etc...

Q3: Which is your recommendation, what experience do you have with the above DDNS providers ? Which one is the best ? The best meaning instant update of new addresses, the lowest possible TTL for lowest possible downtimes.

P.S. I do NOT want to host my DNS zone at some other provider. I have my own BIND DNS Server so I want to personally host my domains. I only want a FREE DDNS HOSTNAME acting as an intermediary between my dynamic IPs and my domains.


4. Technical workaround to avoid CNAME. DNS records for dynamic IP:
-------------------------------------------------------------------
To describe the technical path a DNS query takes is beyond the scope of this thread.
Simply put: I have some domains. At my registrar, I declare the nameservers for those domains as being the free dynamic dns host.

For example, I register "username" at the "ddns.provider" (which can be any of the above providers) and I get a hostname "username.ddns.provider" which automatically points to my Dynamic IPs (both IPv4 and IPv6) and it gets instantly updated with my IPs via a software client called "ddclient" or some other means....

How can I instruct my BIND DNS Server to update A & AAAA records automatically with the new addresses of the PPP0 interface ?

I want a BIND configuration similar to the below one (a very simplified example):

"
SOA {...}
NS		username.ddns.provider
MX	10	mail.domain.suffix
domain.suffix IN	A	{PPP0_IPv4ADDR}
domain.suffix IN	AAAA	{PPP0_IPv6ADDR}
mail.domain.suffix	IN	A	{PPP0_IPv4ADDR}
mail.domain.suffix	IN	AAAA	{PPP0_IPv6ADDR}
"

I do NOT want to use CNAME. I know that the easy way is to use like this:

"
domain	IN	CNAME	username.ddns.provider
"

But this causes extra recursive lookups and may cause some problem with MX and Mail Hosting.

I want to update the Zone file automatically with the current IPs of the PPP0 interface (both Ipv4 and Ipv6) so that the client recieves a clear A or AAAA record to connet to further down the road, and no CNAME (aliases) are involved.

Q4: How can I do that ? :) How can I bridge somehow the "pppoe" and BIND to update my zones with the new IPs from ppp0 interface ?


5. Reverse DNS & Outbound mails:
--------------------------------
Yeah, this is a tough one...
I am afraid that my ISP does not offer me a custom reverse DNS for my IPs as my IPs are changing constantly...

Do you know of other methods to secure or improve my e-mail server in order for my mail to get delivered corectly ?

Blacklisting the ISP IP range is not so common these days because my ISP blocks port 25 and only allows it based on a formal request by a client.

DNSSEC doesn't seem to help, SPF records, domainkeys ?... I only want to be able to send e-mails from my server (using ISP dynamic IPs) and get delivered corectly.


So, basically, these are my concerns.

Please, if anyone can help, offer some suggestions, it would be greatly appreciated !

---

