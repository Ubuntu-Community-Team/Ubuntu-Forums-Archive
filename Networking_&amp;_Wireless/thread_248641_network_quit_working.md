---
title: "network quit working"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by Subnet on 2006-09-01
I reinstalled dapper yesterday and the network connection isn't working when it did before. Dapper detects my network card, but just says that it is disconnected. I have also tried deactivating and activitating the card serveral times and it still doesn't work. Any thoughts or suggestions?

---

### Post by absolutenewbie on 2006-09-01
I'm having the same problem, so any help would be greatly appreciated

---

### Post by Uluen on 2006-09-01
What's the output of

```
$ dmesg | grep eth
``` and ```
$ cat /etc/network/interfaces
```?

---

