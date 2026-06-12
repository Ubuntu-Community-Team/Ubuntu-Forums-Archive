---
title: "PPPoE problem after update in Edgy"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by Onyx_47 on 2007-02-14
Hi. I installed Edgy today. I ran pppoeconf, no problems, everything was working just fine. Then I updated my system throught update manager and restarted my computer. Now it won't sonnect on startup, if I run pppoeconf again it connects, but connection fails after a short time (a minute or so). If i do ponf it gives me an error, something like Remote message: authentication failed (not sure about this, but I can't copy/paste).

Everything works fine under XP thought, so it's not my ISP.

Any ideas?

---

### Post by zvacet on 2007-02-16
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")
In desktop entry Exec=gksudo /opt/rp-pppoe-3.8/go-gui replace with Exec=gksudo tkpppoe

---

