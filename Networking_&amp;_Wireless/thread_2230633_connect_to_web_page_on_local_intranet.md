---
title: "connect to web page on local intranet"
date: 2014-06-20
forum: Networking &amp; Wireless
---

### Post by theDaveTheRave on 2014-06-20
Hi all.

I feel really silly, but I've recently discovered that I can no longer navigate to web pages on my local intranet.

I have installed some drupal sites on my local pc.

I have set up apache with virtual hosts for the names of the drupal sites, and put the site names into a hosts file on the local machine

everything seems to work with the exception of trying to access the various sites via the use of the ip address.

for instance I have the following sites.

[www.myhomepages.info](www.myhomepages.info)
[www.homewiki.info](www.homewiki.info)

and they work fine by putting those names into the browser on the same machine as the web server. so I'm happy at this.

if however I try to navigate to 
127.0.0.1 : I just get the basic apache response of 'it works' which is fine.
If use my public IP address, or my local ip addres (192.168.0.11) i just get a of Not Found
<quote>
The requested URL / was not found on this server.
Apache/2.2.22 (Ubuntu) Server at 192.168.0.11 Port 80
</quote>

the server must be running as the message for apache 2.2.22 is correct. I get the same response from the public ip, so my port forwarding must be working OK.

The strange thing is that this was working a few weeks ago. so I must have put in a config with the new sites I've added, and broken everything else?

My question is how do I get it all back, and how would I navigate the new sites I have created using the ip address.

Thanks in advance for your support.

David

---

### Post by TheFu on 2014-06-20
Virtualhosts work based on the name, not the IP.  Only the default files will be served from the IP address. If you want to visit different websites using only an IP address, then ... er ... create more IPs?

---

### Post by theDaveTheRave on 2014-06-20
so what you are saying is that I have to set up a local DNS.

I was hoping I would be able to avoid that

:)

---

### Post by SeijiSensei on 2014-06-20
You could still use a hosts file, but you'll need to assign multiple addresses to your server's Ethernet interface.  You can do this in /etc/network/interfaces as discussed [here](http://www.liberiangeek.net/2012/04/create-virtual-network-adapters-in-ubuntu-12-04-precise-pangolin/).

Suppose you assign 192.168.1.1 to eth0 and 192.168.1.2 to eth0:0, the first virtual adapter.  In Apache you would include separate <VirtualHost> definitions, one for each IP/ServerName combination:
```

<VirtualHost 192.168.1.1:80>
ServerName www.domain1.com
DocumentRoot /path/to/some/location
[etc.]
</VirtualHost>

<VirtualHost 192.168.1.2:80>
ServerName www.domain2.com
[etc.]
</VirtualHost>

```
Just make sure your /etc/hosts files map [www.domain1.com](www.domain1.com) to 192.168.1.1 and [www.domain2.com](www.domain2.com) to 192.168.1.2.

Notice that these declarations use the full "IP:80" specification in the <VirtualHost> directive, not the "*:80" that is used for name-based virtual hosting.

---

### Post by theDaveTheRave on 2014-06-20
@ SeijiSensei

I didn't know that was how it was done !

however I think that setting up a DNS will be a good experience for me anyhow.

So I'll probably do both.

Thanks for the links.

Dave

---

### Post by TheFu on 2014-06-20
Please don't make your DNS public.  I've been hacked ... thru DNS. Please learn from my mistake.

---

