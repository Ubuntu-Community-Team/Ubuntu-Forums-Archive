---
title: "IFCONFIG COMMAND not working?????"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by supermal on 2007-05-29
According to my boys book of unix I should be able to type 'ifconfig -a' at the terminal and be told the IP address of my local machine. Instead I get 'ifconfig command not found' as the result. I know it's me and something stupid, can someone put me out of my misery and point out my error.;)

---

### Post by taurus on 2007-05-29
Maybe /sbin is not in your path.

```
/sbin/ifconfig -a
```

---

### Post by supermal on 2007-05-29
correct answer, give yourself a medal. Thank you.:D

---

