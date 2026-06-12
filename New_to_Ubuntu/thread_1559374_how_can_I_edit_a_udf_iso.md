---
title: "how can I edit a udf iso?"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by mamamia88 on 2010-08-23
I need to delete a file on an iso so I can use my windows 7 starter product key to reinstall on my netbook.  but when i mount the iso it only shows a file called readme.txt.  I've tried using a modified nautilus script but it didn't work.  can someone please help me out i don't want to waste my entire day off

---

### Post by arochester on 2010-08-23
Clarification needed. Do you want to reinstall Windows 7 _only_ on your netbook? 

Have you seen "Windows 7 ISOs you can download" - [http://www.insidesocal.com/click/2010/08/windows-7-isos-you-can-downloa.html](http://www.insidesocal.com/click/2010/08/windows-7-isos-you-can-downloa.html)

---

### Post by mamamia88 on 2010-08-23
I have a proffesional iso from digital river.  I want to delete the ei.cfg file so it will let me chose starter edition and I can use my key. would you know how I could mount this iso in ubuntu?  and yes only on my netbook

---

### Post by Paul820 on 2010-08-23
Have you tried isomaster, it's in the repositories.

---

### Post by mamamia88 on 2010-08-23
i will thanks

---

### Post by colferma on 2010-12-13
I'm a bit late here, but did ISO Master work for the OP? I'm having the exact same problem. I have a windows7 iso that I want to edit but all I see in ISO Master is a readme text file that tells me this:

This disc contains a "UDF" file system and requires an operating system 
that supports the ISO-13346 "UDF" file system specification.

Any help is greatly appreciated.

M

---

### Post by dr_duck on 2010-12-13
UDF is a filesystem, like ntfs or ext3.

There is a kernel module for it, it's probably not built (it usually isn't by default).

I would guess that you'll need to built or somehow acquire the kernel module for UDF fileststems, then you can just mount the iso via the usual means.  Not sure how you're going to delete a file from it though.

To build the module, you'll need the kernel source for the version you're running & the development tools (compilers etc).  Then build the module (you don't need to build the whole kernel), copy it to your live kernel location & load it.

EDIT:
Oh, also check this (its for vista dvds): [http://ascending.wordpress.com/2008/06/14/howto-read-vista-burnt-udf-dvds-on-ubuntu-linux/](http://ascending.wordpress.com/2008/06/14/howto-read-vista-burnt-udf-dvds-on-ubuntu-linux/)

---

### Post by porec on 2012-11-05
Hi.

try to install 7zip from Ubuntu software center, with the add-ons.
then right click and choose "extract here"


You are probebly looking for a way to repack the ISO file, and I would sugest ISO Master.

God luck.

---

### Post by fhqiihcy on 2012-11-05
you can try ultreiso [IMG]http://allkindsofpic.info/images/giai.gif[/IMG]

---

### Post by sandyd on 2012-11-05
**Necromancing - thread closed**

Please do not post in threads more than one year old.

Thanks!

---

