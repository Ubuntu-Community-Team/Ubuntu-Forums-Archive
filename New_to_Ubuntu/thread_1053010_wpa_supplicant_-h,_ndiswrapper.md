---
title: "wpa_supplicant -h, ndiswrapper"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by fairy._.queen on 2009-01-28
Hi all!
How can you add a driver to your wpa_supplicant -h list?
That is, if I type "wpa_supplicant -h" it says:
```
drivers:
  wext = Linux wireless extensions (generic)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)     
  wired = wpa_supplicant wired Ethernet driver

```

and I need wpa_supplicant to use ndiswrapper instead.
Can you help me? Thanks in advance! :D

---

### Post by Bachstelze on 2009-01-28
Try using wext.

---

### Post by fairy._.queen on 2009-01-28
Thanks for your reply! :-)
I'm currently using wext, but the problem is sometimes it connects and sometimes it doesn't. Restarting network or rebooting sometimes help and sometimes doesn't.

I guess the problem is wpa_supplicant is using the wrong driver. Can anybody tell how to add ndiswrapper to that list?

---

### Post by fairy._.queen on 2009-01-28
any hints?

---

