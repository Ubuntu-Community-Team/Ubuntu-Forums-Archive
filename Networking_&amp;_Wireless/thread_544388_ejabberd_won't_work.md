---
title: "ejabberd won't work"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by el3ktro on 2007-09-06
I've installed ejabberd from the repos on 6.06. The daemon is started and seems to run, but I can't access it at all.

I've set the "hosts" option in ejabberd.cfg to "mydomain" but when I do

ejabberdctl --node ejabberd@mydomain status

it gives me a 'nodedown' message. Also, I can't create the inital admin user or any user at all. I don't know what to do anymore, I tried several different things as hostname (localhost, mydomain.de, only mydomain, set it to the hostname of the computer which is 'otrs' etc. - nothing works)

Any ideas what's the problem?

Tom

---

### Post by tallman9 on 2007-09-09
I did the same and it doesn't work...I registered a user and made it admin in ejabberd.cfg but when I try to connect from a client or from web interface it refuses.

---

