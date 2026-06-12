---
title: "Terminal Codes"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by dstleanage on 2011-02-09
Hello,

Want to know what the code to get driver information in the Ubuntu terminal. 
Need to get driver details of my laptop.

---

### Post by P4man on 2011-02-09
ubuntu is not windows, you usually dont need any drivers that arent already included in the kernel.

If you have a problem with a device, please describe it, rather than applying your windows logic ;)

---

### Post by dstleanage on 2011-02-09
> **P4man said:**
> ubuntu is not windows, you usually dont need any drivers that arent already included in the kernel.

If you have a problem with a device, please describe it, rather than applying your windows logic ;)
I'm going to migrate from Windows to Linux.
So want to know Linux terminal codes.
Please give me the code.

"sudo............................"?

---

### Post by P4man on 2011-02-09
you are just applying windows logic to ubuntu. Basically all the drivers you need are part of the kernel, they arent stuff you need (or even CAN) download from the web (exceptions may be nvidia videodrivers, or in some cases, wifi drivers).

What is it you really want to know? If you want to know what hardware you have, you can run

```
lspci

``````
lsusb

```or 
```
sudo lshw
```

If you want to see what modules are loaded:

```
lsmod
```

But it wont give you a lot of useful info I think. What you want to do, is just boot ubuntu from CD and see if everything works or not before installing. If something isnt working, report back.

---

