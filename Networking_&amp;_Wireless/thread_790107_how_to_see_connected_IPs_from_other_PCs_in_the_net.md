---
title: "how to see connected IPs from other PCs in the network"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by D!V00NE on 2008-05-11
hi
we have a private network with invalid IPs. our server has a valid ip and connected to the internet and other PCs connected to the internet through that. we have ubuntu 7.10 desktop edition on the server.

i want to know that PCs saw which sites or what IPs??? something like a log or cache. i know that its exists but don't know where it is.

excuse me if my question is a bit :confused: but i can't find anything searching.

thanks.

D!V00NE.

---

### Post by Bill magee on 2008-05-11
Hi D!VOONE,

I am not sure if this is what you need, but in order to scan hosts on an entire network you can use nmap:
```

sudo nmap -vv -sP 10.0.0.0/24
```

-vv for max verbosity. -sP tells nmap to perform a ping sweep.

(This command straight from Negus and Caen, *Ubuntu Linux Toolbox*)

Cheers,
Bill

---

### Post by .rdg on 2008-05-11
I would install a proxy on your server (squid or safe-squid) and run it transparently for users.

I assume you just have a rule in netfilter (changed by iptables) that just makes a SNAT (Source Network Address Translation), so entire local network shares one public IP. For squid to run transparently you would have to make rule such as:

iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 80 -j REDIRECT --to-port 3128

What this rule does is it REDIRECTs the traffic which is destined for TCP port 80 (HTTP) to the default squid port, which is 3128. That would make your users unaware of being proxied, but proxy keeps a full log of what users watch etc.

Keep in mind that analyzing logs what people do on Internet you might be doing something illegal (depends on country and situation, but it may be so). Hope you have a good reason for doing that.

---

### Post by Bill magee on 2008-05-11
Ah, I see what D!VOONE means now. 

.rdg, assuming a setup such as you describe can users get their privacy back someway? For instance Tor?

---

### Post by .rdg on 2008-05-11
Sure they can as long as they are security aware. The simplest solution would be using a simple outside proxy (anonymous public one for example). Tor is a multiple-step proxy, so it would  be just as good, but not better (I assume tor just moves you through a series of proxies without encrypting your connections). More secure way to hide their Internet browsing would be setting up a tunnel, so that the connection would be encoded when going through the first step - the gateway.

Anyways - how's setting up squid going on?

---

### Post by D!V00NE on 2008-05-18
thank you all for answers. but i didn't want to do anything illegal or take users privacy away. our users must only visit the sites that they are working with. and this is in their contract but some of them not doing their job. because of that i want to know if their seeing other sites or not.

maybe there is another way by restricting IPs to domains that they can view and blocking any other domains. in this case there is no need to view the cache and users have privacy.

but i don't know how!!!:(

---

