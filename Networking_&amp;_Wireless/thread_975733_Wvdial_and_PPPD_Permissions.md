---
title: "Wvdial and PPPD Permissions"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by RMOP on 2008-11-08
I just moved from 8.04 to 8.10. The same configurations for using my BT Phone as a modem still works, BUT, when I invoked wvdial, it ONLY worked if preceded by sudo. Otherwise, I got a permissions error. That was not an issue with 8.04 AFAIK.

I have temporarily worked around this by:

sudo chmod a+x /usr/sbin/pppd

While this works, I'm quite sure that there is a better (safer) set of permissions that should work. But I can't figure out what it would be.

Help??

---

