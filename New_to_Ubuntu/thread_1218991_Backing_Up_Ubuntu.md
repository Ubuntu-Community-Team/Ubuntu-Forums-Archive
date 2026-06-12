---
title: "Backing Up Ubuntu"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by moose4204l on 2009-07-21
I want to dual boot Vista on my laptop. Is there a utility that will back up my ubuntu side first. Also, if I some how ruin everything, does that backup image completely restore the laptop to the way it was even with a reformat?

thanks

---

### Post by SunnyRabbiera on 2009-07-21
Well you can just get an external hard drive, and make sure to constantly back up your home directory.

---

### Post by bacil on 2009-07-21
you can backup whole your partition to file with

```

dd if=/dev/sda1 of=yourfile.iso  

```
and then after reformat you can just easily after you bootfrom live cd put your data back

```

dd if=yourfile.iso of=/dev/sda1

```

mind you /dev/sda1 is your partition so change it to what ever your ubuntu partiton is, dont forget to copy yourfile.iso somewhere where you will not delete it by formating and lastly after all that you have to reinstall grub as described in this thread

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by TuckLive on 2009-07-21
I use rsync to backup only my home directory to an external drive.  I have a .txt file to keep track of my programs that I would need to reinstall if I had a meltdown.

```
sudo rsync --delete -azvv /home/tucklive/ /media/disk/Adam/Bigbox/
```

---

### Post by Paddy Landau on 2009-07-21
You may want to try either [PartImage]("http://www.partimage.org/") or [Clonezilla]("http://clonezilla.org/").

They both allow you to back up a partition and restore it. They also back up only the used parts of the partition, and compress the image, so that they use the least possible space.

PartImage doesn't support ext4 but Clonezilla does.

---

### Post by Cheesemill on 2009-07-21
+1 for CloneZilla

---

### Post by Paddy Landau on 2009-07-21
> **Cheesemill said:**
> +1 for CloneZilla
Apart from the fact that the download isn't working at the moment...

---

