---
title: "Plug n Play Networking Cards -- Anyone known how to rescan the PCMCIA bus?"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by kevdog on 2008-11-22
While Ubuntu is up and running and I unplug and swap out a networking card via PCMCIA, the card is never recognized until a full system reboot.  Any way to force Ubuntu to rescan the PCMCIA bus?

sudo /etc/init.d/dbus restart
sudo /etc/init.d/networking restart

That didn't work

---

