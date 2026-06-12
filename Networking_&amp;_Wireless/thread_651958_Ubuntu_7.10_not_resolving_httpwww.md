---
title: "Ubuntu 7.10 not resolving http://www"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by Garraff on 2007-12-28
Hi there everybody.
Please I am begging you, help me.
This has been an ongoing problem for me for months now, and I have searched the Net flat trying to find a solution, I have followed all links and applied all suggestions, but to no avail.
I have a fresh install of Ubuntu Server 7.10 on one machine, and a fresh install of Ubuntu Desktop 7.10 on my laptop.
The problem is this, I can access the internet from my laptop using firefox 100%
From the terminal I can ping [www.facebook.com](www.facebook.com) for example, and I can access that page from my web browser.
However if I ping [http://www.facebook.com](http://www.facebook.com) the terminal returns "unknown host http://www.facebook.com"

The reason I say this has been ongoing is because I had the same problem with an install of Debian Sarge.


Since the Server has no GUI I can only access the Internet from the terminal, and it works 100%, all updates run fine, everything works, except me pinging [http://www](http://www)
This normally wouldnt be such a huge problem except I am setting up a Squid proxy on the server and when the client makes a request through Squid the page pops up with a DNS error, because the address always begins with [http://www](http://www) and the server cannot resolve it.

Please can somebody help me.
Thanking you in advance.

---

### Post by Mba7eth on 2007-12-28
> **Garraff said:**
> However if I ping [http://www.facebook.com](http://www.facebook.com) the terminal returns "unknown host http://www.facebook.com"


Ping is not an http protocol, Ping is a different protocol(i.e. ICMP). Therefore ping will not know anything about http. One more thing in DNS ppl usually map every URL to an ip address. The url doesn't define what protocol is running in your server(e.g. http, ftp, ...ect). 
I advice you to stop searching .... you'll lose more time for nothing :) .... 
I hope your misunderstanding is clear now :)

---

