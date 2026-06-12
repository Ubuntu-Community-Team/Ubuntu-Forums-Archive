---
title: "ASUS ExpressGate?"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-04-19
It's not strictly Ubuntu but it's kind of around that area:D

Basically is ExpressGate tied to my windows install? as that crashed and died and so I've copied everything over to my other install (L. Mint) and now I want to delete my windows partition but what I want to know is if it will stop me from booting Mint?

also can I remove ExpressGate from within Linux? if it's not removed when I delete windows?

If you can make any sense of that;) 

Thanks in advance!

---

### Post by cariboo on 2009-04-20
Expressgate is independant from your Windows installation it is loaded from a chip on the motherboard. You can disable Exoressgate in the BIOS.

Depending on how you have installed Ubuntu, you can delete your WIndows installation without affecting Ubuntu.

If you have installed Ubuntu inside Windows, using wubi, you will have to do a complete reinstall of Windows and Ubuntu.

Be aware that if you reinstall Windows, you will have to repair grub, as Windows will overwrite grub. to repair grub have a look at this [thread=224351]howto[/thread]

Jim

---

### Post by Paqman on 2009-04-20
> **cariboo907 said:**
> 
If you have installed Ubuntu inside Windows, using wubi, you will have to do a complete reinstall of Windows and Ubuntu.


Not necessarily. [LVPM]("http://lubi.sourceforge.net/lvpm.html") can migrate a Wubi-installed system to a dedicated partition.

---

### Post by kamitsukai on 2009-04-20
it's not a wubi install I have a partitions setup =]

Thanks!

---

