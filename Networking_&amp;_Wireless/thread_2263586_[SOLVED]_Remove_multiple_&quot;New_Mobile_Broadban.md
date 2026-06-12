---
title: "[SOLVED] Remove multiple &quot;New Mobile Broadband GSM connection&quot; entries in nm-applet"
date: 2015-02-01
forum: Networking &amp; Wireless
---

### Post by ogilvierothchild on 2015-02-01
Hi, just posting this in case anyone has the same problem.  After 10 years of using the same Ubuntu install, each time I used a GSM phone modem appears to have added a new entry into the menu provided by "nm-applet", eventually crowding out all the normal wifi entries with 6 blocks of 4 lines each, with one active entry saying "New Mobile Broadband GSM connection" and three greyed out lines.

This was annoying since there is no way to remove those entries using the front-end.  After a bit of debugging, I realized that NetworkManager was reading connections out of /etc/ppp, so I just moved the whole thing using "sudo mv /etc/ppp /etc/ppp.bak", and voila I could now see the menu entries for wifi access points instead of all these useless GSM connections I used once in Brazil or Africa 5 years ago and will never use again.

---

