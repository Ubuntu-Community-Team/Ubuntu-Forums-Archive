---
title: "Changing WPA Password on Multiple Acess Points (WIFI)"
date: 2015-05-10
forum: Networking &amp; Wireless
---

### Post by ZilogCWB on 2015-05-10
HI, 

I have 8 Access Points and every time I need to change the WPA password, I have to go one by one and change it. Is there any way to have a central location where I change the WPA password and it replies to all Access Points?

Thank You.

---

### Post by TheFu on 2015-05-10
If the APs have a central data store, probably yes. If they are all $20 cheap routers - no.
You could make them all 802.1x with RADIUS authentication and use keys going forward. Then just change the key pairs out as needed. [http://www.tldp.org/HOWTO/8021X-HOWTO/freeradius.html](http://www.tldp.org/HOWTO/8021X-HOWTO/freeradius.html) explains.

If you won't or can't switch to RADIUS authentication, it might be possible to automate through either **expect** or some automatic testing tools (think web interfaces) - which really depends on the way the WPA2 passphrase is managed.

Shared keys are ok for home users, but not in a business - except for public wifi access stuff. Even then, I'd use something like pfsense to "hotel" access for specific periods of time.

**Future:**
If this is a business, please use FreeRADIUS and have individual keys per user, so you only have to enable/disable one key when 1 user leaves the company - leaving all the others alone.

---

