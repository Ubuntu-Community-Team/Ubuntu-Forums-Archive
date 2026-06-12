---
title: "Disk space appears to be lost (not the ext3 5% reserved issue (I believe))"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by slimvad on 2009-03-07
Dear all,

I've just finished installing Ubuntu 8.10 after a HDD upgrade. This time I chose to go for separate ext3 primary partitions for the / and /home directories.

The latter is supposed to be 250 GiB (i.e. ~268,43 GB), but looking at the System Monitor I see that my /home only has 246.1 GiB of Total space...

So I'm kind of curious - where did the 3.9 GiB go?

Thanks for reading this one.

---

### Post by Shippou on 2009-03-07
> **slimvad said:**
> Dear all,

I've just finished installing Ubuntu 8.10 after a HDD upgrade. This time I chose to go for separate ext3 primary partitions for the / and /home directories.

The latter is supposed to be 250 GiB (i.e. ~268,43 GB), but looking at the System Monitor I see that my /home only has 246.1 GiB of Total space...

So I'm kind of curious - where did the 3.9 GiB go?

Thanks for reading this one.

I'm not sure if I am reading this post right, but then HD spaxce is not exactly what it says; i.e., a 250GB HD is not 250 per se. This is only an estimation, as sizes are really measured in terms of powers of two (i.e. in binary number base). So don't be surprised if your 250GB becomes less (or luckily, more) than what it's supposed to be (it also happened to me; my 80GB HD became 73GB.)

---

### Post by Ms_Angel_D on 2009-03-07
check here [http://ubuntuforums.org/showpost.php?p=2294968&postcount=10](http://ubuntuforums.org/showpost.php?p=2294968&postcount=10) this could be the reason your missing 3.9 gb

---

### Post by Redache on 2009-03-07
If it was a whole Hard Drive this wouldn't be a shocker. But if you made Partitions and set it to 250Gb then it should be 250Gb!. 

Is it a partition that spans the whole disk or is it within the disk? it could be that the Partition manager used as close to 250Gb as it could given the size of the disk.

---

### Post by slimvad on 2009-03-08
Heh, I'm aware of the marketing-GB issue. The new drive is actually 298 GiB (marketed as a 320 GB). Note that I pointed out the partition shoulda been 250 GiB (~268 GB).

So this is not the case.

As for the space consumed by the [artition and file tables... is it normal for things like these to take up ~4 GiB of space?

---

### Post by mikechant on 2009-03-08
> As for the space consumed by the partition and file tables... is it normal for things like these to take up ~4 GiB of space? 

1-2% - doesn't sound unreasonable to me.

---

### Post by Syed_Muhammad_Shahbaz on 2009-03-08
Change the jumper settings on your hard disk. It will make you able to get all the disk space they have marketed.

---

### Post by slimvad on 2009-03-08
> **Syed_Muhammad_Shahbaz said:**
> Change the jumper settings on your hard disk. It will make you able to get all the disk space they have marketed.
You're kidding me, aren't you?
There are no jumpers.
There is no spoon either.

---

### Post by mikechant on 2009-03-09
> Change the jumper settings on your hard disk. It will make you able to get all the disk space they have marketed.

If this is supposed to be a joke, I don't quite get it.

---

