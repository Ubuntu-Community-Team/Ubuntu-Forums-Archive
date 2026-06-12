---
title: "Ubuntu wont install after accidental hibernate."
date: 2011-02-08
forum: New to Ubuntu
---

### Post by Thinder on 2011-02-08
hi,
 
I wasnt paying attention and hibernated my computer. Now it wont resume.  i have Ubuntu 10.4 on a HP Dv9700 laptop. I have been in grub2 trying to get it to mount from the correct place but im having no luck any suggestions?
 
Thanks!
 
here is what my Grub screen looks like
 
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set eda71aa-bb70-4588-a9e6-411bd2e0eb1e
linux /boot/vmlinuz-2.6.32-28-generic root=uuid=eda71aa-bb70-4588-a9e6-411bd2e0eb1e ro quiet splash
initrd /boot/initrd.img-2.6.32-28-generic
 
 
P.s. I meant resume not install

---

### Post by Thinder on 2011-02-08
Computer will not boot with Ubuntu Live USB, displays text:
 
/init: line 7: cant open /dev/sr0: no medium found

---

### Post by Thinder on 2011-02-08
i tried manually setting the grub boot, but im knida guessing where to boot from.  I cant get any of the Grub2 commands to work with the command prompt so I cant see what is where.

What is going on??

---

### Post by matt_symes on 2011-02-08
Hi

> Now it wont resume.

What exactly is happening when you try to resume ?

Kind regards

---

### Post by Thinder on 2011-02-08
grub comes up with a menu like normal, then lines of text.  Killed on Mount: mounting/dev/ on root/dev failed: no such file or directory
with two more similar linesrefering to /SYS and /Proc 
 
 finishing on (initramfs)
 
 
> **matt_symes said:**
> Hi
 
 
 
What exactly is happening when you try to resume ?
 
Kind regards

---

### Post by matt_symes on 2011-02-08
Hi

> /init: line 7: cant open /dev/sr0: no medium found

If you have any CD's in your CD drives remove them and try to boot from the USB stick again.

Kind regards

---

### Post by Thinder on 2011-02-08
nothing in the drives,  still no good.
> **matt_symes said:**
> Hi
 
 
 
If you have any CD's in your CD drives remove them and try to boot from the USB stick again.
 
Kind regards

---

### Post by matt_symes on 2011-02-08
Hi

Can you disable any CDRoms in the BIOS. Make sure the Floppy Drive is disabled in the BIOS as well. Then try to boot from the stick again.

I'm pretty sure you will need a Live environment. If that does not work can you burn a LiveCD ?

It may be an issue with grub, fstab or maybe file system corruption off the top of my head. A live environment will tell us.

Kind regards

---

### Post by Thinder on 2011-02-10
I still cant get a live boot.  I puled the HD and still nothing.  Im swaping Harddrives around to see if i can get a boot off of the live USB with a windows HD

---

### Post by Thinder on 2011-02-10
I got a live boot by removing my Ubuntu Harddrive and INstallingmy old vista Hard drive and booting off the USB.  

I moved my Ubuntu Drive to a USB external case and plugged it in after the live boot.  Now I cant access the Ubuntu Drive. It shows up under places but will not open to explore it.

Error message Comes up with 

Unable to mount 311GB File System

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending


That tells me that something is tying up the Hard drive as soon as it receives power, and I believe it has something to do with my former unsucessful Hibernate.  Is there some way to break whatever is stopping this drive from mounting with out a repartition and format?

Thanks,

---

### Post by Thinder on 2011-02-10
Looking in diskutility I found a periphal called filesystem.squashfs.  I didnt notice this last time, but i didnt have the HD plugged in via USB.  

 Ill work on getting a screenshot



[IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

