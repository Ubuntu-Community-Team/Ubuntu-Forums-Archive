---
title: "eth0 missing"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by Willye on 2010-08-18
Hey buddies, i had well installed the  eth0 card and it was working, but i don't know why when i run ifconfig only appears the conf for lo, the eth0 does not appear, the card is well connected, thanks for your help

---

### Post by dineshs on 2010-08-18
```
ifconfig -a
```

---

### Post by Iowan on 2010-08-18
**ifconfig -a** will:> display all interfaces which are currently available, even if down
**sudo lshw -C network** will probably tell you more than you really wanted to know. :)

---

### Post by Willye on 2010-08-20
hwinfo --netcard shows me the ethernet card, i run modprobe e100 and shows: FATAL module e100 not found, in /sys/class/net it does not appear the eth0 directory, 
how can i fix it ?

---

