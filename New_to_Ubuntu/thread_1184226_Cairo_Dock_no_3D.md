---
title: "Cairo Dock no 3D"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by cjv8888 on 2009-06-10
I re-installed 8.04 with a clean install of the / partition.
I used dpkg --set-selections < installed-software to reinstall the packages.
Everything is working but I lost the 3D view of the Cairo Dock which was ok before.
Now if I go to configuration/view, there is only 2D available.

Is there any easy way to re-enable 3D or should I do a removal/purge of the dock and re-install either from the repository or .deb from the website?  I understand that the .deb from the website has newer versions.

---

### Post by 4Orbs on 2009-06-10
Did you enable the driver for your graphics card in Hardware Drivers Mgr?

---

### Post by cjv8888 on 2009-06-10
> **4Orbs said:**
> Did you enable the driver for your graphics card in Hardware Drivers Mgr?

AFAIK there is no proprietary hardware driver.  There is just the onboard video card which works on install.  Compiz and extra effects are all working.

---

### Post by 4Orbs on 2009-06-10
Did you turn off the fake transparency in the Cairo-Dock configuration? It's under the cairo-dock System settings in advanced mode.

---

### Post by cjv8888 on 2009-06-10
Thanks
I will try that when I get home this evening.

---

### Post by cjv8888 on 2009-06-11
> **4Orbs said:**
> Did you turn off the fake transparency in the Cairo-Dock configuration? It's under the cairo-dock System settings in advanced mode.

No, fake transparency was not turned on.  The dock is still in 2D whether it is on or off.
Thanks.

---

