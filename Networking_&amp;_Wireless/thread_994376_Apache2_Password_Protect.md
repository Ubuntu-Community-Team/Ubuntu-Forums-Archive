---
title: "Apache2 Password Protect"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by lateralus01 on 2008-11-26
I am hosting a site with apache2 and I password protected it.  My problem is, once I type in the password once my IP is cached somewhere because I'm never asked for a password again unless I try to connect from a different IP.  Anyone know how to fix this?

Thanks,
Lateralus01

---

### Post by sammy_pal on 2008-11-27
> **lateralus01 said:**
> I am hosting a site with apache2 and I password protected it.  My problem is, once I type in the password once my IP is cached somewhere because I'm never asked for a password again unless I try to connect from a different IP.  Anyone know how to fix this?

Thanks,
Lateralus01
I don't think the server is caching your ip address. Most probably, your browser is saving the authenticated session. Try clearing your browsers cache and authenticated sessions. (Clear private data - if your are using Firefox) and then accessing the site again.

---

### Post by lateralus01 on 2008-11-28
> **sammy_pal said:**
> I don't think the server is caching your ip address. Most probably, your browser is saving the authenticated session. Try clearing your browsers cache and authenticated sessions. (Clear private data - if your are using Firefox) and then accessing the site again.

yep you were right, doing that and logging in with a different browser required me to enter a password again.

thanks,
lateralus01

---

