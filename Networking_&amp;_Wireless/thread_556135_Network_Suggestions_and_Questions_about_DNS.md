---
title: "Network Suggestions and Questions about DNS"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by atjensen11 on 2007-09-20
Hello,

I am (perhaps becoming a "was") avid Windows user.  I decided to install Ubuntu server to broaden my horizon.

I would like this server to be a print server, file server, and web server for several different web sites I design and host.

I have a DSL broadband connection that is connected to my router (192.168.100.1).  On this network, I have a Windows XP latop and desktop, both of which are connected to the router wirelessly using DHCP.  The Ubuntu server is connected by ethernet jack to the router and is assigned a static IP address (192.168.100.2).

I am thinking about heading down the path of using Virtual servers in Apache to host the different sites.

My question really comes to what, if any need do I have for a DNS server.  My DSL connection is like most in that I am assigned a Dynamic IP address.  I have used DynDNS for testing purposes, but don't know if this is really a long term solution.

So I looking for input from others who have head down this road before.  I only have a few weeks of Ubuntu under my belt, so please bear with me through the dumb questions.

Thanks.

---

### Post by helgman on 2007-09-21
Hello!

I've not been down that path myself but:

> **atjensen11 said:**
> I would like this server to be a print server, file server, and web server for several different web sites I design and host.

[...]

I am thinking about heading down the path of using Virtual servers in Apache to host the different sites.

My question really comes to what, if any need do I have for a DNS server.  My DSL connection is like most in that I am assigned a Dynamic IP address.  I have used DynDNS for testing purposes, but don't know if this is really a long term solution.

I guess the different web sites all have different DNS-names? And since you have a dynamic IP-address, every time it change the DNS-records of all the sites would have to be changes. I'd say no to the need of running your own DNS-server. It would work fine for your private network, serving the internal IP-addresses of the server (192.168.100.2) but for the outside world ... maybe.

All your sites should be aliases for the DynDNS-name, that is, when ever someone tries to access one.if.your.sites.com they are redirected to the IP-address of your.dyndns.org address.

To not blur this post further:

DynDNS should work for you. I'm not sure if there are any nice scripts trying to take your IP-address and updating your DNS-records on the fly but as I recall BIND (DNS-server) needs to read the new configuration every time it's changed. If you give more information about your site-name setups (are they all registered with DynDNS or do you own your own domains etc), it will be easier to point you in the right direction.

Regards,
Helgman

---

### Post by atjensen11 on 2007-09-21
Right now, I am using the free service at DynDNS.  With the free service, you have to append one of their domains to the end of yours.

So for example, I have a domain hosted by GoDaddy at [www.digitaltoolbox-inc.com]("http://www.digitaltoolbox-inc.com").  I purchased the domain through them and their DNS servers handle the DNS requests.

I have another site, [www.ourwaitingarms.com]("http://www.ourwaitingarms.com") that is also hosted by GoDaddy.

I would like to eventually move these two site and a few others in house to my server.

The DynDNS domain is [www.digitaltoolbox-inc.dnsalias.com]("http://www.digitaltoolbox-inc.dnsalias.com").

Hopefully that helps you more to answer my question.

Thanks.

---

### Post by helgman on 2007-09-22
It does!

Now, I'm no DNS-expert but I have some understanding of how it works AND I've also had domains hosted by webhotels. The thing is that when you buy a domain you are in charge of the DNS for that domain. The one in charge of the top-domain (com in this case) points all requests for information about your domain (IP-addresses connected to addresses like [www.digitaltoolbox-in.com](www.digitaltoolbox-in.com) or mail.digitaltoolbox-inc.com) to a DNS-server in charge of your domain. So if you run your own DNS-server you have to have records with the .com-servers pointing at your server.

So far so good.

IF you are lucky (and I know nothing about this) then you can use a FQDN (that is an address) instead of an IP-address to tell the com-DNS-server where to send requests for information about your site. IF that is possible then your DynDNS-name can be used and you can run your own DNS-server.

If you are not so lucky you'll have to use an IP-address (not the DynDNS name but your IP-address) - in that case you'll have to change your IP-address registered in the com-servers every time it changes. If you're lucky like me it doesn't change a lot ... if your unlucky ... I hope you see the problem there.

But ...

If you set up your own DNS-server then all you have to do is keep your DynDNS-account running and point your www of both your domains to a CNAME record that points at your DynDNS domain. But then you'll have to figure out some other stuff about HOW DNS-servers work as well ... :)

If you are really serious about hosting them and so on you should try to get a static IP-address, then the redirection of the DNS-requests from the com-servers will all work like a charm and so on and all the uncertainties above will go away. But you'll still have to learn about DNS ...

I'll gladly try to answer any other questions you have about this or clarify anything that is unclear in this post, just let me know.

Regards,
Helgman

---

### Post by wxman on 2007-09-25
> **helgman said:**
> 

If you set up your own DNS-server then all you have to do is keep your DynDNS-account running and point your www of both your domains to a CNAME record that points at your DynDNS domain. But then you'll have to figure out some other stuff about HOW DNS-servers work as well ... :)

If you are really serious about hosting them and so on you should try to get a static IP-address, then the redirection of the DNS-requests from the com-servers will all work like a charm and so on and all the uncertainties above will go away. But you'll still have to learn about DNS ...

I'll gladly try to answer any other questions you have about this or clarify anything that is unclear in this post, just let me know.

Regards,
Helgman

Hi Helgman

I'm asking you this because you sound like you know a lot more than I! 

I maintain 16 web sites on a rented server, and I'm thinking of switching to a server based here at home instead. I can get a great high speed DSL connection, no block on port 80, and a single static IP address. I'm an old pro at setting up sites by telling Godaddy, or whoever, to point to our name server. With a single IP address,  and 16 different domain/sites, do I still need to set up a DNS server too?

I'm planning to use Ubuntu Server, Apache, PHP5, MYSQL. I'm also going to need FTP and SMTP/POP3 setups as well.

Sound like fun??!!

---

### Post by helgman on 2007-09-26
Hello vxman!

> **wxman said:**
> I'm asking you this because you sound like you know a lot more than I!

[..] I'm an old pro at setting up sites by telling Godaddy, or whoever, to point to our name server.

I have a lot of theoretical knowledge. By helping others I get a chance to see that it works in real life ... and so far so good. Sound like might have some real life experience instead. Anyhow ...

A few questions:

1) Does the great high speed DSL have a great uplink? (That is, can the uplink support the traffic going from you sites?)

2) If you need SMTP you've got to make sure that the ISP allows traffic on port 25? (The reason I asking is that mine don't, not even to a relay server controlled by them.)

3) In the quote above you say that you are use to pointing things to you name server, if you don't know if you need a DNS server then what is that name server? (Is it any server or is it a DNS server but you're just not sure if you want to run one at the moment.)

If you can make Godaddy point all traffic for you domains to your IP address and you are only going to have one server doing all the work then it MIGHT work ... but you've got to make sure that

a) Godaddy points both domain.com and [www.domain.com](www.domain.com) to your IP address and

b) that Apache know that [www.domain.com](www.domain.com) and domain.com is really the same domain.

c) You also have to make sure that Godaddy has a MX record for mail pointing at your server (for every mail using domain I think).

As for the hosting part, it sound like fun. Personally, if I was running a server 24/7, I'd set up my own DNS as well. It's not all that much work and all the domains look more or less the same so once one domain is up and running you can do a lot of copy and paste to get the others up in no time.

These are my (current) thoughts on the subject.

Regards,
Helgman

---

