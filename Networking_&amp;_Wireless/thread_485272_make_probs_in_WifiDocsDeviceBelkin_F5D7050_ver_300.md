---
title: "make probs in WifiDocs/Device/Belkin F5D7050 ver 3000 (Ralink rt73 driver)"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by Gran3D on 2007-06-26
I (newbie) am carefully following the directions in WifiDocs/Device/Belkin F5D7050 ver 3000 (Ralink rt73 driver).  When I get to the "make" section the error message says it can't find a rule for modules.  I am not sure what the "rule" might be.  Have mucked about for some time, but I am really stuck.  FrodoB maight have an answer, although his turorial was writen for Edgy and I have Dapper.  His tutorial might expect more experience than I have also.

---

### Post by Gran3D on 2007-06-26
To add information, the line in Makefile which is 

make -C /lib/modules/2.6.15-28-386/build modules

Generates this error
make[1]: Entering directory `/lib/modules/2.6.15-28-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-28-386/build'
make: *** [all] Error 2

Is "modules" supposed to be a directory or a list or ??

Prior to this, I installed the W2K drivers using the ndiswrapper method twice, but it doesn't join a net with WEP protection.  Guess I must get the linux driver working.

TIA, Larry

---

