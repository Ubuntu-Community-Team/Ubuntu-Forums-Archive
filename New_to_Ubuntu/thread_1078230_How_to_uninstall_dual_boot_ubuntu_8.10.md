---
title: "How to uninstall dual boot ubuntu 8.10"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by bha148 on 2009-02-23
Hi, I want to uninstall the ubuntu 8.10 and I wanto install it again... How can I uninstall the ubuntu 8.10.. I am using windows xp and ubuntu in dual boot method.
Thanks.

---

### Post by bertolo on 2009-02-23
uninstall ubuntu using partition magic. then run partition magic again to recover free space to a new windows partition.

---

### Post by bha148 on 2009-02-23
> **bertolo said:**
> uninstall ubuntu using partition magic. then run partition magic again to recover free space to a new windows partition.

Ok, thanks. I will try that.

---

### Post by kahlil88 on 2009-02-23
Partition Magic is commercial software, isn't it? If you want to remove Ubuntu and re-install it, boot from the install disc and overwrite the old Ubuntu system.

---

### Post by candtalan on 2009-02-23
> **bertolo said:**
> uninstall ubuntu using partition magic. then run partition magic again to recover free space to a new windows partition.
perhaps you mean 
Parted Magic?
[http://partedmagic.com/](http://partedmagic.com/)

I use it a lot and it is easy to use. It would be easy to delete the partitions which currently hold ubuntu - probably the partition for system (  /  ) and also for swap.

Care must be taken obviously to identify which is the Windows partition (NTFS?) and the others. 

The Ubuntu installer does have an option to install into 'the largest unused space' on the hard drive, and I would use this choice in this case.

As always, ensure you have a good backup of your data before starting.

---

### Post by bertolo on 2009-02-23
anysoftware will do fine

---

### Post by hammad1337 on 2009-02-23
>Put your live CD in, and reboot.
>Run Install program.
>when you get to partitioning, choose manual.
>select the partition to which Ubuntu was installed earlier. (It will be an ext3 partition)
>Double-click it to bring up its properties.
>From drop-down, choose ext3 journaling filesystem.
>Select mountpoint as: /
>check Format partition.
>Click ok.
>Then click next and continue with the install.
Your Ubuntu will be re-installed, deleting the older installation. Your windows partition will remain untouched and unharmed. You will be able to dual-boot as well.

Hope this is helpful.

---

### Post by cgb223 on 2009-05-09
if u installed the partition by putting in the disk while in windows and all that stuff then there should be a C:\Ubuntu folder (or where ever you saved it) that has an uninstall feature in that folder called something like Uninstall-Ubuntu. follow the instructions from there.

i hope that helps!

---

### Post by raymondh on 2009-05-09
> **kahlil88 said:**
> if you want to remove ubuntu and re-install it, boot from the install disc and overwrite the old ubuntu system.

+1 if you decide to reinstall and dual boot

(and if you decide not to dual boot, remember to fix the master boot record (MBR))

---

### Post by webwiller on 2009-05-09
If you have a separate partition with WIN XP on it, up and running, and another one with ubuntu which you want to erase and reinstall, well, I perfecly agree with hammad1337, I did it many-many times with no troubles at all.

If you install ubuntu AFTER windows it's fine, cause Grub will automatically find windows, live it untouched and give you the option to boot the one or the other at boot time.

If you do so, and repartition it manually, dont forget to allow a swap area (size depending on how much ram you have, let's say you have 1Gb/ram, another 1Gb/swap will do fine, if you have lots, i.e. 4Gb/ram, then is up to you, but 256/512Mb will be more than enough in most cases).

Finally, as you are repartitioning, I would suggest a /home partition. You format a different ext3 partition with /home as mount point.

Then, if you like, you can format a shared partition in ntfs, which can be seen, read and wrote by both win&ubuntu. You can set its mount point as /mnt/data

---

### Post by jkoval on 2011-02-28
> **cgb223 said:**
> if u installed the partition by putting in the disk while in windows and all that stuff then there should be a C:\Ubuntu folder (or where ever you saved it) that has an uninstall feature in that folder called something like Uninstall-Ubuntu. follow the instructions from there.

i hope that helps!

If I run the Uninstall-Ubuntu,
do I still have to do the 
mbrfix 
to remove the reference to ubuntu from the master boot record

---

