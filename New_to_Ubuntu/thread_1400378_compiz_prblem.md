---
title: "compiz prblem"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by TroyStachnik on 2010-02-06
i tryed enabling desktop effects but i just get an error saying can't enable visual effects, what can i do to fix this problem? (BTW i'm using a packard-bell NEC with an ATI Rage II2 c graphics card.)

---

### Post by theozzlives on 2010-02-06
Your computer and graphics card most likely can't handle special effects. Try this [http://ubuntuforums.org/showthread.php?t=799070]("http://ubuntuforums.org/showthread.php?t=799070")

---

### Post by samantha_ on 2010-02-06
> **TroyStachnik said:**
> i tryed enabling desktop effects but i just get an error saying can't enable visual effects, what can i do to fix this problem? (BTW i'm using a packard-bell NEC with an ATI Rage II2 c graphics card.)

I dont know if your card actually has enough power to run compiz, but to enable compiz, you will need to install graphics drivers.
Your computer's graphics card is not supported by ATI anymore, but you can use the open-source drivers.

More info about them, and installation instructions at [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by coldfusion1313 on 2010-02-06
Have you installed 3rd party drivers, for ATI card?

---

### Post by mushwars on 2010-02-06
Have you tried installing the restricted ati driver? The xf86 ati driver doesnt have 3d aceleration with the current stable version of **Mesa, libDRM,** and **Xorg Server** not to mention that you also need the 2.6.32-r2 kernel which you have to build from source and the other 3 in bold from git.

Just use the non free driver. 

I have tried that xf86-ati-driver-9999 and it has weird rendering problems in games like doom3 things render upside down some times >_<

---

### Post by mushwars on 2010-02-06
`

---

