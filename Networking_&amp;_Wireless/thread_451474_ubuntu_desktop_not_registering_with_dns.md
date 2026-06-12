---
title: "ubuntu desktop not registering with dns"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by amani on 2007-05-22
hi

i set up ubuntu desktop, and it gets its ip address via dhcp. the network connectivity works fine.

i can ping the machine by ip address, but not by hostname. i've been scratching my on this one for a few days.

any suggestions would be greatly appreciated. thank you in advance.

amani

---

### Post by kidders on 2007-05-23
Hi there and welcome,

Normally, it's the DHCP server's job to update DNS. Most administrators consider it inappropriate to allow remote alteration of DNS records, because of the potential for malicious interference. Having said that, you can make Ubuntu *try* to perform the update, if you really want/need to.

What kind of DNS service are you running?

Depending on where DNS updates are coming from on your network, your DHCP configuration may also be important. For instance (as an obvious example), updates being propagated by a DHCP server won't be performed for static leases.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

