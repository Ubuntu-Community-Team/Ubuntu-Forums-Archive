---
title: "PPPOE and outbound mail timing out"
date: 2005-10-23
forum: Networking &amp; Wireless
---

### Post by yourmanpann on 2005-10-23
Recently upgraded from Hoary to Breezy (not sure that's important since I never tried to set this up under Hoary).  pppoeconf works as expected and all is well except outbound mail.

I get "connection timed out" when trying to pass mail to the relay host. Happens under both postfix and exim, and with two different relay hosts.

This worked (with exim and both relay hosts) under Debian woody.

Any ideas?

---

### Post by yourmanpann on 2005-11-24
To answer my own question: my ISP blocks outbound port 25 so I had to reconfigure postfix to relay on port 587.

---

