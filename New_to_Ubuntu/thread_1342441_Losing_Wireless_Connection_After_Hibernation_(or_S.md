---
title: "Losing Wireless Connection After Hibernation (or Sleep, Not Sure)"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by frigate13 on 2009-11-30
I don't have a screen saver on my laptop (I don't even know if one is available, I haven't had Ubuntu long enough), and when the computer goes into hibernation, or sleep, or whatever it is after I haven't used it for a while, I lose my wireless internet connection.

If I restart the laptop, I get my wireless connection back.

Any ideas on how I can remedy this?  It wasn't happening last Friday when I first installed Ubuntu.

---

### Post by slumbergod on 2009-11-30
I have had some weird wireless issues with Karmic (actually, Jaunty wasn't perfect either). In my case, everytime I got disconnected from the wireless network in the office I would have to reboot to get back online.

In the end, someone did make a suggestion that worked for me. Basically, I had to unload the kernel's wireless drivers then reload them. It saves rebooting but it is still disappointing that anyone should have to do this at all, especially given the "maturity" of the Ubuntu project.

In my case, I have Intel's 3945 wireless chip so I have to issue these commands:
# modprobe iwl3945
# modprobe iwlcore
# modprobe mac80211
Then again in reverse order to reload them.

If you have a broadcom chipset handling wireless you could jump over to the wicd forum. The guy who helped me listed the kernel modules he has to reload for broadcom on his pc.

Good luck.

---

