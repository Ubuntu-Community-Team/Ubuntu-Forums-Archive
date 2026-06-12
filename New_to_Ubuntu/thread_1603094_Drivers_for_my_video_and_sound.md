---
title: "Drivers for my video and sound?"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by rrp85 on 2010-10-22
how do i go about getting my radeon 4800 series gfx card drivers and along with my onboard sound through 10.10?

---

### Post by migs73 on 2010-10-22
Open a terminal (Applications > Accessories > Terminal) and type in;
```
lspci
```

that is lower case LSPCI. This will let us see what Ubuntu sees on your PCI bus.

---

### Post by rrp85 on 2010-10-22
thank you very much i appreciate it.:popcorn:

---

### Post by 3rdalbum on 2010-10-22
> **rrp85 said:**
> how do i go about getting my radeon 4800 series gfx card drivers and along with my onboard sound through 10.10?

There are two drivers for that card; the open-source driver ("ati") and the "binary blob" official ATI closed-source driver ("fglrx").

By default, your card will use the open-source driver. This driver is very limited, but if your card is doing everything you want it to do, then stick with it. If you want more (such as 3D acceleration), then go to System > Administration > Additional Drivers and you will be offered the fglrx driver, which is made by ATI.

---

### Post by migs73 on 2010-10-22
Sorry, I should have asked you to post the results back here so we can have a look at what hardware you have.
Is it working now??
If so the code I gave you had nothing to do with it!!!!

---

