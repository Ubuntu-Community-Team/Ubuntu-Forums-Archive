---
title: "Screen random freezes"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by Maxiejoe on 2011-03-05
I have searched the Q and A ,  turned off screen saver and set sleep to never, also used compressed air to clean the cpu to try and solve the random screen freezes.  I have used Ubuntu for about 4 months and it has been perfect until now. will never go back to Microsoft.   I was using XP and the  problem started on XP so I installed another 250 g HD I had with Ubuntu 10.04 and kept the other HD installed also.  Am only using about 10% of the HD an both.  I have removed the HD with the XP but the problem still exists. I wonder why the problem went away and then came back on Ubuntu?  

It must be a hardware problem but I do not know how to find it and would appreciate help.  The freezes are random except I can watch movies for hours with no problem ??  

The system freezes and after about 15-20 seconds it re-boots itself.

Using Intel P-4 2.4 GHZ cpu,  1 gig, ram, 250 gig (2) Hard Drives, PM800-m2 mother board and Logtech wireless Keyboard and mouse, with VIA  and Phoneix tech 

Thanks for any help.

---

### Post by sanderd17 on 2011-03-05
could it be that your computer runs too hot?

To check the temperature, run
```

sensors

```

I think it is installed by default

my output is
```

acpitz-virtual-0
Adapter: Virtual device
temp1:       +49.0°C  (crit = +95.0°C)   

```
for reference.

If that is your problem, check that your fan works and clean your cooling metals.

Reason why I think this:
Windows uses more CPU than linux => becomes hot faster
When time goes by, the cooling metals work less eficient, so it could become a problem with ubuntu too.

---

### Post by Maxiejoe on 2011-03-05
Here is the data,  What is the acceptable range?

acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +75.0°C)

---

### Post by sanderd17 on 2011-03-06
That's acceptable, but I don't have any inspiration of what the problem can be.

I hope someone else has a good idea.

---

### Post by Dutch70 on 2011-03-06
This may be irrelevant, but do you use compiz, and what video card do you have?

---

### Post by Maxiejoe on 2011-03-06
I don't use compiz , the soundcard is VIA 8237 ,   and a Realtek ALC655 chip  This is a reall stumper.

---

### Post by Maxiejoe on 2011-04-23
Problem solved,  The problem was with my motherbord,  I found a new on online and installed it five days ago and everything has been running  good without random shut downs at this time.  I do have another problem that I will post on a new thread that has come up since .

---

