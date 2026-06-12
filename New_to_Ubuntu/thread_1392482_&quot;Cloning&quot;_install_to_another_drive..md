---
title: "&quot;Cloning&quot; install to another drive."
date: 2010-01-28
forum: New to Ubuntu
---

### Post by skymera on 2010-01-28
I currently have Ubuntu installed to a 10GB partition on my 150GB drive.
I need this drive for games and it's filling up fast (The 140GB Windows partition).

I have a 1TB F2 drive which i'd like to move Ubuntu to. 
Is there a way to "transfer" or "clone" my install to another partition?

Thanks

---

### Post by bullgr on 2010-01-28
the best sollution for me is clonezilla: [http://clonezilla.org/](http://clonezilla.org/)
with clonezilla you can make image backup of partitions or entire disks...

---

### Post by skymera on 2010-01-28
Thank you for the reply :)

I'll check out Clonezilla when i get home. It's blocked at college :(

I'm guessing i just copy all the data to my new partition, update-grub or something so i can boot to it.
Reinstall GRUB to the new drive's MBR and delete my old partition?

---

### Post by HermanAB on 2010-01-28
Howdy,

If you want to copy the whole disk from a smaller to a larger model, then you can simply boot off a live CD and use cat or data definition:

$ sudo cat /dev/sda > /dev/sdb

or
$ sudo dd if=/dev/sda of=/dev/sdb bs=1M

Read the man pages or Google for more details.

Use mount, df or ls /dev/sd* to figure out exactly which drive is which.  It would be most disappointing to get things the wrong way around.

Afterwards you can use fdisk to change the partitions and reclaim unused space on the larger disk.

---

### Post by skymera on 2010-01-28
> **HermanAB said:**
> Howdy,

If you want to copy the whole disk from a smaller to a larger model, then you can simply boot off a live CD and use cat or data definition:

$ sudo cat /dev/sda > /dev/sdb

or
$ sudo dd if=/dev/sda of=/dev/sdb bs=1M

Read the man pages or Google for more details.

Use mount, df or ls /dev/sd* to figure out exactly which drive is which.  It would be most disappointing to get things the wrong way around.

Afterwards you can use fdisk to change the partitions and reclaim unused space on the larger disk.

Thank you, i have a Lucid disc luckily, i haven't lost it yet! :D

I've also seen that gParted can be used to Copy/Paste partitions.
I was condsidering this the editing GRUB and fstab on the copy then installing GRUB to new MBR.

---

### Post by oldfred on 2010-01-28
If you have done a lot of customization copying may be better, but alternatively you can easily manually partition and install a new copy. This then gives an opportunity to add a new /home if you do not have one as that is all you have to copy from your old /home first to save your settings.  If you have added a lot of additional programs you can export them and reimport them either from synaptic or command line.

---

