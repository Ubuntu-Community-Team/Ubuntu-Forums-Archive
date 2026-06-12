---
title: "Internet Lost??? n00b question"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by bamboojj on 2009-01-20
Hey everyone,

I am facing this problem whereby my computer loses its wireless capability after performing a sleep. (This means that after I suspended or slept my computer and when I turn it back on, the wireless card **cannot detect any wireless channels/source around me** (but I am 100% sure there are at least 10+ around me)

How should I go about fixing this? BTW I am using Asus EEE PC, HA1000
```

uname -a
Linux jojoju-laptop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

```

I am using madwifi btw

---

### Post by disappearedng on 2009-01-20
bump

---

### Post by bgerlich on 2009-01-20
try "sudo ifconfig ath0 up"

---

