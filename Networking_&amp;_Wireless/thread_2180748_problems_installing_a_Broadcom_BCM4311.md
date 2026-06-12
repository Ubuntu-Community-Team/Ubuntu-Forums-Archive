---
title: "problems installing a Broadcom BCM4311"
date: 2013-10-14
forum: Networking &amp; Wireless
---

### Post by 4dr14n on 2013-10-14
Hello everyone,
 I am quite nw using linux but not completely... some time ago, I used to have an Xubuntu OS, and already there I had problems with my wireless card, however, thanks to some of you guys, we managed to solve it and, finally, it worked.
Now, I have a similar problem with my lubuntu (I changed because Xubuntu seemed quite slow), I don't know how to install the drivers, but it should work once done. And, unfortunately, I don't find the original post where I asked it the first time.
I hope you can help me.
Thank you so much!

---

### Post by wildmanne39 on 2013-10-14
Please do:
```
sudo apt-get install linux-firmware-nonfree
```
Thanks

---

### Post by 4dr14n on 2013-10-14
Thank you, I dont copy waht it appears but it worked in some way, now I can see some networks but not all of them, actually, mine is one meter from the laptop and it doesn't appear, would you know why and/or how to solve it?
Thank you anyway!!

---

### Post by 4dr14n on 2013-10-14
False, it appear, some minutes later, but now it is, so, you can close the topic, thank you!!

---

### Post by zKhtdyX on 2013-10-31
> **4dr14n said:**
> False, it appear, some minutes later, but now it is, so, you can close the topic, thank you!!

There are some problems like this reported with the b43 driver and BCM4311. If you use 12.04lts(?) with the 3.8 quantal kernel you could try the 3.2 precise kernel and look if this issue remains or not.

---

