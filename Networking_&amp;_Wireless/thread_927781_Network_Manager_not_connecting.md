---
title: "Network Manager not connecting"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by kidnot0ri0us on 2008-09-23
New Ubuntu (Hardy Heron) user here, having probs getting Network Manager to connect to my wireless access point.

I can connect to it manually via the terminal (from the *very handy* guide on these forums), but the GUI app can't

I am using a 64-bit WEP key, entered in HEX, and my AP is a DLink DWL-2100

Any reason why my WEP key works in the console but not with Network Manager?

---

### Post by shanix on 2008-09-23
Check your syslog file from /var/log directory.

Command:

less /var/log/syslog

---

### Post by Iowan on 2008-09-23
Sometimes it is useful to go around NM.  Check contents of **/etc/network/interfaces**.  Details there *should* match what you're putting in manually... plus, there should be an "auto" line for your interface.

---

### Post by kidnot0ri0us on 2008-09-23
thanks a lot for the suggestions :)

any alternative GUI apps that you guys recommend?

---

### Post by Iowan on 2008-09-23
I've heard the name [WICD]("https://help.ubuntu.com/community/WICD"), but haven't tried it. [Here]("http://ubuntuforums.org/showthread.php?t=891969") is a thread about it.

---

