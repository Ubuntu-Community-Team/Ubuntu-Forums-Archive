---
title: "Dell laptop - always need to restart wlan0"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by rickbeton on 2008-09-25
Hi

I installed Ubuntu Hardy on my new Dell M1350.  The wireless works fine in every respect except one: every time I boot up, the wireless doesn't come up.  If I do

sudo ifdown wlan0
sudo ifup wlan0

then it's fixed and will work fine until next shut down.

I can also fix it by opening the 'Network' control panel, unlocking, then in the wireless properties I re-enter the WPA password. This has the same effect as the above, i.e. it gets the wireless working again.

How can I fix it permanently so that it works automatically soon as the laptop boots up?

Rick

---

