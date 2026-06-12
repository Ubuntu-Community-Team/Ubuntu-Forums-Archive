---
title: "Services and Ports on Server edition &amp; Netgear DG834G"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by technologynow on 2008-07-01
I installed Ubuntu 8.4 server with **LAMP and a mail server** 3 weeks ago and before this I'd never used Linux or tried to set up a web server. I'm using a Netgear DG834G router.

I've set up a public website and can view the index page from inside my network, but **what services do I need to allow IN through my router firewall**?

The router gives me many options including Apache1, Apache2, HTTP, HTTPS and what seem to be several hundred others (I exaggerate a lot). **Which of these should I be allowing in through the firewall and on what ports?**

---

### Post by superprash2003 on 2008-07-01
apache2  - port 80
mail server - smtp port 25
              pop port 110

---

### Post by technologynow on 2008-07-01
Hi.  (Should this be in the server section - I clicked on the wrong line!)

I've opened the ports on my router, but an external probe still shows them closed and I'm not sure why.

I've double checked the server settings.  Any idea what would cause the ports to still appear closed?  I've no firewall on my PC as fas as I'm aware.

---

### Post by superprash2003 on 2008-07-01
hmm..have you tried port forwarding on some other pc with the same routeR??does it work ?

---

