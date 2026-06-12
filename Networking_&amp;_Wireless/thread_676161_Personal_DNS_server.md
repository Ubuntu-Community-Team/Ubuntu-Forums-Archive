---
title: "Personal DNS server?"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by Anovadea on 2008-01-23
Hi all,

I have, what is probably a weird question. *****

I'm running ubuntu on a laptop, and use it both in college and at home wirelessly (you'll see why I think this is worth mentioning in a second).

What I want to do is set up some sort of personal dns so as to redirect some sites to my personal webserver, which I'd typically do with /etc/hosts, but I want to take any subdomain into account.

For example, if I wanted to point anovadea.test to 127.0.0.1, I'd just use /etc/hosts, but what I want is that I want *.anovadea.test to point to that domain.

More to the point, I want to override some existing sites in existence in the internet (i.e. let's say I'd point google.ie to localhost along with all the subdomains).

What would be a good way to go about it? I'm looking at tutorials for bind, and I'm wondering if it's too heavyweight for what I want to do.

Also, because I use this machine on a number of different networks, the resolv.conf will be probably be overwritten when I get onto a new network, so how would I get it to use my dns server when I connect to a new server?

So, is this do-able, or am I looking at this entirely the wrong way?

Thanks
Aoife
***** Basically, the entire reasoning for this is that when I'm in college, if you leave your machine unlocked, the other students have a nasty habit of browsing to "shock sites". While it's funny and all, I would like to be able to steer some of the the requests away to my own webserver.

---

### Post by HermanAB on 2008-01-23
You can use BIND to do that.  It is complex, but doesn't consume much resources on a machine.

Cheers,

Herman

---

### Post by lintoolman on 2008-01-23
Maybe a proxy server would be better or less complex?  Look into squid to see if it suit your needs. Just a thought.

---

