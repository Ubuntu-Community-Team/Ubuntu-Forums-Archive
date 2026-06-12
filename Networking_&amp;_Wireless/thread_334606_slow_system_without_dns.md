---
title: "slow system without dns"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by docwex on 2007-01-09
I have a problem with my laptop:

whenever i use it without a network connection to look up for the DNS the system gets really slow. I've checked a couple of other threads with similar problems and allready tried to fix it by disabling ipv6 via blacklist and removing all ipv6 host entries, with no luck.
When I remove my DNS entries in the Network Settings, everything seems to be back to normal again, even without a network connection.

Another strange Problem was, that the connection to the network would just die, after a while, but i seemed to have fixed that by removing the 127.0.1.1 entry in /etc/hosts (which i didn't need anyway).

Anyone has an idea how to fix that? 

I was considering to set up something like pDNS and redirect requests to a local cache, but right now i don't have the time to play around with the system to much, especially since i doubt that will help much, as DNS requests still will be made eventually.

Thanks in advance for any help.

---

### Post by teaker1s on 2007-01-09
[http://ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns]("http://ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns")

---

### Post by docwex on 2007-01-09
thanks for the quick reply, but that didn't help. 

I don't think it has something to do with instability, as everything works if the system can actually find the DNS. The problem arises e.g. when i have no internet connection at all or when I'm in a different network (like the university) with it's own DNS.

If at all it felt like it made things worse, rather then better.

---

