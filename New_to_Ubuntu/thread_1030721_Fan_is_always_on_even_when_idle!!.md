---
title: "Fan is always on even when idle!!??"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by FAMUgolfer on 2009-01-04
I have dual boot (8.10 and XP) on an Acer 4530-5889 with 9100M nvidia graphics.  Since installing 8.10, the fan seems to be on all the time, even when on idle.  The fan isn't blowing at full strength all the time but at a noticeable slow-medium speed (sorry about my terminology).  Is this due to poor support for the newer nvidia cards.  This is also occuring when I boot into XP as well.  Why is this?  I recall before I wiped out Vista, the fan never came on unless I had at least 3 task going on at the same time in Vista.  What should I do or is this normal?  Thank you.

Also under the "Thermal Monitor" in the Nvidia X Server Settings, the core temperature reads 60C and the fan is still blowing at what seems to be at medium speed.

---

### Post by cmnorton on 2009-01-05
Start with the hardware manufacturer. If this is happening on XP, too, it could be for another reason. Also, look in your logs (/var/log). Comb those for anything interesting, where interesting might be an error or some other indicator as to why your fan is running a lot.

---

### Post by supererki on 2009-01-05
i would start with easier things... like looking in BIOS if the "fan always on" setting is enabled or not... 

Then i would use the vacuum cleaner to remove the dust or whatever which is near the fan.. this could help..

---

### Post by FAMUgolfer on 2009-01-05
Thank you for the responses. I will try both of you guys' suggestions.  I just noticed that when I unplug my charger, the fan turns off for a few minutes that turns on at full speed. Weirdness.

---

