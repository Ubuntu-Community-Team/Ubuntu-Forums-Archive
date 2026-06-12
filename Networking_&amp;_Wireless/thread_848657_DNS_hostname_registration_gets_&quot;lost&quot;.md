---
title: "DNS hostname registration gets &quot;lost&quot;"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by shutterbc on 2008-07-03
I have an Ubuntu Gutsy desktop in an environment where DNS resolution is handled by DHCP hostname registration.

Now, I know where dhclient performs the hostname registration (successfully) in /etc/dhcp3/dhclient.conf.

I can resolve the hostname for this machine for some time without an issue.  But after a few days, I can't resolve the hostname after a while (I think the AD server throws the info away).  I don't have control of the DNS/DHCP server.

If I manually run dhclient, then I can resolve the hostname again.  Is there a way to get this to automatically run periodically (say, when the lease expires) other than me setting a cron job?

---

