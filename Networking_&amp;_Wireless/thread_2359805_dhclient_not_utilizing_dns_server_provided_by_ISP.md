---
title: "dhclient not utilizing dns server provided by ISP"
date: 2017-04-28
forum: Networking &amp; Wireless
---

### Post by linuxjb on 2017-04-28
Ubuntu 16.04, 

During the week ending 4/21, I was able access the internet whether from home, using my provider's DNS, and at school using the locked down DNS, both handled automatically.

Over the weekend something changed, and now at seems the DNS request is not receiving the default--the only way I can access the internet is after editing the /etc/resolv.conf file to specify nameservers. I have similar results whether using wireless or ethernet cables.

I discovered this when I was testing using nslookup and saw it would timeout unless I specified the dns server.

Do you have any ideas what is 'broken' and how to fix it?

Thanks

---

