---
title: "Can Not Recognize Router but works with Just ADSL Modem"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by lobsterclaws on 2007-01-01
My Dapper setup works if I directly plug my eth0 into the ADSL modem.  When I do this and run ifconfig I see eth0, lo, and ppp0.  I had set it up using the ADSLPPPoE forum link and created a firewall using iptables from another link I found.  Everything worked perfectly.
Then I added a TrueMobile 2300 Wireless Router and it works with my laptop both wireless and plugged in but I can not even access the router config page from my browser.
I've tried poff dsl-provider, it doesn't change anything.
ifconfig shows eth0 and lo but Not ppp0.  I am stuck.

---

### Post by lobsterclaws on 2007-01-02
I figured out the solution myself.  My firewall script had ppp0 as the interface, once I disabled it worked.  Now I changed it to eth0 and it still works fine.  I guess you don't even need a firewall with a free standing router.

---

