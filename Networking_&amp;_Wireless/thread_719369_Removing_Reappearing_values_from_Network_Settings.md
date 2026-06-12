---
title: "Removing Reappearing values from Network Settings"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by Hero Doug on 2008-03-09
For me the internet on Ubuntu has been horribly pathetic out of the box. I changed the ([window scaling](http://ubuntuforums.org/showpost.php?p=3617526&postcount=12) and now use the [OpenDNS](http://www.opendns.com) DNS servers which seems to help some (I can at least use the net now).

(When setting up pppoeconf I told it not to rewrite the dns file with the dns servers provided my my ISP. I edited the dhclient.conf file to prepend the opendns servers and not request any from my ISP.)

When I start up my computer I notice there is a third dns server listed, and a private domain listed, neither of them are my doing. Does anyone know how I can prevent these values from being entered upon startup?

---

