---
title: "Need to restart network on boot"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by neutrino15 on 2008-05-29
Hello,

I recently installed a wireless g card in an ubuntu tower using ndiswrapper and the original windows driver. Whenever i restart my system, however, the configuration does not hold. I need to go

```
$ sudo /etc/init.d/networking restart
```

every time I boot. Why is this and how can I remedy it?

---

### Post by bluefrog on 2008-05-29
has ndiswrapper been written in /etc/modules ?

---

