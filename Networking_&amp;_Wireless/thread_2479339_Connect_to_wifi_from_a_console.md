---
title: "Connect to wifi from a console"
date: 2022-09-21
forum: Networking &amp; Wireless
---

### Post by hornetster on 2022-09-21
This should be simple, but after hours of looking, still cannot figure it out...
How Can I connect Ubuntu to a known wifi network, with a valid adaptor attached, from a basic console (ie login in text mode.)
Can use ifconfig/ip/iwconfig or whatever. Will they do it??
Examples please!!

---

### Post by chili555 on 2022-09-22
Is Network Manager installed? If so:

```
nmcli device wifi connect mylilrouter password qqqspy12345
```

---

### Post by &amp;KyT$0P# on 2022-09-22
You can also do it interactively with
```
nmtui
```

---

