---
title: "dell latitude d630 wifi issue"
date: 2015-03-11
forum: Networking &amp; Wireless
---

### Post by tru3 on 2015-03-11
just installed ubuntu to my dell latitude d630 and i can not get the wifi to work. wont even show up. any help?

---

### Post by QIII on 2015-03-11
Hello!

Please follow the instructions in post #2 [here]("http://ubuntuforums.org/showthread.php?t=2082305") so that others will have the information to help.

Someone will be along shortly, no double.

---

### Post by tru3 on 2015-03-11
here is what it came up with. ignore last post.

---

### Post by jeremy31 on 2015-03-11
Your wifi doesn't like the driver you installed so, in terminal enter
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-*
```
```
sudo apt-get install firmware-b43-installer
```

Reboot and let us know the results

---

### Post by tru3 on 2015-03-11
> **jeremy31 said:**
> Your wifi doesn't like the driver you installed so, in terminal enter
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-*
```
```
sudo apt-get install firmware-b43-installer
```

Reboot and let us know the results

thank you! that worked.

---

