---
title: "HELP please find a driver"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by Leigen_Zero on 2008-10-13
Hi there, would do this myself but since the ndiswrapper wiki seems to have vanished into thin air and 'autondis' comes up with 'card not supported yet' I was wondering if you guys could help.

I have a buffalo wireless network card (model number: WLI2-CB-G54L) which doesn't work off the native linux drivers, and thus I require ndswrapper, however I formatted my laptop recently and I cannot remember which driver I used last time, also, as the wiki has vanished I can no longer find out which driver to use.

Could anyone please inform me of which one to use

thanks
Leigen_Zero

---

### Post by Leigen_Zero on 2008-11-18
bump

---

### Post by Ayuthia on 2008-11-18
Can you go into the Terminal and post the results of:
```
lspci -nn
```It will help identify which chipset you have and that might help others find what driver you need.

---

