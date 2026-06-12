---
title: "partition concerns Xubuntu 10.10"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by jfbooth on 2010-11-01
Old Desktop computer.  512MB memory, 10G hard drive.

Installed Xubuntu 10.10 from CD . using entire HD.  Took the default partitioning.

I want to confirm the swap partition is appropriate.  Trying to find out what I actually have .. and if not right, get it right.  I **think** recommended swap for 512MB of mem should be twice that (1G), but maybe that is not true.

Tried to find 'ways' to see my partition info.  One recommendation was to use the command 'df'

jb@john-xubuntu:~/Desktop$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             8.8G  2.3G  6.1G  28% /
none                  243M  220K  243M   1% /dev
none                  248M  212K  248M   1% /dev/shm
none                  248M   88K  248M   1% /var/run
none                  248M     0  248M   0% /var/lock

Hmmmm, no mention of a swap file here.  I also found 'fdisk -l':

jb@john-xubuntu:~/Desktop$ sudo fdisk -l
[sudo] password for jb: 

Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000348d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1159     9304064   83  Linux
/dev/sda2            1159        1217      463873    5  Extended
/dev/sda5            1159        1217      463872   82  Linux swap / Solaris

That looks better .. but this NOOB doesn't know how to interpret this.  

**If** I need a 1G swap for a 10G drive, the swap should be 10% of the drive.  According to the above, I have a total of 9767936 blocks and swap is 463872 blocks, that is only 0.047489255 or about 5% of the drive.  I will say .. the machine seems to run OK AS IS .. but pretty slow (do not expect it to be very fast in the first place).

Do I NEED to adjust anything?  If so, how do I do it?

Comments, corrections, and advice are welcome and appreciated in advance.

---

### Post by ubunterooster on 2010-11-01
It is debatable whether swap is still needed but with your specs it looks very good

---

### Post by jfbooth on 2010-11-01
> **ubunterooster said:**
> It is debatable whether swap is still needed

OH?  Really.  Interesting.

> but with your specs it looks very good

Hmmm, That's good to know.  Thank you.

---

### Post by ubunterooster on 2010-11-01
No problem; glad to help. Actually, with my usage, Swap is often used, though 33GB of swap is more than I am likely to need. So, it is still used by many, but I would say that with over 1 GB of Ram it is not *really* needed

---

