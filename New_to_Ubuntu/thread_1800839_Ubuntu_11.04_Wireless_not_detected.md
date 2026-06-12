---
title: "Ubuntu 11.04 Wireless not detected"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by swaroop.striker on 2011-07-09
i recenlty installed Ubuntu 11.04 in my laptop... HP Compaq nx7300... i hav a belkin router... i've 2 OS viz., windows XP and Ubuntu 11.04... in XP the wirelss detects and i am able to browse the web but in Ubuntu it doesnt detect at all as a result which i am unable to surf :( :( ... But wired connection works..... somebody please help me with this problem.....

Thanks in advance..

---

### Post by mrhhug on 2011-07-09
post output of ```
iwconfig
``` who made the wifi chip?

---

### Post by westie457 on 2011-07-09
In a terminal run ```
lspci
```
Copy and paste the result in quote marks. Amongst other things this will show the wireless card and chip number

---

