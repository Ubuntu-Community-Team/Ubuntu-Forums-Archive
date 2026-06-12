---
title: "PC to Linux networking problem"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by lobotheduck on 2007-03-27
Hi

I'm using xubuntu on a g3mac and im trying to connect to a windows pc using a crossover connection

I'm using the following IP setup:

**xubuntu**
**ip address:** 169.254.66.145
**subnet mask:** 255.255.0.0
**gateway address:** 169.254.66.144

**windows**
**ip address:** 169.254.66.144
**subnet mask:** 255.255.0.0
**gateway address:**

regards

Lobo the Duck

---

### Post by lobotheduck on 2007-03-27
*edit* sorry i didnt mention the state of my problem

when i connect them together i get limited or no connectivity.  does anyone have any advice?

regards

Lobo the Duck

---

### Post by Mr. C. on 2007-03-27
> **lobotheduck said:**
>  ... limited or no connectivity.

Define this.

Can machine ping each other ?

On Ubuntu, what is the output of :
```
ifconfig -a
route -n
```

On Windows, what is the output of:
```
ipconfig /all
route print
```

MrC

---

