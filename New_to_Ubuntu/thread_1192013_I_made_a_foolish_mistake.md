---
title: "I made a foolish mistake"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-06-19
I edited My xorg file wrongly and i didnt take any back up and now I cant activate my graphic driver as it says "Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid." So what should i do

---

### Post by candtalan on 2009-06-19
try booting into the Recovery mode and I think ther is a simple menu which includes a choice to reconfigure graphics. (Try to fix X server)

---

### Post by blackxored on 2009-06-19
```

Xorg -configure

```

Test it. And then copy the generated config file to /etc/X11/xorg.conf

Sincerely.

---

### Post by bodhi.zazen on 2009-06-19
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.broken
```

And restart X

---

### Post by ravi_buz on 2009-06-19
> **bodhi.zazen said:**
> ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.broken
```

And restart X

THanks that corrected my display but still my refresh rate is at 50 but my monitors refresh rate is 60 how to change this

---

### Post by bodhi.zazen on 2009-06-19
what hardware are you running ? videocard ? monitor ?

---

### Post by ravi_buz on 2009-06-20
I have nvidia fx 5200 graphic card and have a acer x19w monitor

---

