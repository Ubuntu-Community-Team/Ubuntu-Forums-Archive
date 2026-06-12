---
title: "No wireless after update"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by yssida on 2008-05-15
Before I updated last night, my wireless was working fine, after an update I had difficulty connecting, and finally gave up. What should I do? My network adapter is an Intel PRO/Wireless 3945ABG, it has an open source driver.

Regards,
yssida

ADD: Actually, it wasn't fine, I couldn't connect to many public access areas (airports,etc), but it worked fine at home.

---

### Post by chili555 on 2008-05-15
There is evidently a better iwl3945 in here:```
sudo apt-get install linux-backports-modules-hardy-generic
```Please let us know.

---

### Post by yssida on 2008-05-15
I plugged in the ethernet wire and installed it. Removed the wire, and it worked.

I'll keep you posted. Thanks!

---

### Post by yssida on 2008-05-21
Hmmm, it didn't work again. Required me to change wireless security for my router to 'none'. And then set it again to WPA Personal, and reentered the password. I don't exactly know what the problem is either.

---

### Post by chili555 on 2008-05-21
This is a great tutorial on WPA: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by yssida on 2008-05-21
Does that let me connect to WPA network? Or is it for setting up WPA network?

Anyway, what if iwlist scan says

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```

---

