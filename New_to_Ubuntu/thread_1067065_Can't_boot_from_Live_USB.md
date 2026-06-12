---
title: "Can't boot from Live USB"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by jbrown96 on 2009-02-11
I've tried several times to create a live USB to reinstall Ubuntu from. However, it never ever seems to work. I download the ubuntu iso, and install usb-creator. I even verified the md5 hash to make sure the image is good. It completes successfully, but won't work at all. Most of the time it's not even recognized but when it is it just hangs and says > GRUB

I've tried different USB drivers, but nothing works. I did get it working several months ago, but that was after creator a Fedora live USB, which worked perfectly. Somehow doing the live Ubuntu USB after worked.

How can I get this to work?

---

### Post by ibizatunes on 2009-02-11
what version of ubuntu are you installing? 8.04 8.10? Alt or desktop version?

What version of ubuntu are you install from? 8.10 with built in usb boot creator?

Maybe you need to gpart the usb disk and wipe it completely

---

### Post by jbrown96 on 2009-02-11
I have deleted the the partitions before and it didn't work. the boot and lba flags are set correctly, so I don't think it is a partitioning problem. I'm running 8.10 (AMD64) and trying to create an 8.10 (x86) live USB. I guess the only difference is the architecture.

---

### Post by snowpine on 2009-02-11
Give unetbootin a try; it is a utility that automates the process.

---

### Post by uberg on 2009-02-11
How old is the machine you are trying to boot into?  I was really excited when i got a little key ring for Ubuntu but was quickly dosed when i found out a lot of older machines out there can't boot from USB.  Too old for such a great concept.  So some machines it will work on and some not.

Joe

---

### Post by C.S.Cameron on 2009-02-11
I've had problems with usb-creator.
After using Unetbootin and wiping the files usb-creator worked ok.
I've heard that it is sometimes necessary to create a new partition table to get U-C to work.
Unetbootin makes a pretty good installer by itself.

---

### Post by jbrown96 on 2009-02-11
> **C.S.Cameron said:**
> I've had problems with usb-creator.
After using Unetbootin and wiping the files usb-creator worked ok.
I've heard that it is sometimes necessary to create a new partition table to get U-C to work.
Unetbootin makes a pretty good installer by itself.

It would make sense that it could be the partition table. 

Thanks Snowpine. Unetbootin wasn't really what I was looking for. It's ugly but works. Thanks

---

