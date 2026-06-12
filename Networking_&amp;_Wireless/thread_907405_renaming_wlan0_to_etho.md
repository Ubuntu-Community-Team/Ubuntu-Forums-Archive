---
title: "renaming wlan0 to etho"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by grindbox on 2008-09-01
I need to rename serveral wireless cards from wlanx to ethx. can someone point me to what I need to edit?

---

### Post by pytheas22 on 2008-09-01
I think it's the wireless driver that decides what the device should be named, so you'd probably need to edit the source files and recompile the driver.

But I'm wondering why you want to do this, as you may be trying to make something more difficult than it needs to be.  Please let us know what your objective is; maybe we can make other suggestions.

---

### Post by grindbox on 2008-09-02
Well I solved my problem. needed to edit "/etc/udev/rules.d/70-persistent-net.rules"  after your in there is pretty much self explanatory. The purpose for the edit is because I am binding my wireless cards for use of round robin, and bind does not like wlan.

---

