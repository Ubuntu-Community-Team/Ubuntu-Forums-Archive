---
title: "Bind9 Not Using New Settings"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by BadServo on 2008-11-25
This is an odd situation.  Hopefully someone can shed some light on things.

I previously setup a Hardy server installation.  It served 4 purposes:

-Ubuntu Repository  (debmirror, rsync, apache2)
-Ubuntu PXE Server
-DHCP Server  (dhcp3-server)
-DNS Server  (Bind9)

Things have been working beautifully ever since.  A few days after the release of Intrepid, I performed an in place upgrade of the server.  This *appeared* to go smoothly and things continued to work as expected.  Today I setup squid on the server to do proxy caching for my LAN.  It is configured and is working fine, including youtube caching.

Here's were things fall apart.  Previously, if I wanted to add a new machine to my network, I'd simply put it's hostname and mac info into my dhcpd.conf file.  Then put it's IP and CNAME aliases in my hosts and rev file under bind/zones.  I'd then restart each service and the changes would take effect immediately.

Now, my changes do not take effect.  No matter what I do (restart services, restart networking, flush cache) the new settings will not take effect until I reboot the system.  This is hardly ideal.

Can any offer any possible suggestions for what may be causing this issue?  Any help is appreciated.

---

