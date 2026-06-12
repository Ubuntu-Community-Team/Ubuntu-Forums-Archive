---
title: "[SOLVED] Wireless on Dell Vostro"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by jesuisbenjamin on 2008-10-09
hello there,

I newly bought a Dell Vostro 1510 and am trying to figure out how to enable wireless networking, right now i am connected via cable.

The help files are quite confusing. I cannot see any wireless network listed. 

Can someone teach me how to sort this out?

Thanks
B.

---

### Post by jago25_98 on 2008-10-30
You should say how you got it working. I know there's a script for the bcm**xx somewhere...

---

### Post by jesuisbenjamin on 2008-10-31
> **jago25_98 said:**
> You should say how you got it working. I know there's a script for the bcm**xx somewhere...

It was solved automatically as Ubuntu eventually updated itself with the adequate drivers.
So technically "i" didn't get it working :P

---

### Post by jago25_98 on 2008-10-31
Thanks, that could help some people who searched and found this thread.

Personally it hasn't helped me though:

```
j@IDPP-0644:~$ modprobe bcm43xx && lsmod |grep bcm && lspci|grep BCM43 && iwconfig
bcm43xx               127720  0
ieee80211softmac       30976  1 bcm43xx
ieee80211              35528  2 bcm43xx,ieee80211softmac
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.
```

---

### Post by jesuisbenjamin on 2008-10-31
If you can tell me how i can check which hardware i have and what driver is in use then maybe we could compare.

---

