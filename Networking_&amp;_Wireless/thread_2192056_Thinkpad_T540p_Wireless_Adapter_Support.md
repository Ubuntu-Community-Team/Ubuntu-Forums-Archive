---
title: "Thinkpad T540p Wireless Adapter Support"
date: 2013-12-05
forum: Networking &amp; Wireless
---

### Post by snietfeld on 2013-12-05
Wireless adapter isn't showing up (just *eth0* and *lo* when running *ifconfig -a*).
Running fresh install of Ubuntu 12.04.3.

Wireless adapter listed as "*ThinkPad Wireless 2 x 2 BGN with Bluetooth*" on Lenovo website.

Result of running *lspci -nn | grep 0280*:
    [I]04:00.0 Network controller [-0280]: Realtek Semiconductor Co., Ltd. Device [10ec:818b]
[/I]
Reading online it sounds like Linux support for Realtek devices is poor. 
Tried installing the r8168 drivers from [here]("http://code.google.com/p/r8168/"), but no luck (adapter still doesn't show up after running *ifconfig -a*). 
Found a [similar thread for the Thinkpad 440p]("http://askubuntu.com/questions/376732/thinkpad-t440p-wireless-network-controller"), which indicates that no drivers exist yet and lead to this [Ubuntu bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1239578"), which is tagged as incomplete.

Is there anything else I can try, or should I send it back and get one of the other wireless adapters (listed below)?
 - [COLOR=#555555][FONT=Arial]Intel Single Band Wireless 7260BN with Bluetooth 4.0
 - I[/FONT][/COLOR][COLOR=#555555][FONT=Arial]ntel Dual Band Wireless 7260AC with Bluetooth 4.0[/FONT][/COLOR]

---

### Post by chili555 on 2013-12-05
I'm fairly confident that the 7260 devices will work in 13.10 and can be made to work in earlier versions: [http://askubuntu.com/questions/322511/no-wireless-with-intel-centrino-advanced-n-7260](http://askubuntu.com/questions/322511/no-wireless-with-intel-centrino-advanced-n-7260)

---

