---
title: "uninstall ubuntu"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by mohammedadel on 2011-04-08
I want to remove Ubuntu from my laptop but I have windows 7 too
what shall I do?
thanks

---

### Post by pmlxuser on 2011-04-08
1.reinstall windows boot loader (MBR) if you don't know how to do that advise you to get one who does.
2.delete ubuntu partition.
3.expand windows partition (using windows disk management tools)

---

### Post by madjr on 2011-04-08
> **mohammedadel said:**
> I want to remove Ubuntu from my laptop but I have windows 7 too
what shall I do?
thanks

did you find any particular problem with ubuntu ?

any area it should improve?

your feedback is appreciated. Thanks.

---

### Post by Mark Phelps on 2011-04-09
> **mohammedadel said:**
> I want to remove Ubuntu from my laptop but I have windows 7 too
what shall I do?
thanks

If your laptop has a CD or DVD drive, the FIRST thing you should do is use the Win7 Backup feature to create and burn a Win7 Repair CD.

Then, you can use the Disk Management utility in Win7 to remove the Ubuntu partition.

Finally, you boot from the Repair CD you made and run Startup Repair three times.  That will restore the Win7 MBR and get it booting again.

---

### Post by Rubi1200 on 2011-04-09
> **mohammedadel said:**
> I want to remove Ubuntu from my laptop but I have windows 7 too
what shall I do?
thanks
If you installed Ubuntu **inside** Windows with Wubi, this guide will explain how to uninstall it:
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

