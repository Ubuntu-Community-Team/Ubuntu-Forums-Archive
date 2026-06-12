---
title: "Get list of all apaches running on network"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by mevets on 2007-08-27
I am running apache on my network. My IP is determined by DHCP and manually setting it is not an option. Nor can I enter the host name (ex: [http://theserver](http://theserver))

So, I was wondering if there was a way could search my network for servers that are set up. Is that possible?

---

### Post by kidders on 2007-08-29
Hi there,

Do you mean you want to be able to identify your *own* web server? The lack of proper DNS on the network you're using seems a bit weird, but can't you simply check what its IP address is, after you start up the machine with the web server on it?

Assuming that you can't for some reason, your options are limited to:
[LIST]
[*]Finding a way for the web server to notify you of its IP, perhaps via email, or another web server somewhere with a know address.
[*]Methodically scanning your entire subnet for Apache servers running on standard ports. (If you can't predict what port the server will be on, this option would take a *very* long time.)[/LIST]

---

