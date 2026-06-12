---
title: "aircrack-ng problem"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by username5 on 2010-12-08
I Have a problem with patching and installing the proper driver for my wireless card because i dont know if my wireless card is compatible with aircrack-ng.
I am using a Dell Inspiron mini 10 (it was bought it in 2009 if it helps)
I installed aircrack with synaptic package manager pleas help

---

### Post by trikster_x on 2010-12-08
Have a look [HERE]("http://www.aircrack-ng.org/doku.php?id=compatibility_drivers").  That is the driver compatibility page for aircrack.  Just follow the instructions and you should be able to find your card if it is compatible.

If you have trouble figuring out what your wireless card is, try using the following command:

```
lspci -v|grep -C 5 -i "wireless"
```

This will show you your chipset and what drivers you are using for the chipset.

---

### Post by MacKennedy on 2010-12-08
You should spend some time with the Aircrack-ng website. There are a few tutorials and the documentation is quite extensive. Read it first, then read their forums. Everything you need is on their website. Also, Backtrack 4 latest release has quite a few patched drivers included and will run from dvd and flash drive.

---

### Post by username5 on 2010-12-10
> **trikster_x said:**
> Have a look [HERE]("http://www.aircrack-ng.org/doku.php?id=compatibility_drivers").  That is the driver compatibility page for aircrack.  Just follow the instructions and you should be able to find your card if it is compatible.

If you have trouble figuring out what your wireless card is, try using the following command:

```
lspci -v|grep -C 5 -i "wireless"
```This will show you your chipset and what drivers you are using for the chipset.

Thank you this has helped me allot .

---

