---
title: "bluetooth problem"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by constantine_77 on 2011-08-15
hi,

i am new in this forum. i have a toshiba nb305 net book and have installed ubuntu 11.04. WiFi, screen brightness works just fine. but the problem is with bluetooth. it shows the bluetooth icon on the panel but bluetooth remains turned off. please help me solve this problem.

regards,

constantine:D

---

### Post by LowSky on 2011-08-15
open a terminal
```
sudo service bluetooth restart
```

---

### Post by pierreyy on 2011-08-15
> **constantine_77 said:**
> hi,

i am new in this forum. i have a toshiba nb305 net book and have installed ubuntu 11.04. WiFi, screen brightness works just fine. but the problem is with bluetooth. it shows the bluetooth icon on the panel but bluetooth remains turned off. please help me solve this problem.

regards,

constantine:D

 try this,
  >  sudo service bluetooth start 

 if it doesnt work... try a bluetooth manager (blueman or smthn) maybe itll work

---

### Post by constantine_77 on 2011-08-15
Hi LOW SKY,

Your solution worked like a charm. Thank you very much.

Also many thanks to PIERRY for the suggestion.


Kind regards,

Constantine_77:guitar:

---

### Post by pierreyy on 2011-08-16
no problem...
 please mark as solved

---

