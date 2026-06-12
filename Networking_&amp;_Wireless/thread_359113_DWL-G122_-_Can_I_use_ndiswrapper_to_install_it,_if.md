---
title: "DWL-G122 - Can I use ndiswrapper to install it, if so, what files do I need?"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by Condoulo on 2007-02-11
It would help big time. :) I know how to use ndiswrapper actually, I just don't know what files for that driver have been tested with ndiswrapper or not. So please help. :)

I got it to work. :)

---

### Post by Floppyjoe on 2007-02-11
> **Condoulo said:**
> It would help big time. :) I know how to use ndiswrapper actually, I just don't know what files for that driver have been tested with ndiswrapper or not. So please help. :)

I have a DWL-G122 Ver A1 that works with Ndiswrapper and the windows drivers that come with this unit.

I also have a DWL-G122 Ver C1 that works out of the box with a native driver.

For the other versions of DWL-G122 I could not tell you what works.

---

### Post by Condoulo on 2007-02-11
I have a DWL-G122 Rev B.

---

### Post by Floppyjoe on 2007-02-11
> **Condoulo said:**
> I have a DWL-G122 Rev B.
Do you have the driver CD that came with it?
If there are files on there that are called driver.inf and driver.sys and possibly a driver.bin file you probably could use those with ndiswrapper.

I use the term driver.inf here but it will say something different than driver.inf but it will be a .inf and a .sys and a possible .bin file.

---

### Post by Condoulo on 2007-02-11
Well I downloaded the drivers from the site, and now it works. But thanks for your help. :)

---

### Post by changcheng on 2007-02-11
You can find it in [Ndiswrapper's WIKI]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D"). If you got a .exe file for your windows driver then that will be a little bad luck. I got a ver.C1, and I installed the driver from source code, that works perfect.

---

