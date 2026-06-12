---
title: "i know what i need... i just dunno where to get it!"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by amiacamal on 2009-07-08
i recently installed ubuntu on an acer aspire 6935g. i have no sound whatsoever. i tried multiple things to fix this wit the guidence of various forum users, to no avail. so i stumbled on this --> [http://www.linlap.com/wiki/acer+aspire+6935g](http://www.linlap.com/wiki/acer+aspire+6935g)

it says...Sound working install latest alsa-driver snapshot and set model=acer-aspire-8930g
my question is... where do i get that nd how do i install it? >_>

:guitar:  <--- just noticed this guy, \m/  ^_^  \m/

---

### Post by alexlafreniere on 2009-07-08
Alsa should be installed by default, that's how Ubuntu produces sound. I didn't think it also handled drivers.

---

### Post by amiacamal on 2009-07-08
at the min im trying what Kamaludu said on that page, 

"Finally I've added this lines at the end of: /etc/modprobe.d/alsa-base.conf" 

^ that part. any idea how i add the lines to that....thing?

---

### Post by amiacamal on 2009-07-08
anyone??

---

### Post by snowpine on 2009-07-08
From the Terminal:

```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by amiacamal on 2009-07-08
apparently i dont know what i need... that didnt help at all >_>

---

