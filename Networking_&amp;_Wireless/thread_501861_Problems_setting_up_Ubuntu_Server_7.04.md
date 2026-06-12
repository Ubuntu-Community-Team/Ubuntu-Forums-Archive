---
title: "Problems setting up Ubuntu Server 7.04"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by ragrim on 2007-07-15
Well ive spent days working on this problem and searching for answers with no luck so here goes, oh and sorry if this is the wrong section.

im setting up a spare box with ubuntu 7.04 server using this guide

[http://www.howtoforge.com/ubuntu6.10_firewall_gateway]("http://www.howtoforge.com/ubuntu6.10_firewall_gateway")

Now everything was going fine till i went to start shorewall and got this error

```
Starting "Shorewall Firewall": not done (check var/log/shorewall-init.log)
```

So i checked the logs and found this

```
Starting Shorewall....
Initializing...
   ERROR: The 'norfc1918' option has been specified on an interface with an RFC 1918 address. Interface:eth1
TerminateROR: The 'norfc1918' option has been specified on an interface with an RFC 1918 address. Interface:eth1
Terminated
```

Now.. after some research i found out what this rfc1918 thing is. i removed rfc1918 from my interfaces file and then shorewall starts fine, problem is once shorewall starts i cannot access my server via webmin anymore, i can still ping it and i can still connect to it through PUTTY.

i get the feeling im missing something here, like allowing access to port 80 or something like that, ive looked though all config files i can find and still found nothing, to be honost the setup of this is far more complicated than i expected.

only experiance i have ever had with firewalls was the ones built into modem routers so allowing access to port 80 and so on was easy.

Any help on this would be muchly appreciated. Thank you!

---

