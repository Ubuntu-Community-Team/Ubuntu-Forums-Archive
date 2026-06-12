---
title: "Access your computer by dynamic dns from within the network"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by sefs on 2007-07-19
Hi, all I've been having this problem for a while, but would like to see if i can solve it now.

I can access a computer on my internal network from any computer outside of the network But if i try access the same computer by the same dynamic dns address from with in the network its a no go.  There must be a setting somewhere safegauring such access.

Any ideas?

Thanks.

---

### Post by amadeus266 on 2007-07-19
External addresses and internal address are different. Find out what your internal address for the machine in question is and I bet it'll work.

---

### Post by t1n0m3n on 2007-07-19
I suspect you are running into a NAT U-Turn problem.
when you are using nat, your cannot access the outside natted address from the inside.

---

### Post by sefs on 2007-07-19
I want to access it from the external address, so i dont have to go outside my network to see if its working.

---

### Post by sefs on 2007-07-19
Yes thats it i think.

> **t1n0m3n said:**
> I suspect you are running into a NAT U-Turn problem.
when you are using nat, your cannot access the outside natted address from the inside.

---

### Post by tturrisi on 2007-07-19
> **t1n0m3n said:**
> I suspect you are running into a NAT U-Turn problem.
when you are using nat, your cannot access the outside natted address from the inside.
Sure you can!  I have a deb server that I access from any comp on my lan and can also access it by it's fqdn (turrisi.org).  The name is parked at Domain Direct and I use their free domain  forwarding to route to my isp assigned dynamic ip (which changes once about every 2 years).  I can even access my sites from the server web browser using the fqdn or wan ip.  If you cannot do theis then your router (port forwarding) is not set up correctly.

---

### Post by netztier on 2007-07-20
> **tturrisi said:**
> If you cannot do theis then your router (port forwarding) is not set up correctly.

Yes it *is* set up correctly.

A proper firewall does and should forbid such "U-Turn" connections: proper antispoofing rules refuse internal source adresses (in this case probably some 192.168.0.x addresses) and the external interface's own address as source address on an incoming packet.

