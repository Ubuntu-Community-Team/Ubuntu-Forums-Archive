---
title: "Resizing partition help"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-01-30
How do I make one partition take up the entire hard drive after it's already been installed?

---

### Post by nightmare0 on 2009-01-30
You need to install a partitioning program like gparted

---

### Post by oldsoundguy on 2009-01-30
or you can boot with the CD and go to system> administration> partition editor.  You can expand there .. will take a bit of figuring out if there is anything on the partition you want to utilize, but that is another way.

(I used that to expand a partition on a WINDOWS machine .. works well there, too!)

---

### Post by JawsThemeSwimming428 on 2009-01-30
```
sudo apt-get install gparted
```

Once you install it you can launch it and resize the drive from the first window.

---

### Post by Sup3r3g0 on 2009-01-30
Okay so I installed Gparted and opened it up. How do I know which partition I'm using right now? And if I resize it will it overwrite everything else?

Thanks, I appreciate the help.

---

### Post by Sup3r3g0 on 2009-01-30
How do erase the first partition and use the space it was taking up to add to the partition I'm using right now?

[IMG]http://i93.photobucket.com/albums/l41/buck3tph0t0/Gparted.png[/IMG]

---

### Post by balaknair on 2009-01-30
1) "How do I know which partition I'm using right now?"

You're using the logical partition sda6(on extended partition sda2) right now.

2) To resize/move the partition, it has to be unmounted first. Since this is the partition you have installed Ubuntu to, that means you have to boot into the LiveCD and use GParted(it's already there on the CD) to make any changes.

From the screenshot above, I think you'd be better off backing up all important data and reinstalling Ubuntu with a fresh partition table. You currently have Ubuntu installed on a logical drive (sda6) on an extended partition(sda2). The first partition(which you want to get rid of) is flagged as boot. Removing this partition is NOT a good idea, you will end up with an unbootable system.

S

---

