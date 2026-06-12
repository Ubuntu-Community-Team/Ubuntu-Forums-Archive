---
title: "DHCP requests new lease right after getting one"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by diverse_izzue on 2007-03-29
Hi,

I'm running Feisty, nm-applet, wireless.

My admin is complaining, that my machine requests new DHCP leases even though it just got an address several seconds ago. Does anyone have an idea?

Cheers,
Alex

---

### Post by spd106 on 2007-03-29
I suggest you gather as much information/logs as you can and open a bug report in launchpad.

---

### Post by diverse_izzue on 2007-03-29
What logs would that be?

---

### Post by spd106 on 2007-03-29
Start with the /var/log/syslog and it might be useful if you could get an excerpt from the dhcp server's client log, though that's probably unlikely.

---

