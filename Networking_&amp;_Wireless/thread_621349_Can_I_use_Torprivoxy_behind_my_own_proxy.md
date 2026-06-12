---
title: "Can I use Tor/privoxy behind my own proxy"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by morrin on 2007-11-23
Hi

Apologies if this has been answered before. There are pages and pages in multiple postings about Tor/Privoxy but I can't get one that answers my question directly.

I'm behind a local proxy -- i,e all my internet traffic has to go through proxy1.organisation.com:8080 . I tried messing around wih Tor/Privoxy and the only way that I could get it to work was to change and uncomment, in /etc/privoxy/config, the line 

forward   /                  proxy1.organisation.com:8080
forward   .organisation.com   .

However when I look at [http://torcheck.xenobite.eu/](http://torcheck.xenobite.eu/) it tells me my own address which means that it's not working. I think that I am just sending everything through my own proxy as normal. 
I followed a few of the troubleshooting setups on this and other sites but to no avail.

Can I use the Tor network if I have to go through this specific proxy to access the outside world in the first place. Do I need some kind of fancy software for chaining proxies or something. 

If anybody has a quick and easy answer for me I'd be very grateful.

I'm only trying to learn about this stuff so any help would be greatly appreciated.

Thanks in advance.

---

