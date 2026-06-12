---
title: "dual boot root size"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by spiky001 on 2009-09-23
Hi havin been readin the forums i hav a Q i dual booted xp & ubuntu9.04 made 20 gig windows 15gig ubuntu 5 gig spare drive between both systems
when loadin ubuntu it asked for space for boot just guessed at 5 of the 15 gig leavin 10gig swap did i nead as much as 5 gig for boot? hope this makes sence

---

### Post by ken22 on 2009-09-23
I would say 100-512MB would have been more than enough for a /boot if you're going to have a few kernels about. 100Mb should be sufficient for the average user. 256Mb would be plenty.

Did you say 10Gb swap?

---

### Post by spiky001 on 2009-09-23
thks ken

---

### Post by ken22 on 2009-09-23
Swap works as so [https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

Rule of thumb. Swap size == Double your amount of ram.

---

