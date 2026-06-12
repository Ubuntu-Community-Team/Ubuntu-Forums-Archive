---
title: "pdnsd fails to start up"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by yesudeep on 2008-05-04
I've installed pdnsd and resolvconf for persistent DNS caching for my small network.  The problem I'm facing however, is that pdnsd does not start up at boot time.  Yes, I have modified /etc/default/pdnsd
to the recommended START_DAEMON=yes.

pdnsd simply fails to start up at boottime, no matter how many times I enable or disable it.  It works fine if I start it manually.   How do I get it to start up automatically?

I'm using Hardy Heron.

Cheers,
yesudeep.

---

### Post by fiatguy85 on 2008-06-18
Thank you for this, I didn't even realize mine was not starting up, but it wasn't!  Anyhow as a workaround I just added pdnsd -d to /etc/rc.local and that starts it up.  Not sure about a more proper fix.  I briefly looked through the logs and couldn't find any errors on startup.  It does have entries in the rc init directories.

---

