---
title: "My computer won't boot- mount doesnt work"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by JeannaMarie on 2010-08-12
Hi, I woke up this morning and my computer would not boot normally.  Instead, I got a screen saying the following:
 
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting/ sys on /root/sys failed: no such filr or directory
mount: mounting/proc on /root/proc failed: no such file or directory
Target filesytem doesn't have /sbin/init/
no init found. Trypassing init= bootary
 
{initramfs}
 
I looked at a previous forum on this topic, and tried to boot my system using my USB drive with the ubuntu download ( i do not have a working CD player), but I get the same message plus alot of extra code and the last line stating:
[        6.323720] sd 2:0:0:0 [sdb] attached SCSI removable disk
 
Any ideas on what I do from here?  I am a complete newb and understand next to nothing about computer programming.  Thanks for your time and help :)

---

### Post by MooPi on 2010-08-12
Did you reset your computer to boot from the usb drive ?

---

### Post by JeannaMarie on 2010-08-13
I don't know how to get my computer to boot from the USB drive.  How do I do this?

---

### Post by lkjoel on 2010-08-13
You go into the BIOS, and change the Boot order.

---

### Post by clabdio on 2010-08-13
Hi, the same happens to me, after install grub can't found de hd, i've tried twice, so I have now 2 installations, that doesn't work. But if I use de usb live it runs ok, any idea?
thanks:)

---

### Post by lkjoel on 2010-08-13
> **clabdio said:**
> Hi, the same happens to me, after install grub can't found de hd, i've tried twice, so I have now 2 installations, that doesn't work. But if I use de usb live it runs ok, any idea?
thanks:)
So boot normally, with no USB.
Then see if you can type.

---

