---
title: "DHCP IP Renewal"
date: 2005-09-04
forum: Networking &amp; Wireless
---

### Post by numberexhaust on 2005-09-04
Everytime I DHCP, it says IP address renewal in x seconds.  Even though it might be a long time, I still would like to make it not do that, because it does disconnect me from the internet.

Any ideas?

---

### Post by s_p_a_r_k_y on 2005-09-04
dhcp renewal times are set by the DHCP server. Not much you can do about it. How long is your lease time?

---

### Post by davidbb on 2005-09-04
yeah if your isp is hosting the dhcp server, there's nothing you can do. however if the dhcp server is on a local router/server, you should be able to configure the lease time.

---

### Post by numberexhaust on 2005-09-04
its a good 2-3 thousand (actually, probably 20-30) seconds, but even then, if i keep my computer on for a while and go away, it disconnects and i have to manually reconnect when i come back.

---

### Post by numberexhaust on 2005-09-04
Fair enough, but then in that case is there a way to make it reconnect automatically whenever it disconnects?

---

### Post by s_p_a_r_k_y on 2005-09-04
ummm you could create a cron job to ask for a new lease every hour?

---

