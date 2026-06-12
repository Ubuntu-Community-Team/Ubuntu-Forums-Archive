---
title: "Questions about ext3 and reformating"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Videogameavatar on 2008-12-25
I have a 750gb external hard drive that I plan to dual boot. I plan to have ubuntu use the whole external hard drive. I also plan on useing the program fs-driver.

Heres the question: Do I need to install fs-driver first before I install ubuntu in order to access the files on my external hard drive which ubuntu will be using.

Second Question: Do I need to use gparted on my 750gb external hard drive first before I install ubuntu so that I have a ext3 filesystem, OR will ubuntu do that automatically for me when I select manual on the installation screen of ubuntu.

---

### Post by cariboo on 2008-12-25
> Heres the question: Do I need to install fs-driver first before I install ubuntu in order to access the files on my external hard drive which ubuntu will be using.


No Ubuntu uses it's on file system, and is its own operating system, you don't need to access any files during installation. You can install the driver before installing ubuntu, but you won't need it.

> Second Question: Do I need to use gparted on my 750gb external hard drive first before I install ubuntu so that I have a ext3 filesystem, OR will ubuntu do that automatically for me when I select manual on the installation screen of ubuntu.


No you don't need to partiton the hard drive before installing Ubuntu. There is a partitioner on the LiveCD that is part of the installation process.

If you plan on dual booting, with a standard installation the external hard drive will need to be attached in order to boot either Windows or Ubuntu. If you don't want this to happen, have a look [here]("http://help.ubuntu.com/community/Installation") and [here]("http://help.ubuntu.com/community/BootFromUSB").

Jim

---

### Post by Moop on 2008-12-25
If you mean Ext2 IFS, that's a program you install in windows so it can read ext3 file systems and it doesn't matter when you install it. 

Ubuntu will offer to format your drive during the installation.

---

### Post by Videogameavatar on 2008-12-25
You said:

If you plan on dual booting, with a standard installation the external hard drive will need to be attached in order to boot either Windows or Ubuntu. If you don't want this to happen, have a look here and here.

However couldnt I just change the Grub boot loader from default '(hd0)' to '/dev/sdc 

Then just change the boot order in the bios

Would THAT make it so i didnt have to have the external hard drive plugged in to boot either windows or ubuntu?

---

