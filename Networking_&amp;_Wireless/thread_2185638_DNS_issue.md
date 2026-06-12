---
title: "DNS issue"
date: 2013-11-03
forum: Networking &amp; Wireless
---

### Post by mjwestkamper on 2013-11-03
I have an office with a static IP. I have a number of other sites, remote data collection and employees, that are dynamic.

What I would ike to do is to enable those within by little domain to find each other without all the acrobatics needed to resolve the addresses of each machine.

I have tried the Dynamic IP DNS. Of late it has become costly, and difficult to maintain a DNS entry. It used to be easy and free, however it has been "Improved....."

Since I have a Static IP in Internetland I thought, why not setup a DNS that all the folks in my little domain cound use to find everyone else and my servers in the offcice?

Seems like the "simple question" requires a non-simple knowledge base.

I Have a Internet facing box with a static IP running ubuntu 12.04. I currently use it for a private website and and ftp server. It is not an Internet Domain, but I could make it one.

If someone with a lot more knowledge than I could point me down a road that I can follow to setup a DNS (BIND or other) that would fit into the wild and allow my dynamic IP folks to find each other and the office I would ber greatly appreciative.

Mike

For reference - I am somewhere between a novice and mildly knowledgable about IP.

---

### Post by btindie on 2013-11-04
Take a look at [http://www.kirya.net/articles/running-a-secure-ddns-service-with-bind/](http://www.kirya.net/articles/running-a-secure-ddns-service-with-bind/) which should allow you to do what you want. The alternative being is to create your own VPN.

---

