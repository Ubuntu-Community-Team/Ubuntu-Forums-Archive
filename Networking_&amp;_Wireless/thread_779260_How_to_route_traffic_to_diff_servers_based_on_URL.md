---
title: "How to route traffic to diff servers based on URL"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by TurboRush on 2008-05-02
Heres the scenario... I have a crappy little computer that hosts a few websites. My connection comes in through my router and forwards anything on on port 80 to the local IP of that server, say 192.168.1.100, I then have several virtual hosts configured in Apache. There are several other computers on the network but no traffic gets routed to them via the router, i.e., 192.168.1.101 and .102

Now, I have another site I want to set up, but the application itself is going to consume a considerable amount of resource that my current server just doesn't have. What I'd like to do is some how route traffic to another server on my network based on requested URL..

SO, traffic would flow as seen in the example below:

[www.site1.com](www.site1.com) --> 192.168.1.100
[www.site2.com](www.site2.com) --> 192.168.1.100
[www.site3.com](www.site3.com) --> 192.168.1.102

I don't think my router has the capability to do this and I haven't seen anything from reading through apache documentation...

Any ideas on how I can do this WITHOUT purchasing additional or specialized hardware?

Thanks.

---

### Post by bwhaley on 2008-05-02
Since you only have a single IP address, you only have one port 80 available to serve web sites. This is not a missing feature on your router, it's just that there isn't a way to host multiple sites on different physical servers with a single IP. 

One work around that might work for you is mod_rewrite. You put rules in your VirtualHosts that sends certain requests to another IP address. 

Here's a link with some examples:

[http://www.bloghash.com/2006/12/apache-mod_rewrite-examples/](http://www.bloghash.com/2006/12/apache-mod_rewrite-examples/)

Here are the Apache docs:

[http://httpd.apache.org/docs/1.3/mod/mod_rewrite.html](http://httpd.apache.org/docs/1.3/mod/mod_rewrite.html)

You could also look in to a reverse proxy set up with Apache or Squid. See here for one example:

[http://www.apachetutor.org/admin/reverseproxies](http://www.apachetutor.org/admin/reverseproxies)

- Ben

---

### Post by TurboRush on 2008-05-02
Thanks. I'll take a look at this..

I guess I was hoping that there was some software out there that would sit in front of the web server in the software stack that was capable of deciphering the request and then deciding which server to route to..

i.e., [www.site1.com](www.site1.com) --> router forwards to 192.168.1.100 port 80 --> some software determines [www.site1.com](www.site1.com) belongs on this server and hands off to apache

[www.site3.com](www.site3.com) --> router forwards to 192.168.1.100 port 80 --> some software determines [www.site3.com](www.site3.com) lives on 192.168.1.102 and forwards off to port 80 .102.

I knew it wouldn't be that simple... :)

---

### Post by bwhaley on 2008-05-02
An Apache reverse proxy would definitely do this for you. You could have 2 Apache daemons running on your "main" server. The reverse proxy would listen on port 80 and proxy requests to either the other systems on the network OR the other Apache instance running on a different port on the same machine.

---

### Post by TurboRush on 2008-05-02
> **bwhaley said:**
> An Apache reverse proxy would definitely do this for you. You could have 2 Apache daemons running on your "main" server. The reverse proxy would listen on port 80 and proxy requests to either the other systems on the network OR the other Apache instance running on a different port on the same machine.

Great... I'll dig deeper into this.

---

