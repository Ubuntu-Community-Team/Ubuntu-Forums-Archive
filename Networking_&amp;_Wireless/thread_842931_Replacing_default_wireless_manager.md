---
title: "Replacing default wireless manager"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by pteri498 on 2008-06-27
I am not home very much these days, and as such I love to remote into my computer with ultravnc (remote desktop) or putty (ssh).

However, when I need to restart my system for whatever reason, I lose complete access because the wireless manager requires me to put in my keyring's password after logging in before it can connect to the internet, in order to access my router.

I would rather have my WEP key handled on a level where I need not ever interact with it. Is there a way I can do this?

Thanks.

---

### Post by spd106 on 2008-06-28
In this instance you need to bypass Network-Manager because it doesn't support system-wide settings yet (v0.7 does).

Start by opening System -> Admin -> Network and in the Properties of your interface disable roaming mode. Then proceed to fill in the wifi settings.

Normally in this situation I would also recommend that you set a static address as you don't really want it to ever change, but it's up to you whether you do this or just stick with DHCP mode.

Your settings should now come back automatically on a restart, but this has been a problem for some people. Some have found that editing the init scripts to restart networking after boot helps. There are lots of threads about this already on the forum.

---

