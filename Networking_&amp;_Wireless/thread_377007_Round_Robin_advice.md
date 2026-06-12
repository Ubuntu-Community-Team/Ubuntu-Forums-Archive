---
title: "Round Robin advice?"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by jcpunk on 2007-03-05
I am setting up redundant servers and was looking to do some basic load balancing while I play with [http://linux-ha.org/]("http://linux-ha.org/").  I have a CN entry for time.mysite.tld and was wanting it to map back to ntp1.mysite.tld ntp2.mysite.tld and ntp3.mysite.tld (which are in themselves aliases if that matters).  

I have been working with webmin usually for my DNS stuff, but it doesn't want to let me do this.  Does anyone know how I can set this up?  I would really like to be able to have the load dispersal until I get a good clustering setup (and also for services that really don't need cluster level redundancy (and also for my own knowledge)).

I am running Bind for my DNS server if that matters....

---

