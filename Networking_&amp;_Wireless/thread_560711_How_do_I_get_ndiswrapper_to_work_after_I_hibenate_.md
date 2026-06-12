---
title: "How do I get ndiswrapper to work after I hibenate or suspend?"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by krazy1912 on 2007-09-26
Whenever I return from hibernation or suspend my wireless doesn't seem to work.

Any suggestions?

---

### Post by jimmydugs on 2007-09-29
If you know the driver that is being used by the kernel, try adding it to the /etc/default/acpi-support file under MODULES=.  It says that network cards and such are automatically unloaded/loaded, but this seemed to work for me.  

I'm not too sure what is the best way to determine your driver name if you don't know that...  I'm a bit new at this and just googled my wireless card (Intel Pro Wireless 3945 = ipw3945).  You can run 'lshw' and look for your wireless device and under its configuration section, there will be a 'driver=drivername'.  Not sure if that is the BEST way.  Anyway, that drivername is what you want to put in the acpi-support file.

---

