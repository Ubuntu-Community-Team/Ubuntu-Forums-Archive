---
title: "Can I install a CA certificate to encrypt my IP?"
date: 2016-12-04
forum: Networking &amp; Wireless
---

### Post by big_z2 on 2016-12-04
Can I install a CA certificate to encrypt my IP? If not how can I do this?

---

### Post by gordintoronto on 2016-12-05
A web site needs to know your IP address to send packets back to you.What you are asking for is not feasible.

---

### Post by big_z2 on 2016-12-06
> **gordintoronto said:**
> A web site needs to know your IP address to send packets back to you.What you are asking for is not feasible.

Can you elaborate on this please?

---

### Post by darren780 on 2016-12-06
This will allow you to run a server without your ip being known.  [https://www.torproject.org/](https://www.torproject.org/)  Though in the past some sites have been tracked with great effort.

---

### Post by lisati on 2016-12-06
A web server needs to know where to send the information about pages you are browsing, otherwise you wouldn't see a thing on your screen. I haven't had the need to use one, but there are services available that can help you with a degree of anonymity.

edit: Ninja'ed by darren780 with a good suggestion.

---

### Post by kpatz on 2016-12-06
CA certificates are used to encrypt data from a web server (i.e. https).  Encrypting/hiding your IP won't allow you to get to/from the internet.  Much like if you want to receive mail, you have to provide your address.  Tor is sort of like using a PO box instead of a street address.  It can still be traced, but not without some effort.

---

