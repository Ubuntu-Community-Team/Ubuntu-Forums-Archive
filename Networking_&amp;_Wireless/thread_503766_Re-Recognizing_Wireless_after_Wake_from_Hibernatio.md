---
title: "Re-Recognizing Wireless after Wake from Hibernation"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by mojohn on 2007-07-18
Hello. I just installed Feisty on my Dell Inspiron 1100 laptop. My wireless card uses Broadcom 43xx, which I have working using ndiswrapper. I previously ran Dapper on the same machine with the same wireless card.

Under Dapper, when I hibernated the laptop and awakened it, the wireless connection was recognized with no problem. However, when I hibernate Feisty and awaken it, the wireless connection isn't recognized. The only ways I have found to "awaken" the wireless  connection are to: 1) reboot the computer - which defeats the benefits of hibernating, and 2) run ifdown wlan0 followed by ifup wlan0. This works just fine and I'm OK with doing that each time, but I have a question for the list.

Can I add the ifdown and ifup commands to a script that will run each time I input my password when the dialog is presented upon awakening from hibernate? 

Thanks, Mojohn

---

