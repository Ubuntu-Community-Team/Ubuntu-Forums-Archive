---
title: "wi fi connection"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by sjbhu on 2010-05-27
hi
i have dell wlan 1501 wireless card
can u help me to access wi fi in my area
my laptop is not detecting wi fi in ubuntu

---

### Post by sadaruwan12 on 2010-05-27
> **sjbhu said:**
> hi
i have dell wlan 1501 wireless card
can u help me to access wi fi in my area
my laptop is not detecting wi fi in ubuntu

Need a little more details on your problem.

Is your wireless card get detected by the OS?


Run these commands,

```
lspci
lsusb
```

and post the out put here.

If the card is there does network manager list the available wireless networks in your area ?

Please reply with the answers.

---

### Post by Matt__ on 2010-05-27
It will be one of the broadcom wifi cards;
connect to wired internet and apt-get update, then check for hardware drivers.
you should find b43 and STA driver option...try the latter first.
reboot.

if this fails your next steps are:

try apt-get install b43-fwcutter
or apt-get reinstall bcmwl-kernel-source
or finally try ndiswrapper

there are numerous threads on these forums for any and all of these methods. good luck :)

---

