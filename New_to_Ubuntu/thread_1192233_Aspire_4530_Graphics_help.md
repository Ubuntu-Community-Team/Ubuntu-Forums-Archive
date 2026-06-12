---
title: "Aspire 4530 Graphics help"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by pfeifferock on 2009-06-19
Hi I just installed Ubuntu the latest version on Acer Aspire 4530 laptop and the graphics were horrible like it could not scrole without it taking like ten mins to scroll. I assumed that i just needed to get an update online but then i got the update and it continues to act like it has no graphics card. Help what do i do?
-Matt

---

### Post by nandemonai on 2009-06-19
First thing to do would be to check System -> Administration -> Hardware Drivers and check to see if there are any 3rd party drivers that need to be installed.

Failing that, open up terminal and type:

```
lspci | grep VGA
```

That should tell us what video chipset you're using.

---

