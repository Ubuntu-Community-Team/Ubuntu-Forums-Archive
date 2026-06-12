---
title: "Setting up BIND so that you can serve outside DNS requests"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by dash86no on 2008-07-01
Hi,

I have set up BIND9 within my local network, and everything seems to be working great. 

My problem, is that I'd like to use my DNS from outside my network. 

I have opened up Port 53 on my firewall and uncommented query-source address * port 53; in named.conf

However, i am unable to resolve DNS from outside of my network. Also, I have checked most of the log files in /var/log and can'd really find anything relating to this request being denied/blocked. 

Has anyone got any ideas?

Cheers,


Dash

---

