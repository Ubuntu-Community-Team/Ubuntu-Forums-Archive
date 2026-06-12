---
title: "Repartitioning: failed to mount vfat partition!"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by webwiller on 2009-03-19
Hi all! It's hours I'm trying to repartition my hdd in order to get ubuntu installed but I keep gettin error when applying repartitioning.

The error I keep getting is "failed to mount a vfat partition on /mnt/data" & brings me back to the repartitioning table.

I tried moving that partition, believing it could be because it was primary, but logical wont work too. I tried moving it at one or the other end of the table..same error. After the error GParted says the partition is unknown, but when I reformat it with fat32 it says successfull. But during installation same error again...please...I'm really stuck and tired...:(

---

### Post by ivanvajar on 2009-03-19
Did you try formating it as **EXT3** and not fat32?

---

### Post by webwiller on 2009-03-19
I need it to be shared between win/ubuntu. Do you mean format it as ext3 and than reformat it as vfat AFTER mounted and finished install? From inside Ubuntu?

---

### Post by webwiller on 2009-03-19
This is the situation...am I doing something wrong?

---

### Post by ivanvajar on 2009-03-19
I'm not sure that you can install Linux on fat32. For all the partitioning you want to do, use LiveCD. Boot Linux from it and then work with partitions. There are programs that make ext3 partitions visible to Windows. However, boot from liveCD to do all the partitioning.

---

### Post by ivanvajar on 2009-03-19
Why don't you format it as ntfs?

---

### Post by ivanvajar on 2009-03-19
Look, if you want to install Ubuntu, you need 1 ext3 partition (about 15 GB mountpoint '/'), 1 swap partition (512 - 1024MB). Everything else can be formated as ntfs for data storage. You just need that second partition to store your data, right?

---

### Post by webwiller on 2009-03-19
That's what I did. The image I posted is taken from inside the live cd.

---

### Post by ivanvajar on 2009-03-19
If you need that partition only for data storage, format it as fat32 or ntfs. There is no need to give it mountpoint. I use 3 ntfs partitions for storing both Ubuntu and Win data.

---

