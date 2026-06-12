---
title: "[SOLVED] wireless does not work on acer 2920"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by elliah on 2008-11-24
the wireless card is detected and it is an intel pro/wireless 3945ABG but i cannot get the wireless card to switch on. the button that activates wifi doesn't seem to have any function when i'm running any variant of ubuntu. 
however, my dell inspiron 1420 which has the same wireless card functions without a hitch.
can anyone help?

---

### Post by elliah on 2008-11-30
for anyone who happens to have the same problem, i solved it by installing the backports module...

sudo apt-get install linux-backports-modules-hardy-generic

---

### Post by dulbirakan on 2008-11-30
I used this same solution on intrepit, except I used the line below.

sudo apt-get install linux-backports-modules-intrepid-generic


Thank you

---

