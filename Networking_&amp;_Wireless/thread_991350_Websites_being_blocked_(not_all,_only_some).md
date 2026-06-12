---
title: "Websites being blocked (not all, only some)"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by meggark on 2008-11-23
Hi,

I'm running Xubuntu 8.10 on my Acer Aspire One. Everything is running great and exactly the way I want it, except when i try to visit google.co.uk or news.bbc.co.uk I get a page load error. This happens in any browser, and if I try to ping either of them, I instantly get a host cannot be found error. I know these sites work fine, as I'm on them with my desktop (also running Xubuntu. I get the same problem on any network, and it is only these two sites.

Anyone any idea what the problem may be?

Cheers,

Mark

---

### Post by binbash on 2008-11-23
edit /etc/hosts and put those lines and try google.co.uk: 

google.co.uk 209.85.129.147
[www.google.co.uk](www.google.co.uk) 209.85.129.147

---

### Post by meggark on 2008-11-23
thanks, but still having same problem. I can access the sites via the IP addresses, and I've also cleared the DNS cache, forgot to mention that earlier

---

