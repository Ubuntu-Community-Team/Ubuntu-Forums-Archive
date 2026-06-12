---
title: "[SOLVED] Screen Resolution changed after latest update (8.10)"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by manilaph on 2008-12-03
Hi,

Everytime there is an update for 8.10, I just always click on the install (and update).

After the last update after a few minutes ago, i noticed that my wired connection got cut (after the update completed and system is up-to-date). And so, I restarted the computer. 

After restarting, the wired connection became okay but my screen resolution now is totally wrong.

How can I bring back my screen to the previous resolution... I tried the System - Preferences - Screen Resolution but my choice of the proper screen resolution is no longer there.

Please help.

Thank you.

---

### Post by falcon61102 on 2008-12-03
What type of graphics chip do you have?

And have you check to see if you need to enable any Restricted Drivers for it by going to System>Administration>Hardware Drivers.

What may have happened is that your kernal got updated in your most recent update and now you have to rebuild the kernal for the graphics drivers.

---

### Post by manilaph on 2008-12-04
Solved.

What I did (which is what a newbie like me would probably do) was to check "add/remove software" and I uninstalled all the NVIDIA-related stuff. Then I restarted the computer.

In my horror, the computer became purely text only and asked if i wanted to continue or go through manual configuration or trouble-shoot.

I chose trouble-shoot and then just pressed okay all the way and the system chose the best configurations from scratch and now my screen resolution is back to normal.

All problems solved.

Thanks Ubuntu team.

I love Ubuntu!

---

### Post by falcon61102 on 2008-12-04
You may want to check to ensure that the nVidia drivers were installed again because you may be just running on the basic display drivers and won't have 3d support.

---

