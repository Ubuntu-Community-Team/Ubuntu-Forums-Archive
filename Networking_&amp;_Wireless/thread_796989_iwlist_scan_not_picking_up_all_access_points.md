---
title: "iwlist scan not picking up all access points"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by anontrol on 2008-05-16
"iwlist scan" produces a list of three or four access points; however, when I crank up kismet / airodump-ng, I see about 10.

Is there any particular reason why "iwlist scan" might produce a truncated list of available access points?

---

### Post by rlcomstock3 on 2008-05-16
It is possible that the iwlist is showing the access point that it could connect to, as with a low enough signal an access point can be detected, but a connection can not be maintained.  I don't know that is the case, but that would be my initial thought.

---

### Post by vyruss on 2008-05-16
> **anontrol said:**
> "iwlist scan" produces a list of three or four access points; however, when I crank up kismet / airodump-ng, I see about 10.

Is there any particular reason why "iwlist scan" might produce a truncated list of available access points?

Maybe some of them are hidden and really not meant for you to access. However if you're knowledgeable enough to use kismet and airodump, you really should be able to figure this out on your own :)

---

