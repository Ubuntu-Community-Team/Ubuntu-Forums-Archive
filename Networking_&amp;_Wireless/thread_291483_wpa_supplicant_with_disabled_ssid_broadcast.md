---
title: "wpa_supplicant with disabled ssid broadcast"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by mahy on 2006-11-02
G'day,

i tried disabling ssid broadcast on my router, but the most tangible result was my wpa_supplicant unable to associate. Can somebody give me advice as how to achieve it? TIA

---

### Post by wieman01 on 2006-11-02
You have seen this thread before, but the solution is described in here: [http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

But you may not like the idea of editing "/etc/network/interfaces" yourself. The relevant section would be:
> wpa-ap-scan 2

---

### Post by mahy on 2006-11-03
> **wieman01 said:**
> You have seen this thread before, but the solution is described in here: [http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

But you may not like the idea of editing "/etc/network/interfaces" yourself. The relevant section would be:

Thanks, i already did it that way. However, i'd still prefer to do it the old-school way, mostly because i have to restart networking every time after reboot to get it connected...

---

### Post by wieman01 on 2006-11-03
Ok, there is a solution posted (same thread) for the "restart" problem as well. Check it out, works fine.

But I understand the concern. Some like it, some don't. :-)

---

