---
title: "Internet just stopped working"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by RockxLee on 2007-05-22
I have my linux box connected to the internet through my wired Dlink router. I have been using it trouble free for the past few months and all of a sudden it doesn't seem to be getting a signal. I have tried a direct connection and still no good. My other pc connected to the same router works fine, and also tried switching up the wires and still nothing. I haven't messed around with any network settings

Does anyone know what is wrong?

---

### Post by codesplice on 2007-05-22
Are you running DHCP on the router, and do you have the appropriate settings for your network card enabled?  I'd suggest using a terminal to ping along the path to see where your issue might be:  ping the router first, then your ISP's gateway, and then an external webpage.  Hopefully that might help to isolate the problem.

---

