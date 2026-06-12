---
title: "A way to determine the number of UDP packets received?"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by mothbitten on 2008-05-15
Greetings,

I would like to monitor the number of UDP packets received by a server, since data is transmitted to us in that fashion. My plan is to use nagios to monitor the results, but first I need to be able to get the data.

Utilities like IPtraf show it in a graphical format, and sar gets close as well, but I need something where I can run a command and get the information on received UDP packets per second.

I suppose I could do a tcpdump cron job and run a script on the results, but that seems like a complicated thing to do for something that may be more easily obtained otherwise.

Thanks!

---

