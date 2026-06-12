---
title: "iwl3945 and power management"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by jun0ne on 2008-05-10
I'm running Hardy x86_64 and the old ipw3945 drivers in Gutsy used to automatically go into power management mode when on battery power. The new iwl3945 drivers do not. I have to manually set it each time.

Does anyone know how I can automate this process?

TIA

---

### Post by chili555 on 2008-05-10
Is this a command you issue, similar to *sudo iwconfig eth1 power saving 3*? I suggest adding the command, without sudo, to */etc/rc.local.* Make sure it's on its own line above exit 0.

---

