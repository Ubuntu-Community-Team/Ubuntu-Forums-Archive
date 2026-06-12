---
title: "Intel Wireless 8260 not working after fresh install of Ubuntu 16.10"
date: 2016-10-22
forum: Networking &amp; Wireless
---

### Post by richard650 on 2016-10-22
Intel Wireless 8260 [8086:24f3] (rev 3a), 
Subsystem: 8260 [8086:0130], iwlwifi


Tried numerous posted solutions (> 8 hours). 
Nothing worked. Finally figured out it's the
firmware.


/lib/firmware/iwlwifi-8000C-22.ucode ==> NO WIFI
/lib/firmware/iwlwifi-8000C-21.ucode ==> WORKS!


workaround: move or rename -22. then -21 is loaded.

---

