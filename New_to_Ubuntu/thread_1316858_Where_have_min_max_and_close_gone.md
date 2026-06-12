---
title: "Where have min max and close gone?"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-11-06
i had some toruble with UNR a minute ago, so i removed it, and now i cant find my min max and close icons on any of my windows....ive gone through the computer janito and that doesnt help.

can anyone tell me how i can recover it.

---

### Post by philinux on 2009-11-06
> **JamesParnell said:**
> i had some toruble with UNR a minute ago, so i removed it, and now i cant find my min max and close icons on any of my windows....ive gone through the computer janito and that doesnt help.

can anyone tell me how i can recover it.

What did you remove?

---

### Post by JamesParnell on 2009-11-06
the netbook launcher and everything attached to it...via package manager

---

### Post by samh785 on 2009-11-06
> **JamesParnell said:**
> i had some toruble with UNR a minute ago, so i removed it, and now i cant find my min max and close icons on any of my windows....ive gone through the computer janito and that doesnt help.

can anyone tell me how i can recover it.
```
sudo apt-get remove maximus
``` in the terminal. It'll ask you for your password, and you should enter it. When it's done removing the package, log out and back in again.

I had the same exact issue. You should still go into synaptic and remove the UNR packages, but I found that when you do that it doesn't get rid of the package that screws around with the Minimize, Maximize and Close buttons.

---

### Post by JamesParnell on 2009-11-06
thank you =]

---

### Post by samh785 on 2009-11-06
no problem :D

---

