---
title: "ATI Catalist 10.7"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by auroraa9420 on 2010-08-11
iv downloaded the ati catalyst 10.7 and im not shure about installing it

i have a sapphire 5830 card and iv been torturing my self with downloading a driver and installing it without a problem

i tried with installinga a linux vanila kernel and everytime i got a kernel panic...(look at some of my posts if you think you can help me with it)

---

### Post by clhsharky on 2010-08-11
auroraa9420

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Sharky

---

### Post by clhsharky on 2010-08-11
auroraa9420

Ubuntu driver installer and ATI installer are different and can conflict.
You need to remove and purge a fglrx install or even a failed install before reinstall. Incorrectly installed drivers will give you a kernel panic.
 Default Lucid kernel is mature and capable of using latest catalyst.

Clean and return to default before installing fglrx
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Sharky

---

