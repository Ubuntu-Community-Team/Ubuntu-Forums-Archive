---
title: "Installing Broadcom STA driver from live USB"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-07-26
Okay, I have a Dell Mini 10v and no wireless.  Ubuntu desktop is installed.  I do not have any access to a wired connection.  I inserted the live USB while I was already booted from my hard disk and went to pool>restricted>b>bcmwl.  When I double click on the bcmwl-kernal-source_5.60.48.36+bdcom-0ubuntu3_i386.deb Package Installed pops up, but I get an error message saying "Error: Dependency is not satisfiable: dkms"

What should I do to get my wireless working?

---

### Post by TriBlox6432 on 2010-07-26
Bump?

---

### Post by CoolJohnB on 2010-07-26
With my Dell I loaded the drivers by going to System>Administration>Hardware Drivers it was listed there and installed automatically.

Hope it works for you.

---

### Post by TriBlox6432 on 2010-07-26
Thanks, but that's only if you're connected to wired first.  I have no access to the internet on that device at all.

---

### Post by bkratz on 2010-07-26
> **TriBlox6432 said:**
> Thanks, but that's only if you're connected to wired first.  I have no access to the internet on that device at all.




See section 2.2 of the first half of this thread, perhaps it will help

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by JustinR on 2010-07-26
Hi,

You first need to install these packages from 'Pool > Main':

DKMS
Patch
Fakeroot

Then try to install the wireless driver.

If you created the Live USB through Ubuntu startup disk creator then this will not work - the Live USB uses a different directory structure.

If you actually went through the install process on the USB stick then is should go fine.

---

