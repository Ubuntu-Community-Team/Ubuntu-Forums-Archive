---
title: "Ping problem"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by mlucool on 2007-09-08
I can ping ip addresses like: 64.233.187.99 [google]
But when I try to ping google.com it will not work: ping: unknown host google.com

What do I need to change to make this work on Ubuntu server.

---

### Post by rickyjones on 2007-09-08
You probably need to configure the correct DNS servers for your computer. For example, you could add the following to your /etc/resolv.conf file:

```

nameserver 192.168.1.1

```

Of course, replace the 192.168.1.1 with the correct IP address of your DNS server.

This assumes you assigned a static IP address. If it is DHCP then the /etc/resolv.conf file should be correct - you may wish to check it and see what it says.

-Richard

---

### Post by mlucool on 2007-09-08
thank you so much. It worked! this solved all my problems

---

### Post by rickyjones on 2007-09-08
You're welcome. :)

---

