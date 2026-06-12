---
title: "How do I install Belkin Enhanced Wireless USB Adapter."
date: 2015-02-13
forum: Networking &amp; Wireless
---

### Post by adam120 on 2015-02-13
Hi,

I have a Belkin Enhanced Wireless Adapter (N150, F6D4050, ver.1001ed) and I'm wondering how I use/install it on Ubuntu 14.04.1?

Thanks.

---

### Post by Bucky Ball on 2015-02-13
Welcome. Perhaps open a terminal and give us the output of:

```
sudo lshw -C network
```

We can see what driver, if any, it is currently using. ;)

---

### Post by adam120 on 2015-02-13
I plugged a USB stick in so that I could copy the output of that, and it started working. I wasn't sure why but then I realised that the USB stick was pushing the adapter backwards a bit. When I unplugged the USB stick it stopped working again, so I tried the adapter in a different USB port. It turns out that the USB port that I had been using it in was just faulty, and it works now! Thanks for the help though! :D

---

### Post by Bucky Ball on 2015-02-13
Excellent news! Please mark thread as solved. See second link in my sig. Good luck. Enjoy the OS, the forums and the learning curve. ;)

---

