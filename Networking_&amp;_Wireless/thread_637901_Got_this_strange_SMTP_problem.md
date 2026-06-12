---
title: "Got this strange SMTP problem"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by Kleenux on 2007-12-11
After migrating from Suse to Ubuntu 7.10, I couldn't send mail to x@localhost anymore.

mailq was always showing
  (connect to localhost[10.11.12.13]: Connection timed out

My postfix conf was ok imo, got the line 
   mydestination = $myhostname, localhost.$mydomain, $mydomain, ...

For some reasons 'localhost' was being resolved through the MX entry of 'localhost.com', i.e.
   ghost.localhost.com.    81514   IN      A       10.11.12.13
while host file contained
   127.0.0.1 localhost localhost.my.domain
and nsswitch.conf do files before dns

**Fix**

To fix that, I added localhost.localdomain to the host file, 127.0.0.1 entry... That works - but I don't understand why smtp was trying to resolve 'localhost' from DNS, why anyway it added a '.com' to get the resolution. I grepped localdomain in /etc/* /etc/*/*, nothing.


Does anybody has an idea? Thanks

---

