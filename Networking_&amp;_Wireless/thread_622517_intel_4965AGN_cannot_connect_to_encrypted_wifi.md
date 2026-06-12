---
title: "intel 4965AGN cannot connect to encrypted wifi"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by nah40 on 2007-11-24
I have an HP dv6500t with the 4965AGN wireless, using Gutsy.
I can connect to public wireless but not private encrypted networks.
I have tried everything I can find in the forums. Nothing helps.
I have tried both wpa and wpa2.
Twice everything has been so fouled up that I reinstalled Gutsy.
This problem is the only thing keeping me on Windows Vista.

---

### Post by brennydoogles on 2007-11-24
> **nah40 said:**
> I have an HP dv6500t with the 4965AGN wireless, using Gutsy.
I can connect to public wireless but not private encrypted networks.
I have tried everything I can find in the forums. Nothing helps.
I have tried both wpa and wpa2.
Twice everything has been so fouled up that I reinstalled Gutsy.
This problem is the only thing keeping me on Windows Vista.

Have you tried any network managers other than the default? Maybe try Wicd ```
sudo aptitude install wicd
```

---

### Post by kevdog on 2007-11-25
I assume you have confirmed that this will work on windows.  It also is driver dependent.  What driver are you using

---

### Post by nah40 on 2007-11-25
tried wicd did not help.

---

### Post by nah40 on 2007-11-25
using the wext wpa supplicant driver.

---

