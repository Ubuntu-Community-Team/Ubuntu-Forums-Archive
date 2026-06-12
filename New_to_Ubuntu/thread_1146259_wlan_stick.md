---
title: "wlan stick"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by Bigjge on 2009-05-02
I need some sort of help.   I have looked all through info pages in ubuntu and linux.
I cannot find anywhere info on how to install a program or what program for a wlan stick 
(dongle).
There must be others who have a router and someone else is using a wlan stick to go online with same router.
Please soneone look into this.
I can find all to set-up lan cards or anything else but not a wlan stick.

---

### Post by cariboo on 2009-05-02
Depending on the chipset, your wireless device should be setup automagically. Could you open a Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

and paste the output in your in your next post.

---

### Post by Bigjge on 2009-05-02
Sorry the sudo command is not recognised.

---

