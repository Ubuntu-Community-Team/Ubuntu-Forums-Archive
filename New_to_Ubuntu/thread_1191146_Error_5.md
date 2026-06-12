---
title: "Error 5"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by zhenpenthaye on 2009-06-18
Why is it that with every download of ubuntu from way back, when I try to install, I get this error 5 - during the copying files stage of the installation? It has happened again with 9.04.  Very trying!

---

### Post by raymondh on 2009-06-19
> **zhenpenthaye said:**
> Why is it that with every download of ubuntu from way back, when I try to install, I get this error 5 - during the copying files stage of the installation? It has happened again with 9.04.  Very trying!


Hello Zhenpenthaye,


[I]5 : "Disk geometry error"

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).[/I]

As noted above, older BIOS' can only access a limited amount of cylinders to look for an operating system.  This error can result when we put newer, bigger HD's in an older system, or if we dual boot and put the second OS beyond the cyclinder limit of the BIOS.  

Install Ubuntu within the first 8GB of your hard drive, if possible.

---

