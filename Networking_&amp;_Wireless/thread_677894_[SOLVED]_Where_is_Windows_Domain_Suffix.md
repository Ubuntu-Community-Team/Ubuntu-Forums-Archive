---
title: "[SOLVED] Where is Windows Domain Suffix?"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by cmnorton on 2008-01-25
This question encompasses CUPS (because I noticed this defining a printer), SAMBA, and Windows.

Our domain is Arlington1.local. But, in Windows, when I browse our network, our domain shows up as Arlington1. Linux recognizes that our domain really is Arlington1.local, and I recently fixed a long standing misunderstanding in resolv.conf by changing the search directive from Arlington1 to Arlington1.local.

But, when I go to define a printer in CUPS' interface Under System --> Administration --> Printing, the domain found is Arlington1, not Arlington1.local.

Is this a bug in Windows? If so, what is it? I've seen some posts in these forums about suffixes, but they did not answer this particular question, which is where is the ".local" suffix?

---

### Post by spd106 on 2008-01-26
You have probably read that Ubuntu uses Avahi for mdns and that mdns doesn't  like .local domains. This could be the cause of your issue, but I don't know that for certain.

Perhaps have a read through this page for some more information.
[http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal)

Good luck.

---

### Post by cmnorton on 2008-01-27
> **spd106 said:**
> You have probably read that Ubuntu uses Avahi for mdns and that mdns doesn't  like .local domains. This could be the cause of your issue, but I don't know that for certain.

Perhaps have a read through this page for some more information.
[http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal)

Good luck.

Thanks. Avahi might explain why CUPS expects the domain name without the prefix. I've still got to find out why Windows' My Network Places does not list the suffix.

---

### Post by cmnorton on 2008-02-07
My understanding of why Windows My Network Places displays the domain name without the suffix is because the NETBIOS name is being displayed, not the full domain name.

---

