---
title: "Virtual Mailserver ?"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by Barriehie on 2008-10-20
I'm currently running a server with dyndns redirecting my hostname to my machine.  Does this mean that for me to setup a mailserver on my machine it will be a virtual mailserver???  i.e. I'ld only have a non-virtual server if my machine was dynamically assigned an IP?

Thank You,
Barrie

---

### Post by cariboo on 2008-10-20
The only thing dyndns does is redirect request to your current ip address. It keeeps track of your changing ip address. your mail server will be a real mail server, though it may not be very useful, as most email servers do a hostname lookup and if your hostname isn't registered with ICANN your email will probably get bounced.

Jim

---

