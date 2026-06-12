---
title: "Firestarter question"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by ehderube on 2011-02-26
Ok,

I am running pokerstars through wine on 10.10.  When I run the pokerstars it can't get through the firewall and I have to for a short time (10 sec.) change my security settings for outbound traffic in firestarter from restrictive to permissive.  Once pokerstars is connected I can switch with no problems.  My questions are how do I work around this?  ANd is this a security issue with ubuntu?

---

### Post by wojox on 2011-02-26
You should install Gufw and use ufw that should already be installed. Firestarter is not being developed any more I believe.

---

### Post by ehderube on 2011-02-26
Thanks, Ubuntu should really indicate what is current and not...

---

### Post by 3rdalbum on 2011-02-26
Turn off the outbound filtering entirely - for a single computer it is of no benefit at all.

---

### Post by ehderube on 2011-02-26
Why is the outbound filter no use?

---

### Post by 3rdalbum on 2011-02-26
> **ehderube said:**
> Why is the outbound filter no use?

Firewalls are really meant to stop incoming connections from unknown, possibly malicious computers. Since you're using Linux the chances ate infinitesimal that your computer is malicious, so no need for an outgoing firewall.

---

