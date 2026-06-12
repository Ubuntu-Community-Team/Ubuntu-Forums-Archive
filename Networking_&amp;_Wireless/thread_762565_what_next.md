---
title: "what next?"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by secondstage on 2008-04-22
I've setup LAMP server and I'm able to access it locally(WAN). I am using Apache 2.2.4 (or something close), PHP 5.2.3, and have the streaming software GNUMP3d 2.8

1. Can anyone get to it from 'outside' by using my ip? 
2. Is there a good free domain to ip service?
3. What exactly is a Domain Name Server(does it have the domain name and        computers search in it to find the ip to reroute to)?
4. Can I use DYNdns even if I have a static ip(I think)?

---

### Post by Kebabman on 2008-04-22
In reply to your questions :

(By the way, saying you can access it locally(WAN) doesn't make a lot of sense, WAN is a Wide Area Network, ie this would imply accessing it from outside your Local Area Network (LAN))

1. Whether it is accessible from an external host would depend on how your network is set up. Presuming you are using some sort of router you would need to forward port 80 (presuming your web server is running on port 80) from your router to the internal host running the web server.

2. You mentioned DynDNS in your post, this is a good, free DNS service.

3. A DNS Server basically hosts a list of domain names and the IP addresses associated with those names. When you enter a domain name into your browser for example, it sends off a DNS request to a DNS server it knows about, this will hopefully know about the domain you are requesting and return the associated IP address to your PC.

4. You should be able to use DynDNS without problem on a static IP address.

Hope this was helpful.

---

### Post by secondstage on 2008-04-22
> (By the way, saying you can access it locally(WAN) doesn't make a lot of sense, WAN is a Wide Area Network, ie this would imply accessing it from outside your Local Area Network (LAN))

I thought WAN stood for wireless area network. As in the network of computers that access my wireless router

DynDNS it is then!

---

### Post by secondstage on 2008-04-22
any others that are free and DON'T make the "endofinternet" part tacked on like in

mysite.endofinternet.net

---

### Post by Kebabman on 2008-04-23
> **secondstage said:**
> I thought WAN stood for wireless area network. As in the network of computers that access my wireless router

DynDNS it is then!

WAN is Wide Area Network, wireless networks are usually referred to as WLAN's (Wireless Local Area Network) :)

---

### Post by secondstage on 2008-04-24
OK, I get it now. Thanks

---