Some advanced firewalls (such as Cisco's PIX) offer a form of DNS mangling - they observe a DNS query going out to an external DNS and realize that the reply contains an IP address that they have a static translation (read: a port-forwarding) for. They'll then mangle the internal IP address into the DNS reply, so the internal client will talk to the server using the internal IP address.

The solution to the OP's problem is to tweak name resolution in the local network, by either keeping a hosts file on all internal systems that matches the external name(s) to the internal addresses, or by running a local DNS server that fakes authority for the external domain name; it gives back the internal IP address of the Server when queried for the external name.


best regards

Marc

---

### Post by tturrisi on 2007-07-20
> Yes it is set up correctly.
How do you know that?  We have not seen his configs.

I reread all above posts above and don't see that he said he is running a firewall (iptables) on the server.  I don't.  I use a router with nat as my hardware firewall and could care less about outbound firewalling (this is not an ecommerce-production server & all I need is to block all unsolicited requests)

If he is using a router then the port forwarding is not setup correctly w/ dyndns service.  Most newer cheap home routers have a ddns client built into them.  If he is using a ddns client on the server itself and is using iptables then he may have such issues as he described unles he uses a modified hosts file.  But using the hosts file won't allow him to check if the ddns name resolution works for others outside his lan.

His best best is to have someone else, a trusted friend or trusted volunteer try to connect to his server from outside his lan.

What's the ddns url of the server?

---

### Post by netztier on 2007-07-20
> **tturrisi said:**
> How do you know that?  We have not seen his configs.

My apologies! Let me split a hair or two:

My emphasizing "yes it is" was short-sighted and primarily meant to make a counterpoint to your statement, which said:

> If you cannot do theis then your router (port forwarding) is not set up correctly.

With this, you were saying that a router/firewall that did not support U-Turn connections was "not set up correctly" - which is wrong: There are perfectly well-configured routers and firewalls that forbid such connections, exactly because of a well-designed and strict setup.

My insisting that it was configured correctly is of course wrong, because it's based on an assumption that I cannot verify - there might be other config errors, after all. However, I have reason to believe that the port-forwarding configuration on the OP's router seems to be correct - as he/she states that form outside the network, things seem to work well.

Yet, a router/firewall configuration is not per se incorrect because it forbids U-turn connections.  I'd even go as far as to say that a firewall/router configuration that *allowed* U-Turn connections is to be considered incorrect, exactly because it does. But this is getting philosophical... :-)

Most of the small SOHO-class hardware routers I have come across don't allow for connections that loop back into the external interface - you might have fallen lucky that yours seems to do it - or does it do DNS rewriting? 


best regards

Marc

---

### Post by t1n0m3n on 2007-07-20
*shrug* seems obvious to me, its how NAT works.  As netztier stated the OP will need to do some name resolution magic to make the computers on the inside resolve to the correct inside address.  This can be done by host files, or an internal DNS server.  (To name a couple of ways to do it.)


> **tturrisi said:**
> How do you know that?  We have not seen his configs.

When you have this statement (or similar):

[QUOTE=sefs]I can access a computer on my internal network from any computer outside of the network[/QUOTE]

The terms "Inside" and "Outside" are indicative of NAT being used.

tturrisi:  I challenge you.  From the network that you were talking about: visit [http://www.dslreports.com/whois]("http://www.dslreports.com/whois")

The IP address that shows up in that link.... try to ping it...

---

### Post by sefs on 2007-07-20
I don't know about this name mangling dooflickery but what i did to get it to work was to install foxyproxy and when i want to test the domain name from an internal machine I turn on the foxyproxy thing so it probably tricks the nat into believing its coming from a real external address.

---

### Post by tturrisi on 2007-07-21
> **netztier said:**
> My apologies! Let me split a hair or two:

My emphasizing "yes it is" was short-sighted and primarily meant to make a counterpoint to your statement, which said:



With this, you were saying that a router/firewall that did not support U-Turn connections was "not set up correctly" - which is wrong: There are perfectly well-configured routers and firewalls that forbid such connections, exactly because of a well-designed and strict setup.

My insisting that it was configured correctly is of course wrong, because it's based on an assumption that I cannot verify - there might be other config errors, after all. However, I have reason to believe that the port-forwarding configuration on the OP's router seems to be correct - as he/she states that form outside the network, things seem to work well.

Yet, a router/firewall configuration is not per se incorrect because it forbids U-turn connections.  I'd even go as far as to say that a firewall/router configuration that *allowed* U-Turn connections is to be considered incorrect, exactly because it does. But this is getting philosophical... :-)

Most of the small SOHO-class hardware routers I have come across don't allow for connections that loop back into the external interface - you might have fallen lucky that yours seems to do it - or does it do DNS rewriting? 


best regards

Marc

Fair enough then.
I suspect that his issue may have more to do with dyndns than anything else.
I have Linksys 8 port router )befsr81).  I have a parked domain and use the registrar's domain forwarding to forward to my wan ip address.  The name resolution is done by the registrar.  So if one types: [www.turrisi.org](www.turrisi.org) it resolves to (eventually) my wan ip address.  It does this from any computer inside or outside my lan.  Now, a key difference in my setup may be this:  On all my lan computers I do not specify dns ser vers to use and I use the router to handle name resolution because a home router will maintain a table of the isp's dns servers.

As you knoiw, there are several ways to setup networking in windows and other systems.  On windows, if setup dhcp, then windows will pull the dns server table and cache it.  If use static addressing on the lan comp then one can specify exactly which dns servers to use, and I use 192.168.1.1 as the dns server, which causes the router to use its resources for name resolution rather than nput that load on the op sys.  This way, one also never has issues with windows sometimes buggy dns cache corruptions.  I also never use a hosts file on windows either. 

Now, I'll bet the op could type his wan ip address and get the server site to load locally.  

Another thing that may be the reson I can do this and others cannot is because I am not using port 80 for my www serve.  A home router is always listening on port 80 anyway, and won't allow port 80 connnections from outside the lan unless either port forwarding is being used or remote mgmt is toggled ON.  Thus, you are correct in that it is really a security issue to allow "loopback type" port 80 connections.  (when I first got cable internet in 2000 I could do a scan of the isp network and get thousands of isp addresses, then connect to the users' home routers or win98 boxes!)

As for my linksysy, I can use my domain name in any windows or linux lan system and watch the lights and see that the router queries my isp dns to resolve my domain name, then loads the page.

btw, I am not spell checking as I'm sitting outside now and the screen is hard to see.

---

### Post by cybersean3000 on 2007-07-25
Use DNSMASQ as your internal (behind the firewall/nat) DNS Server:

[http://www.thekelleys.org.uk/dnsmasq/doc.html](http://www.thekelleys.org.uk/dnsmasq/doc.html)

-=cybersean3000=-

---

### Post by cybersean3000 on 2007-07-25
Sorry for two consecutive posts, but dnsmasq is available for ubuntu: 

[https://help.ubuntu.com/community/Dnsmasq?highlight=%28dnsmasq%29](https://help.ubuntu.com/community/Dnsmasq?highlight=%28dnsmasq%29)

-=cybersean3000=-

---

