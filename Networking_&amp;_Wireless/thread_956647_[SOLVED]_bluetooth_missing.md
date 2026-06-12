---
title: "[SOLVED] bluetooth missing"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by redviper on 2008-10-23
again this is a topic much debated about but after a time on google I still don't have all the answers.
I know for a fact that my laptop has bult in bluetooth, however I cannot see the bluetooth icon on screen. according to google ubuntu 8.04 (which I am using) kernel has all that is necessary and with minor software update the thing should work. this is however not the case. after "hcitool dev", I get no result.

than I moved to winxp (dualboot) and installed bluetooth there. imediately after making sure that it worker I restarted back into linux and the bluetooth was there, and "hcitool dev" was ok. next time I turned on my laptop again no bluetooth.

this is probably something very easy to solve but since i'm a total noob help is really needed. :D

thanks in advance for any suggestions.

---

### Post by redviper on 2008-10-24
Among others I followed this howto

[http://www.linuxforums.org/forum/ubu...bluetooth.html](http://www.linuxforums.org/forum/ubu...bluetooth.html)

I came to step 5 (bottom of page) and after:

sudo modprobe omnibook ectype=14

I get:

WARNING: /etc/modprobe.d/omnibook line 1: ignoring bad line starting with 'omnibook'

Any suggestions?

Regards,

---

### Post by redviper on 2008-11-02
problem solved with the above mentioned link.

---

