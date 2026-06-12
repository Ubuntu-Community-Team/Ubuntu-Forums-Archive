---
title: "[Apache]renew SSL"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by analoog on 2007-05-30
I want to renew my self signed certificate. 
Its out of date and I moved to a new domain.
I looked into the documentation and tried various things but I need some help..

I use Apache 2.

---

### Post by psusi on 2007-05-30
If you changed host names then you need to issue a completely new cert, not renew the old one.

---

### Post by analoog on 2007-05-30
so I need to edit the file ssl in /etc/apache2/sites-enabled/ and regenerate apache.pem?

---

### Post by psusi on 2007-05-30
Yep.

---

### Post by analoog on 2007-05-30
okay thanks psusi :D

---

