---
title: "Moblock Running but not Filtering"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by zac_2_booya on 2008-09-25
I'm not sure what happened. I've used Moblock for many months now and never had a problem. I recently had to reinstall Ubuntu and I added Moblock from the deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) hardy main repository. It installed without any errors and seemed to run, but when I tested it, I was able to go to all of the websites that should have been blocked. I'll provide you with whatever information you need in order to help me figure this out. Thanks.

---

### Post by jre on 2008-09-25
You are probably using the allow option (WHITE_TCP_OUT) for outgoing on ports 80 (http) and 443 (https). This is the new default since a few versions, but you should have been asked about that during installation. So this might be, why MoBlock seems to be not working.

Try "moblock-control test" and (in doubt) post "moblock-control status".

Greets
jre

---

