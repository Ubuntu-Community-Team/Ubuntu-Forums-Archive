---
title: "How can I tick restricted driver from &quot;not in use&quot; to &quot;in use&quot;"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by Pfau on 2007-09-08
My intel 3945 is in restrict driver "not in use"  (see picture). I can only be enable it but I cannot make it "in use"(when untick and then tick, the system told me to restart but after restart, it is in "not in use" again. What can I do ? , Thanks a million!!!

---

### Post by kvonb on 2007-09-08
It might be using an alternative driver which is stuffing things up (I'm no expert!).

Search the forum for a thread on the Intel 3945, you might get lucky :).

Sorry I can't be of more help.

---

### Post by spd106 on 2007-09-08
It looks like the nic has been disabled some how. Do you have a hardware switch or perhaps a fn+key combination to turn the wireless on/off?

---

### Post by Pfau on 2007-09-08
Um... I think I'm not disable all wireless function key. First it is still "in use" (but cannot connect and cannot see it in network list) after that, I try to install driver from previous intel 3945 thread and....I don't know , once i open restrict driver, it appeared to be "not in use". (T_T) I don't know what to do because I'm really new in ubuntu. Thanks !!!

---

### Post by spd106 on 2007-09-08
Can you please attached the full output of the following commands?
```
sudo lshw -class network
lspci
```

You seems to have a lot of ipw3945 archives on your desktop, did the default driver included in 7.04 not work?

---

### Post by Pfau on 2007-09-08
it turns "in use" after i reinstall some package ^^". But..... I cannot use my wireless (from picture). Any suggestion , Thanks!!!

---

