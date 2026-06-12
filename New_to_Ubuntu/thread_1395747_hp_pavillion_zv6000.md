---
title: "hp pavillion zv6000"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by yannos01 on 2010-02-01
HI

I got this old pc (hp pavillion zv 6000 is about 4 or 5 years old) on which I've installed ubuntu 9.10

everything seems fine appart for the wifi connexion that doesn't work.
interestingly, this comuter is fitted with a button to start using the wifi and this button doesn't work.

No one can be less knowledgeable about computer than I am but please help me because this starts to make me crazy.

I can't even say if my network card is switched on and how to do that

Thanks

---

### Post by skymera on 2010-02-01
Hello :)

Can you post the outputs of lsbusb and lspci please

---

### Post by howefield on 2010-02-01
Have you tried System > Administration > Hardware Drivers ?

You would need a wired connection, maybe you can hook an ethernet cable to the router then open a terminal (Applications > Accessories > Terminal) and type

```
sudo apt-get update
```

Enter your password when prompted, then try the above mentioned Hardware Drivers.

---

