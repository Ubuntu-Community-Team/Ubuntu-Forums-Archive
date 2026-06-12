---
title: "Weird wireless issue when I reboot"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by shaggy999 on 2008-09-10
So I'm running Hardy Heron 8.04 Server (system is too slow for even xfce environment) on an old PII and I bought a wireless card for it that claimed to come with linux drivers. When I plugged it in Ubuntu did not recognize it, and I think that's because the driver might be blacklisted (it's an RTL8185-based card). So anyway, I used ndiswrapper and the winxp drivers and the wireless card works GREAT. There's only one really weird issue that I have with it.

Assume that my computer is on and I'm connected to the wireless network just fine. I then reboot the system for whatever reason (maybe I install a kernel update or something). When the system comes back up the card does not detect ANY wireless networks. No matter how many reboots I do the card is useless. ndiswrapper is corretcly loaded and all that, but the card is just not functioning. However, if I completely shut down the system and turn off the power, then power it back on it works just fine! It seems like something is not "resetting" in the wireless card when the system reboots. The only way to get it to reset is by actually powering off the system.

Any ideas on what might be going on and how to fix this?

---

### Post by fontosaurus on 2008-09-14
Did you ever get an answer to this?  I'm experiencing the exact same thing.

---

### Post by lisati on 2008-09-14
You might have to arrange for your networking to be restarted when you reboot. One way of doing this is described [here]("http://ubuntuforums.org/showpost.php?p=1351902&postcount=2").

---

### Post by shaggy999 on 2008-09-17
Thanks! This worked!

---

