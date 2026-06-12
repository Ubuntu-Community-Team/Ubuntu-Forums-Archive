---
title: "Clock incorrect"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by S0m3th1ngw13rd on 2009-01-30
Here is a new one for me  

Dual Boot Ubuntu 8.10 and Win xp
the time is correct when I'm in linux but if I restart and boot windows the clock is always wrong. Don't think its battery on mainboard because Linux clock is coorect when I boot linux

---

### Post by perlluver on 2009-01-30
> **S0m3th1ngw13rd said:**
> Here is a new one for me  

Dual Boot Ubuntu 8.10 and Win xp
the time is correct when I'm in linux but if I restart and boot windows the clock is always wrong. Don't think its battery on mainboard because Linux clock is coorect when I boot linux

That is most likely because Linux is using UTC.  Windows doesn't recognize UTC only localtime.  Not sure how to fix it.

Edit: A solution here, hope it helps: [http://miknight.blogspot.com/2006/06/storing-system-time-in-utc-in-windows.html](http://miknight.blogspot.com/2006/06/storing-system-time-in-utc-in-windows.html)

---

### Post by S0m3th1ngw13rd on 2009-01-31
Following the link provided a workable solution. Thank You

---

### Post by 73ckn797 on 2009-01-31
I see that you have resolved the situation but I was having similar problems and found setting the clock in BIOS fixed things. The BIOS clock was incorrect and Windows XP always had incorrect time after starting up.

---

