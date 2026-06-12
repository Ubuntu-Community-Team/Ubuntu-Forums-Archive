---
title: "Limited browser problem"
date: 2005-08-16
forum: Networking &amp; Wireless
---

### Post by Geir Smestad on 2005-08-16
I have had some internet issues with my Ubuntu laptop since I installed a router to connect multiple machines to my ADSL connection. The two XP machines on the network work fine, but the laptop doesn't. I am able to ping both IP addresses and web sites, but I am unable to open a web site in a browser. (I have tried both Konqueror and Firefox.) I do get some data from the site, and the browser communicates the "Looking up..." and "Connecting to..." messages, but halts at "Waiting for... [site address]". The progress bar in the lower right corner of Firefox halts at about 50%. Do any of you have an idea what is going on here?

The router is a Klin NE-4904SX, if that is of any interest.

---

### Post by cenithx on 2005-08-16
[QUOTE=Geir Smestad]I have had some internet issues with my Ubuntu laptop since I installed a router to connect multiple machines to my ADSL connection. The two XP machines on the network work fine, but the laptop doesn't. I am able to ping both IP addresses and web sites, but I am unable to open a web site in a browser. (I have tried both Konqueror and Firefox.) I do get some data from the site, and the browser communicates the "Looking up..." and "Connecting to..." messages, but halts at "Waiting for... [site address]". The progress bar in the lower right corner of Firefox halts at about 50%. Do any of you have an idea what is going on here?

The router is a Klin NE-4904SX, if that is of any interest.[/QUOTE]
 Need to edit your resolv.conf and put in your ISP's DNS servers, then lock the file.

That's what I did anyway, and it fixed it for me :)

Still a noob so might wanna double-check that with someone more experienced though, that locking the file wont disturb anything, but i've had it like this for 2 weeks now and it fixed everything perfect :)

---

