---
title: "Domain Name behind router"
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by alexj on 2005-10-19
Hi Guys,

I am a bit lost here. I have a Ubuntu box (5.0, will become 5.10 over weekend) sitting behind Netgear router. I want the box to run my company website, so I want people to access it by my domain name.

Is it doable? I would prefer port forwarding solution rather then DMZ (router support both). 

Any help will be appreciated. 

Alex

P.S. The question is about DNS, not about Apache or how to setup a router

---

### Post by adwait on 2005-10-19
That has nothing to do with the OS you are running on the computer. You get apache2  running and host your website on the computer. How you configure the router to forward the ports to the computer concerned is another question altogether. But as such, you should be able to forward the port 80 of your router to the computer.

---

### Post by heimo on 2005-10-19
alexj, as adwait says, it's not operating system specific, but if you have any detailed questions, go ahead. If you're using "reserved addresses" for you server behind the router (which would in this case work as NAT, I guess), just point the host/domain name to your router's ip address and port forward 80 (and possibly 443) to the corresponding ports of the web server. Usually the routers web interface is quite self explaining and there's not much to configure about port forwarding - incoming port and target ip:port. Static ip addresses make life a lot easier here. First make sure that the webserver is configured properly and accessible from lan, then configure dns and port forwarding. Good luck! helpful tool: [nmap]("http://packages.ubuntu.com/breezy/net/nmap")

---

### Post by mips on 2005-10-19
Two things,

Does your router have a static or dynamically allocated IP address from your ISP ?
If it is dynamic you will have to make use of an DynamicDNS service like [http://www.dyndns.com/](http://www.dyndns.com/)
Your Netgear router should support this, mine does.

You'll have to configure port forwarding to overcome the NAT issue.

---

### Post by alexj on 2005-10-19
I guess I haven't explained my question well. It is about how to configure DNS and what ports should I forward in addition to 80.

Of cause, setting port forwarding is a router issue. 

I don't know what to do with domain name. I have static IP. Is it enough to set domain name for a server via usual network setup? Should I install any DNS package to use it? I understand, the question may sound silly - as I said, I am just a bit lost here.


Thanks

---

### Post by heimo on 2005-10-19
Hmm... Let's try to clear something first. You have some domain name registered, but you don't have DNS servers for it? Right? You probably don't want to run DNS server of your own if it's just for one webserver - actually you would need at least two DNS servers and it's just way much easier to use something like [sitelutions]("http://www.sitelutions.com/"). Create host name, point A record to the router's ip address and (on router) forward port 80 to the port 80 of the webserver. You may want to forward other ports later, if you need ssl (443) or ssh (22) connections, but that's easy to do later.

Did I understand your situation? Depending on where you registered the domain (possibly your isp) you could ask them to do the dns hosting too, but I prefer to use sitelutions (btw, which is free and works very well).

If I completely misunderstood your scenario, please clarify. :)

---

### Post by mips on 2005-10-19
If you have a static IP Address then chances are you already have a hostname allocated by your ISP but it will resemble their domain names, maybe phone them and ask. Once you have this you can use and alias (name of your choice) to translate to the real DNS name.

As for port forwarding look here, the first two links should be enough:

[http://kbserver.netgear.com/kb_web_files/n101145.asp](http://kbserver.netgear.com/kb_web_files/n101145.asp)
[http://kbserver.netgear.com/kb_web_files/n100495.asp](http://kbserver.netgear.com/kb_web_files/n100495.asp)
[http://www.portforward.com/](http://www.portforward.com/)
[http://www.homenethelp.com/web/explain/port-forwarding-dmz.asp](http://www.homenethelp.com/web/explain/port-forwarding-dmz.asp)

---

### Post by alexj on 2005-10-19
Heimo, thank you, you nailed the problem. That is exactly what I needed!

Thanks to all other contributors

---

