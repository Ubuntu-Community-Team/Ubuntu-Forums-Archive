---
title: "Wireless not working - Ubuntu 14.04/12.04 LTS RTL8192EE"
date: 2014-10-30
forum: Networking &amp; Wireless
---

### Post by travisb2 on 2014-10-30
[http://askubuntu.com/questions/541697/wifi-not-working-ubuntu-12-04-14-04-lts-realtek-802-11d-rtl8192ee](http://askubuntu.com/questions/541697/wifi-not-working-ubuntu-12-04-14-04-lts-realtek-802-11d-rtl8192ee)

I've already made an askubuntu about this, but I haven't had any luck. I've made a list of the things I've looked into and tried there. Basically, Ubuntu isn't detecting any wireless networks, and I believe it is because it doesn't recognize the network adapter in my laptop. Is there any solution to this someone can point me to? Anything else I should do/try?

---

### Post by chili555 on 2014-10-30
Please let me see, from a terminal:```
lspci -nn | grep 0280
lsb_release -d
uname -r
```Your paste in askubuntu was unclear.

-----------------
Note to chili: [https://github.com/lwfinger/rtlwifi_new/tree/kernel_version](https://github.com/lwfinger/rtlwifi_new/tree/kernel_version)  <-- if 14.04 et seq

---

### Post by travisb2 on 2014-11-08
Hey, my apologies for taking so long to get back to you. Had a really busy last couple of weeks. Even with some guru help around the office, no one was able to fix this issue for 14.04. However, the new version, 14.10, now works and recognizes this driver, so I am satisfied with that.

I can try to get around to solving my own problem for 12.04/14.04 or following your advice at some point for future readers who may have this issue and want to stick to an LTS OS version, but I make no promises. :P

---

