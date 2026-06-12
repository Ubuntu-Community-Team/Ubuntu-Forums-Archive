---
title: "Intell pro/1000 (82566DM-2) missing when installing virtualbox"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by wazzup on 2008-02-27
Just an observation (maybe it'll help someone).

When I just installed virtualbox and rebooted a while later my eth0 was missing. It appears virtualbox needs the 2.6.22-14-server kernel which somehow doesn;t support this onboard intell ethernet. Switching back to 2.6.22-14-generic brings back the network, but prevents virtualbox from working.

So, no virtualbox for me I'd rather have a network connection :)

---

