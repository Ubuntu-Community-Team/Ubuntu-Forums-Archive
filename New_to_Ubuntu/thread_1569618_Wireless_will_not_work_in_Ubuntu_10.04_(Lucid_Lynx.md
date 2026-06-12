---
title: "Wireless will not work in Ubuntu 10.04 (Lucid Lynx)"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2010-09-07
Hey everyone, I'm VERY new to Ubuntu. Like... I just installed it on a whim last week. Anyway, when Ubuntu starts up, I notice that the wireless is not working. I don't even see an icon telling me that it's on.

I'm assuming I'm missing some sort of driver. Can anyone tell me which one, where to get it, or if I'm completely off-base, how to fix this.

Please be very detailed with your answer as I am an ABSOLUTE newbie without a ton of computer knowledge. Thanks! :D

---

### Post by Chris1274 on 2010-09-07
Can you enter the command ```
lspci
``` in a terminal and then post the output here?

---

### Post by lbrty on 2010-09-07
> **Ranger_Joe said:**
> Hey everyone, I'm VERY new to Ubuntu. Like... I just installed it on a whim last week. Anyway, when Ubuntu starts up, I notice that the wireless is not working. I don't even see an icon telling me that it's on.

I'm assuming I'm missing some sort of driver. Can anyone tell me which one, where to get it, or if I'm completely off-base, how to fix this.

Please be very detailed with your answer as I am an ABSOLUTE newbie without a ton of computer knowledge. Thanks! :D

You may need to activate the wireless driver in your system. Through my experience, I followed the steps below:
Menu>System>Administration>Hardware Drivers
A window will pop-up showing 'Searching for available drivers...'
Select the the drivers suitable for your wireless card (it may have a choice of two--one being free (open source) and the other being proprietary), click activate and close.
Left click the network icon on the panel (by the clock) and the wireless networks should populate.

---

