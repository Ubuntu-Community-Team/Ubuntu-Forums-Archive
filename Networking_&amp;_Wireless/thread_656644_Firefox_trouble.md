---
title: "Firefox trouble"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by fulvioval on 2008-01-02
Hi people. I'm new in this forum!

I have a problem, maybe somebody can help me...
I have a network with DSL-500T modem/router. On Windows XP the internet works fine, but on Ubuntu 7.10 with firefox don't...I've made an PING on [www.google.com](www.google.com) with terminal and it's ok, só network is working, but firefox don't. I set Ubunto network to DHCP client, like Windows XP...

Somebody can help me? please?

Thanks !!!

---

### Post by Sef on 2008-01-02
Applications > Add/Remove > Change top box to 'All Available Applications > search > Epiphany > then search Opera > apply > apply > close.

Those are other browsers, and use it to check if you get a connection with them.  Epiphany uses the Gecko engine that Firefox uses.  Opera use a different engine all together.  If both work then the problem is with the front end of Firefox.  If only Opera works then the problem would seem to be with the Gecko engine.  If neither work, then with the initial DHCP set up would seem to be the problem.

---

### Post by 1976dan on 2008-01-02
Type in the task bar in fire fox about:config
then scroll down to 

network.dns.disableIPv6

make sure this is set to true

---

