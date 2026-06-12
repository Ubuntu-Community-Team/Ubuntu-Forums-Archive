---
title: "aircrack-ng on dapper drake"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by cccc on 2006-09-17
hi

howto install **aircrack-ng** on dapper drake ?
where can I find the aircrack-ng repository for ubuntu ?

greetings
cccc

---

### Post by spd106 on 2006-09-18
I would recommend building it from source. Getting aircrack-ng isn't the hard part. Getting a card + driver that supports monitor mode is where you will find trouble.

If you really must have an ubuntu deb. Then you could always ask the backports team, since aircrack-ng 0.6-1 is in edgy and the only dependancy is libc6, I don't see it being too much of a problem. Ask in launchpad [https://launchpad.net/products/dapper-backports](https://launchpad.net/products/dapper-backports).

---

