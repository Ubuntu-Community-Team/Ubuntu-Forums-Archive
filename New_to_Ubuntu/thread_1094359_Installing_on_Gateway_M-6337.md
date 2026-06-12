---
title: "Installing on Gateway M-6337"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by barrett1 on 2009-03-12
I have a Gateway M-6337 Notebook with Vista

I have been trying to load it with XP.  XP does not have the driver for the hard disk.  Gateway will supply the drive, but there is no floppy drive.  No luck trying to slipstream the driver.

I want to install Ubuntu.  If I download the CD files and make bootble disks - will there be a driver for the gateway laptop hard drive?

---

### Post by prcm311 on 2009-03-12
I can't say yes 100%, but I've never not had a hard disk driver when using any version of Ubuntu (since 6.##) with any type of hardware.

As for your XP install, I think you can load it from a USB drive.

---

### Post by halitech on 2009-03-12
is this the machine you are referring to?

[http://support.gateway.com/s/Mobile/2008/Avalon/1015606R/1015606Rsp2.shtml](http://support.gateway.com/s/Mobile/2008/Avalon/1015606R/1015606Rsp2.shtml)

I'm assuming you are talking about the fact that you have a SATA drive. Ubuntu (and linux in general) doesn't have a problem with SATA drives. 

Looking at the specs, only thing that might be an issue is the wireless depending on what chipset Gateway uses in this laptop. Other then that, everything should work fine and even the wireless we can probably get working for you.

---

### Post by barrett1 on 2009-03-12
I am new to this forum and Ubuntu

Those were great and very quick answers!

THANKS   I am encouraged about stitching

Barrett

---

### Post by barrett1 on 2009-03-13
> **halitech said:**
> is this the machine you are referring to?

[http://support.gateway.com/s/Mobile/2008/Avalon/1015606R/1015606Rsp2.shtml](http://support.gateway.com/s/Mobile/2008/Avalon/1015606R/1015606Rsp2.shtml)

I'm assuming you are talking about the fact that you have a SATA drive. Ubuntu (and linux in general) doesn't have a problem with SATA drives. 

Looking at the specs, only thing that might be an issue is the wireless depending on what chipset Gateway uses in this laptop. Other then that, everything should work fine and even the wireless we can probably get working for you.
Thanks for your answer.

Yes - That is my computer.

I have the install disk for Ubuntu working fine - just as Dovorak from PC Mag said it would.  I played around a little.

I have a question before completing my install:

I want to run XP.  Not dual boot as I would have the same SATA driver problem.  Is there a way to run XP as something like a process and have Ubuntu do the disk access with its own driver?

Maybe I am asking too much from this forum.

Thanks,

Barrett

---

### Post by halitech on 2009-03-13
you could install Ubuntu then use virtualbox to run XP as a virtual machine but you will take a performance hit running it that way. ie. If you are a gamer, forget about most games as running an OS virtually will not take full advantage of your hardware.

Honestly if you want XP, find someone locally that can help you get the SATA drivers so you can install XP.

---

