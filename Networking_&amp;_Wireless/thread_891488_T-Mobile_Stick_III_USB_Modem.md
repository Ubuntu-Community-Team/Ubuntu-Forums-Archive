---
title: "T-Mobile Stick III USB Modem"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by polardesign on 2008-08-16
I have just received my T-Mobile USB Modem.

It is the Latest Huawei Modem.

I have looked at many posts but still unable to get the USB Modem recognised and working.

Has anyone any ideas

---

### Post by Crafty Kisses on 2008-08-16
Post results of
```
lsusb
```
Also
```
lshw -C network
```

---

### Post by polardesign on 2008-08-16
Thanks

I can see the USB Modem by using the above commands...

But how do you get the modem working using UBUNTU?

---

### Post by GeorgeVita on 2008-08-16
Hi,
I own a similar modem (Huawei E170) and be connected with Ubuntu 8.04 just by modifying the wvdial.conf.
Check my post: forum.huawei.com/jive4/thread.jspa?threadID=322982
and post me here any question. You have to know your T-Mobile dial no, APN, default user name & password. The PIN have to be removed (or ask to add some more lines to wvdial.conf).
Regards,
George

---

