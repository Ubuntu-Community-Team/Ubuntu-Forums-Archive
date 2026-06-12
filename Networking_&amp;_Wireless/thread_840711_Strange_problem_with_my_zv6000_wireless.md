---
title: "Strange problem with my zv6000 wireless"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by pdusen on 2008-06-25
I am having an odd problem here. This is a fresh install of Hardy on my HP zv6000. After I installed and fully updated, I ran the restricted driver manager to install the graphics and wireless adapter drivers (which I believe uses bcm-fwcutter).

This works on every network I have been on... except, for some reason, my University wireless network. When i first turn the machine on, the wireless signal connects fine. However, the signal strength slowly goes down, and once it gets to 50% after about 20 minutes I lose internet traffic altogether.

As far as I can tell, the university uses no encryption, it only does MAC address filtering.

Does anyone have any suggestions?

---

### Post by pdusen on 2008-06-25
anybody?

---

### Post by Ayuthia on 2008-06-25
Can you post your lshw -C network?  You might also try installing ndiswrapper.  Sometimes that produces better results.

---

