---
title: "I think I have a swap set-up problem"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by jotiho on 2010-10-31
I am running xubuntu 9.04 on an old (-ish) PC with 496 MiB RAM and two hard drives, one with 4GiB (dev/sda1 at root) and the other  with 30 GiB (dev/sdb1 at /home)

The root drive is partitioned with 3.78GiB ext3 (3.29 used) , 235MiB extended, and 235MiB swap.

The larger drive has a 29GiB ext3 partition and a 1GiB swap partition.

Performance can be very slow (and triggers LOTS of disk reads on - as far as I can tell -  the smaller disk), particularly when handling large files and I suspect that this may be due to several features of the set up:

1.  not much RAM
2.  little free space on root drive
3. limited swap on root drive (?)
4. swap space on second drive not being recognised/used(?)
5. "swappiness" set at default value of 60

Before launching on a series of experiments, I'd appreciate any views on the what lines of attack to try first.  The steps I am thinking of are

a.  set swappiness =10
b.  increase the swap size on sda1, or delete this partition to force use of larger swap on the other drive 
c.  buy more RAM

In option b. Can I just delete the small swap partition in GParted?  How do I check that the system knows about the swap space on sdb?

Very grateful for any help you can give.

Best regards

Jotiho



c

---

### Post by Crusty Old Fart on 2010-11-02
Howdy jotiho:

Personally, I would go with option: b.
On my system, I have /root on /dev/sdc1 and /home on /dev/sdc5 (sdc is a SCSI drive).
My swap space is on /dev/sda2 (sda is an ATA drive)
I haven't had any swap space issues with this setup.

You raise a good question with this:
> 
In option b. Can I just delete the small swap partition in GParted?  How  do I check that the system knows about the swap space on sdb?

My answer is: I don't know. Do you feel lucky enough to try it out, hope it works, and deal with any problems later?

I don't know how many "hooks and handles" happen in the low levels to make the system recognize swap space. Seems to me that if you make sure your /etc/fstab file reflects the change, you may be a long way to staying out of trouble, but I don't know for certain.

I have moved and removed swap space between drives in Windows XP without ever even making partition changes and have never had a problem doing it. But that's XP, which is probably completely irrelevant in this case.

Good luck if you decide to experiment,

Crusty

---

### Post by gmargo on 2010-11-02
> 
 How do I check that the system knows about the swap space on sdb?
Use the **swapon** command.  Read the man page first.  "swapon -s" will tell you all partitions currently being used for swap.  For temporary results, you can use swapon to turn off the little drive's swap or turn on the big drive's swap or both.

For permanent results, you can edit /etc/fstab to control which partition(s) are used for swap. Assuming both drives' swaps are in use, just comment out the one you don't want in the /etc/fstab file.  No real need to delete or resize a partition.  If you want to later add swap to the big drive, you can do it in a file in the filesystem.  See the **mkswap** command for that.

---

### Post by jotiho on 2010-11-02
Thanks to both for your input.

swapon -s gave: 

Filename                Type        Size    Used    Priority
/dev/sda5                               partition    240932    0    -1
/dev/sdb2                               partition    1132572    0   -2    

I'm not sure which is taking priority here (the minus signs(?) confuse things).  The man page says priorities are non-negative and the highest is used first which would imply /dev/sdb2 would be the first to be used - is this right?

If so, then my problem is not swap priority, since the larger swap was being applied first all along...

Best wishes

jotiho

---

### Post by sandyd on 2010-11-02
> **jotiho said:**
> I am running xubuntu 9.04 on an old (-ish) PC with 496 MiB RAM and two hard drives, one with 4GiB (dev/sda1 at root) and the other  with 30 GiB (dev/sdb1 at /home)

The root drive is partitioned with 3.78GiB ext3 (3.29 used) , 235MiB extended, and 235MiB swap.

The larger drive has a 29GiB ext3 partition and a 1GiB swap partition.

Performance can be very slow (and triggers LOTS of disk reads on - as far as I can tell -  the smaller disk), particularly when handling large files and I suspect that this may be due to several features of the set up:

1.  not much RAM
2.  little free space on root drive
3. limited swap on root drive (?)
4. swap space on second drive not being recognised/used(?)
5. "swappiness" set at default value of 60

Before launching on a series of experiments, I'd appreciate any views on the what lines of attack to try first.  The steps I am thinking of are

a.  set swappiness =10
b.  increase the swap size on sda1, or delete this partition to force use of larger swap on the other drive 
c.  buy more RAM

In option b. Can I just delete the small swap partition in GParted?  How do I check that the system knows about the swap space on sdb?

Very grateful for any help you can give.

Best regards

Jotiho



c
you don't have enough disk space.
the computer starts writing data starting from the fastest regions to the slowest. which means your currently on the slowest regions of your hard drive.

you could try riserfs if you want, but its largely unsupported since the inventor is in jail.

---

### Post by jotiho on 2010-11-02
Thanks Sandy D.   Do you think the performance problem is linked with the location of the swap space (and would therefore be improved by having all the swap on the large disk), or are there inherent problems in having so little spare capacity on the primary disk?

---

### Post by Crusty Old Fart on 2010-11-02
Thanks to gmargo for injecting some much needed knowledge into this problem.

Upon studying the man pages, especially swapon(2), the suspicions I had regarding linux choking on setups that have multiple swap spaces seem to be unfounded.
From the man page for swapon(2):
> 
       There is an upper limit on the number of swap files that may be  used,  defined  by  the  kernel  constant
       MAX_SWAPFILES.  Before kernel 2.4.10, MAX_SWAPFILES has the value 8; since kernel 2.4.10, it has the value
       32.  Since kernel 2.6.18, the limit is decreased by 2 (thus: 30) if the kernel  is  built  with  the  CON&#8208;
       FIG_MIGRATION  option  (which  reserves two swap table entries for the page migration features of mbind(2)
       and migrate_pages(2)).
Ignoring the details, the general tone I get from this note is that linux is perfectly capable of handling several different swap spaces.

So...on second thought, the performance issue may be more a result of:
> 
2.  little free space on root drive
The space used on the /root partition fluctuates with the addition and removal of data while the system is running as things like .bash_history and various log files are managed.
When considering this:
> 
The root drive is partitioned with 3.78GiB ext3 (3.29 used)
We're looking at a /root partition that is 87% full. That's kind of pushing it, isn't it? I'm no expert at this, but at 87% usage, there doesn't seem to be much wiggle room for the amount of data to fluctuate on the /root partition. It could be that herein lies the crux of the whole problem.

---

### Post by jotiho on 2010-11-03
OK.  I've commented out the swap partition on the root drive.  That seems to have cut out a lot of disk activity, though I haven't tested it extensively. So far so good.

I'll not post this as SOLVED just yet, but it looks promising.:)

Thanks to all for your help.

(In looking at this I've also found some odd features of the way sda1 is partitioned, but I'll put this in a separate thread)

---

