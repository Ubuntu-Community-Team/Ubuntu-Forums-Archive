---
title: "no networking while using live cd"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by mikepin on 2007-01-11
I started using the live cd to run ubuntu, everthing loads except the ehternet adapter does not start. ive tried admin configuaration wiht no luck. I have an intel ethernet on a dell PC

any suggestion

---

### Post by Paerez on 2007-01-11
open a terminal on the live cd (Applications->Accessories->Terminal)

and type in this:

```
$ sudo ifconfig
$ sudo iwconfig
```

and paste it here for me to see.

---

