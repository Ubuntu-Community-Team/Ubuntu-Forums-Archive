---
title: "Forwarding based on hostname"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by Kallin on 2008-04-12
I have multiple domain names that are directed at a single IP. What I would like to do would be to analyze all requests coming in on port 80 (or any port for that matter), and direct them to the port on the appropriate server.

IE, i have domains a.com, b.com and c.com all pointing at 1.1.1.1. 

a.com uses apache, b.com is a grails app, and c.com is tomcat. I need to find a way to forward all requests to the appropriate server based on the url in the header i guess.

Any ideas wold be appreciated!

---

### Post by nixscripter on 2008-04-12
> **Kallin said:**
> I have multiple domain names that are directed at a single IP. What I would like to do would be to analyze all requests coming in on port 80 (or any port for that matter), and direct them to the port on the appropriate server.

IE, i have domains a.com, b.com and c.com all pointing at 1.1.1.1. 

a.com uses apache, b.com is a grails app, and c.com is tomcat. I need to find a way to forward all requests to the appropriate server based on the url in the header i guess.


The first thing I would suggest is giving the interface receiving all your traffic multiple IPs, each of which you can assign to a domain. a.com would map to 1.1.1.2, for example, while b.com would go to  1.1.1.3. Then you can bind each service to port 80 on that IP only.

If this isn't possible, because your IPs are being assigned by someone else, I do have a rather more complex suggestion. I think apache can do this...

Set up another apache server which does nothing but refer to the others based on domain name. Calling the three services you have now A, B, and C, then you would start another server D, which would analyze the requests as you suggest. This would forward those connections to other ports inside the box, ports with high numbers no one is using, like 2000 for A, 2001 for B, and so on. Then, A, B, and C could be configured to listen on those port numbers.

It seems rather complex. My real suggestion would be to run everything from a single service in subdomains (mysite/a.com/files and mysite/b.com/files all serviced by one process), but multiple applications seems to be a requirement from your question.

I hope this helps.

---

### Post by Kallin on 2008-04-14
Thanks for the advice!

Ideally I'd have seperate IPs for each domain and this would be trivial. However I only have one dynamic IP assigned from my run of the mill ISP, which I have my domains automatically resolve to via easyDNS. It's not the most 'enterprise' of setups, but I've got one decent rig here running an vmware of ubuntu which I'm using to serve everything. More of a demo server for whatever sites I'm developing than anything else...

You suggest using apache to 'refer to others' based on domain name. Do you mean that apache has built in functionality for forwarding requests to other IP/ports based on hostname? Maybe you suggest I write something like a PHP app to analyze the headers and then forward? I'll dig into the apache docs to see if it can do what I want without fuss..

---

### Post by nixscripter on 2008-04-19
> **Kallin said:**
> You suggest using apache to 'refer to others' based on domain name. Do you mean that apache has built in functionality for forwarding requests to other IP/ports based on hostname?

I really meant just an HTTP referral (303 See Other) from yoursite.com/blah to yoursite.com:highport/blah as another URL. This would cause a new request to the service running on port highport I'm pretty sure apache can do that.

>  I'll dig into the apache docs to see if it can do what I want without fuss..

That's my best recommendation. ;-)

---

### Post by CrazyGuy123 on 2008-04-19
another way to do this without having to refer the client would be to use a squid proxy.  The proxy recieves every request and sends it on to the right server.  As the response comes back from the server, squid sends it on to the client.

If configured right, squid behaves entirely transparently so the clients won't ever know you're using a proxy and the servers won't need any special configuration.

Proxys like that are used in many big websites (wikipedia, youtube) to direct the request to a different server depending on which page is wanted.  They're also used to "redirect" the request in case the web server stops working.

---

