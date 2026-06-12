---
title: "Router problem or something else?"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by aceron on 2007-01-04
Hey So I followed the steps [here]("https://help.ubuntu.com/community/ApacheMySQLPHP") to make a server.
I set up an account with dyndns (made sure it was dynamic)
I installed wordpress in /var/www and all was going well....then i plugged in my router instead of going directly through the cable modem
its a linksys i went in and set up the ddns for dyndns
and port forwarded 80
now whenever i try to go to my site it brings me to the routers admin page
note that all was working well and fine pre-router (meaning i could go right to my site via browser)
did i miss a step? does this mean that my isp is blocking 80? or do I have a setting messed up somewhere?
I realize this may be a question asked often so I did search the ubuntu forums but found nothing that could fix my problem
oi, any help would be appreciated

---

### Post by DerHesse on 2007-01-04
I think you cannot connect to your site from your own home network, but from outside you can. Have you tried it from somewher else?

---

### Post by aceron on 2007-01-04
I have done it before on a server someone else set up for me, however i tried to reconfigure xserver and now i cannot log into the desktop is my current problem

---

### Post by DerHesse on 2007-01-07
> **aceron said:**
> I have done it before on a server someone else set up for me, however i tried to reconfigure xserver and now i cannot log into the desktop is my current problem

Have you tried restorin a previous version af your xorg.conf?
There might be a backup in /etc/X11/   . Just copy it over the actual.

---

