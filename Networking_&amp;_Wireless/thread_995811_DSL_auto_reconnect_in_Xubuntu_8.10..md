---
title: "DSL auto reconnect in Xubuntu 8.10."
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by balintdavid on 2008-11-28
Hi. My ADSL internet connection is very unstable, 
(old telephone wires)
and drops connection every 30-40 minutes. 
I searched where can I turn on auto-reconnect in 
Network Manager but I found nothing.

I've been told to try:
"pppoeconf"
"sudo gedit /etc/ppp/peers/dsl-provider"
and remove # marks from "persist" and "maxfail 0"
but that didnt help either.

Q:
Is there an other way to enable auto-reconnect?
Or I should try an other Network Manager?

---------
I'm using Xubuntu 8.10 and the built-in Network Manager 0.7.0.
Sorry for my english

---

### Post by superprash2003 on 2008-11-28
well im not sure about this, but its worth a try, you could set up a cron task to launch the command pon dsl-provider as that is the command to connect.. so say if you want to run that command every 1 hr.. go to the command prompt and type crontab -e
then add the following line

00 * * * * pon dsl-provider

---

