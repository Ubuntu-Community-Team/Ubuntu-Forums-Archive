---
title: "Confusing DNS(?) issue"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by Hammer89 on 2008-05-22
For some reason my laptop (running Ubuntu 8.04) is failing to connect to some hosts. [www.pidgin.im](www.pidgin.im), for example. Odd thing is, if I put the IP address for pidgin.im into my browser, it loads fine -- leading me to believe it's some sort of DNS issue. Prior to having trouble, I had messed around with some firewall settings (I had installed firestarter, but I've since remove --purge'ed it... I've also messed with UFW, though I dont see why that should have caused any DNS issues). I'm by no means a networking expert, though I'm usually a quick learner. Any help would be appreciated.

---

### Post by superprash2003 on 2008-05-22
this is usually a DNS issue.. you could try changing DNS servers to opendns [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by tigerplug on 2008-05-22
> **Hammer89 said:**
> For some reason my laptop (running Ubuntu 8.04) is failing to connect to some hosts. [www.pidgin.im](www.pidgin.im), for example. Odd thing is, if I put the IP address for pidgin.im into my browser, it loads fine -- leading me to believe it's some sort of DNS issue. Prior to having trouble, I had messed around with some firewall settings (I had installed firestarter, but I've since remove --purge'ed it... I've also messed with UFW, though I dont see why that should have caused any DNS issues). I'm by no means a networking expert, though I'm usually a quick learner. Any help would be appreciated.


Yeah seems to be a DNS issue.


Try resetting your router. If that fails it could mean that there is a problem with your ISP's DNS servers.

You could configure your router / computer to use a different DNS service such as OpenDNS mentioned above.


Good luck ;)

---

### Post by Hammer89 on 2008-05-24
Thanks guys... it seems to be working fine at the moment. 

Here's the thing that confuses me though... it seems that this issue occurs only after I mess with UFW (Ubuntu's "Uncomplicated Firewall"). The way I resolved the issue was by running ipconfig /all on a windows machine under the same network... and then wrote down the DNS servers listed (there were 3)... and then opened Ubuntu's network utility, added the two IP's that I didn't already have... and ran sudo /etc/init.d/networking restart. Afterwards it worked perfectly... but then just about a half hour ago I went to turn off UFW's logging... and immediately afterwards I Was having DNS issues again. So I went back into the networking utility, noticed the two entries were missing, so I re-added them... and restarted /etc/init.d networking. Again... working fine.

I've never had a single DNS issue with Ubuntu prior to enabling UFW. So I dunno what to think...

---

