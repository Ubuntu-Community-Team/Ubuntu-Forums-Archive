---
title: "Some questions for newbies"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by shearer_007 on 2009-01-01
Hi, yet another question from me. Sorry for bugging, as im really very new to linux and to top that up...my computer skills are limited.

1. I have quite a number of CDs for hardware installation (stuffs like dvd-rom, graphics card)

Should i just install it?

2. I understand ubuntu offers open office. But can i install Microsoft Office as well? Is it compatible? (I have wine up running)

3. Any engineers around here? Will Solidworks, autocad, Computational fluid dynamics softwares work in ubuntu?

Thanks for the help in advance. Cheers.

Happy New Year 2009
Jingwei

---

### Post by cheesypoof on 2009-01-01
Visit [http://appdb.winehq.org/](http://appdb.winehq.org/) and search for the respective applications. It should tell you how to install, as well as if there are any limitations. Those CDs are most likely only going to have Windows drivers. All your hardware should be supported already.

---

### Post by Delever on 2009-01-01
AutoCAD won't work. I run it inside Windows *virtual machine*. That means it works only on Windows.

---

### Post by azr on 2009-01-01
1) It is most likely that these are the windows drivers for your hardware aao cannot be used. Ubuntu provides many linux drivers that make your hardware work; though if not, you will have to find/download linux drivers for them.

2) You can run ms word through wine. Though I don't think it is necessary at all. (I believe Open Office has mostly equivalent functionality)

3) Try running those through wine, or investigating equivalent linux software.

---

### Post by soxs on 2009-01-01
#1: The driver cds you have are only windows drivers. Linux drivers for your mainboard are allready included in the kernel or it won't install at all. Graphics drivers need to be downloaded from yor GPU vendors home page (except intel, which offers opensource support and thus is allready compiled into the kernel).
Installation of those proprietary drivers is highly sensitive of what you do, in which order and what options you activate/deactivate, but this changes from release to release. Just say, be carefull...

---

### Post by Delever on 2009-01-01
First, make sure 3D graphics don't work, THEN install drivers.

Going to vendor home page to get proprietary drivers for graphics is not recommended (well, more manual work involved, so more mistakes possible), it is better if you install them using System->Administration->Hardware Drivers.

---

### Post by joshmuffin on 2009-01-01
With 2) OpenOffice is completely compatible just make sure to make sure that it saves as .doc rather then the default .odt

---

