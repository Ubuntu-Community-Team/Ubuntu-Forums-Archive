---
title: "Galeon Web Browser and Proxies"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by kvdbreem on 2008-02-22
I just had a strange issue.  I was trying to download some updates but I kept getting this error saying that i couldn't connect to 192.168.1.102.  Then I remembered that I'd set up a proxy server at that address and then taken it down earlier, running Galeon through that server.  

Question is:
Is Galeon supposed to mess up your entire http connectivity?  I tried pulling down google's homepage with wget and got the same error, "no route to host 192.168.1.102:8009".

I removed the proxy settings in galeon, closed that browser, restarted my terminal session, and everything seems fine now.  Anybody else seen this problem?  It sounds to me like a galeon bug, unless galeon's supposed to configure a user's entire http proxy settings etc...  Firefox didn't have a problem though....  Odd.

---

