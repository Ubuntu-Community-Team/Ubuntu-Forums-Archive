---
title: "WPA disconnecting"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by chrisbain88 on 2007-07-25
Hi All,
I have WPA set up on my router and my laptop keeps disconnecting and reconnecting.
this never occured before applying WPA and it does not happen on the other unsecure wireless network that i access, is there a way to fix this?
By the way i am running Ubuntu 7.04
Cheers
Chris

---

### Post by ugm6hr on 2007-07-25
This is a known issue with Network Manager and madwifi (Atheros chipset) driver.  Apparently some Intel chipset users also have the same problem.  There is a report about it in Launchpad somewhere - sorry, I seem to have lost the link.

You can check which driver your wifi uses with
```
lshw -C network
```

If it says *driver=ath_pci*, then this is definitely the case with your computer.  If not, it still might be.

Solution: use Wicd instead.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by chrisbain88 on 2007-07-26
Cheers mate,
I have installed it and i will see if the problem occurs again and report back in a couple of days, so far so good
Thanks
Chris

---

