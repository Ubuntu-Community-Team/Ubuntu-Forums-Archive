---
title: "Wireless doesn´t work anymore after upgrade - Acer Aspire 5040"
date: 2014-10-23
forum: Networking &amp; Wireless
---

### Post by willem5 on 2014-10-23
continuing from [http://ubuntuforums.org/showthread.php?t=2249370](http://ubuntuforums.org/showthread.php?t=2249370)

> **jeremy31 said:**
> Does ```
uname -a
``` still show a  3.2.0-70 kernel or does it show a 3.13.0- one?  If it still has 3.2.0  start a thread in Installation and Upgrades about the issue

```
uname -a
Linux laptop 3.2.0-70-generic #105-Ubuntu SMP Wed Sep 24 19:49:46 UTC 2014 i686 athlon i686 GNU/Linux
```

---

### Post by slickymaster on 2014-10-23
*Moved to the ***Networking & Wireless*** sub-forum*

willem5, please follow the "Wireless Script" link [here]("https://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script"), download and run the script as [per this instructions]("http://ubuntuforums.org/showthread.php?t=2224209&p=13024222&viewfull=1#post13024222"), and post back the report it generates.

---

### Post by kc1di on 2014-10-23
Hi willem5, 

It seems like your upgrade to 14.04 is not complete becuase the kernel image should now be 3.13.xx not 3.2 -- but the wireless should work anyway.

Go to Software & Updates >Additional Drivers tab -and see if it offers you a different driver- select the one it recomends and install that one again. 
reboot see if wireless works.

---

