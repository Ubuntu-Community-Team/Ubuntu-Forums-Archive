---
title: "slow wifi - Ubuntu 16.10"
date: 2017-03-18
forum: Networking &amp; Wireless
---

### Post by yassatoubab on 2017-03-18
Hi

I run Ubuntu 16.10 on a new ThinkPad. The internet works, but from the start is has been very slow. It takes a while to load pages and they often time out.

I am totally new to this. I've looked at a number of threads and tried proposed solutions, but without any success.

I've followed the steps described in the sticky.
The output can be found here: [http://paste.ubuntu.com/24200011/](http://paste.ubuntu.com/24200011/)

Can anyone tell me what the problem is and how I could try to fix it?

Thanx

---

### Post by praseodym on 2017-03-18
Hi,

change the encryption mode to WPA2-AES (CCMP) not mixed mode WPA/WPA2 in your router. Check the manual

Additionally you can try
```

sudo iwconfig wlp3s0 power off
```

---

### Post by yassatoubab on 2017-03-26
Changing the router settings worked. Thanks!

---

