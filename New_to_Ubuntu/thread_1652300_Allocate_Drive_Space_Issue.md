---
title: "Allocate Drive Space Issue"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by johnacornett on 2010-12-24
Okay guys, heres whats up.

I already have OSX on my Mac and I'm trying to install Ubuntu along side my Snow Leopard. When it gets to the "Allocate Drive Space" screen in the install, my only options are to "Erase and use entire disk" and "Specify partitions manually."

How can I get my install to install alongside another operating system?

---

### Post by ajgreeny on 2010-12-24
Choose the "Specify partitions manually" and you can edit the current partition(s) by shrinking it, and then make new ones in the space made available.

It would help to know what partitions you already have, so if possible let's see a screenshot from gparted on the live CD, showing your current setup.

---

### Post by Quackers on 2010-12-24
Does Gparted recognise GUID partition table?

---

### Post by ajgreeny on 2010-12-24
> **Quackers said:**
> Does Gparted recognise GUID partition table?
Ah!  A very good question.

I forgot about the differences between macs and other machines!

---

### Post by Quackers on 2010-12-24
I can't remember what to do :-) There's definitely a way to do it!

---

### Post by johnacornett on 2010-12-26
Okay so do I run Gparted on the same CD as Ubuntu or is it on a completely different boot CD?

---

### Post by johnacornett on 2010-12-26
Is there a guide that I could print off or read from a different computer for a step-by-step specify partitions manually?

Preferably for Mac and 10.10.

---

### Post by candtalan on 2010-12-26
> **johnacornett said:**
> Okay so do I run Gparted on the same CD as Ubuntu or is it on a completely different boot CD?

The Ubuntu live CD includes gparted in the live session 
Menu
System>administration>gparted partition editor

---

