---
title: "Linux swap in GParted"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by Hairywings on 2011-02-06
Dear all,

I have a simple question: I have allocated 8GB of my HD as linux-swap via GParted on my ubuntu 10.10. It states "linux-swap" as file system. Is it going to work as swap already, or I need to do something extra?

Thanks a lot in advance!

---

### Post by Paqman on 2011-02-06
Was it being used as swap already (ie: did you just expand it?) Or have you created a brand new swap partition?

---

### Post by mcduck on 2011-02-06
> **Hairywings said:**
> Dear all,

I have a simple question: I have allocated 8GB of my HD as linux-swap via GParted on my ubuntu 10.10. It states "linux-swap" as file system. Is it going to work as swap already, or I need to do something extra?

Thanks a lot in advance!

You need to check the UUID of the swap partiton, and then configure it in /etc/fstab.

(if you already had a swap partiton, and just changed it's size, you still need to get the new UUID and edit the existing fstab entry accordingly. Any editing of partitions will change their UUID).

Anyway, to get the UUID's for all your partitions, open a terminal and run "*blkid*". Copy the swap partition's UUID somewhere.

The run "*gksudo gedit /etc/fstab*" and chnage the UUID in the old swap entry to the new one, or if you don't have one add it like this:
```

UUID=b99b645f-5af1-47bd-b5a7-74bf35d53995 none swap sw 0 0
```
(use the UUID you got from the *blkid* command, of course. :))

After that save the file and run "sudo swapon -a" to start using the swap.

---

### Post by Hairywings on 2011-02-06
Thanks a lot for your replies!
It seems like applying "pending operations" takes some 2 hours and still not finished. I just created new swap (didn't have any before). Should it be so long??? After it's done I'll try to follow your recommendations. I don't know if it matters, I have dual-boot with win7.

---

### Post by srs5694 on 2011-02-06
You can find out what swap space is currently being used with swapon's -s option, as in:

```

$ **swapon -s**
Filename                Type        Size    Used    Priority
/dev/sda9                               partition    1465340    0    -1

```

This example shows that /dev/sda9 is currently being used as swap space. If, after you reboot or type "sudo swapon -a", swap space you've configured is not being used according to "swapon -s", then you should examine your /etc/fstab configuration. If it is being used, then there's no need to mess with /etc/fstab.

---

### Post by korleon on 2011-02-06
I think 8GB is more than you really need for swap most of the guides I've read recommend 2GB.  

It's easy to check from the gparted by right clicking the swap partition.  If you see "swap on" in the context menu then it's NOT in /etc/fstab.  You can also copy the UUID from the Gparted info menu to paste into your text editor when you follow mcduck's advice.

---

### Post by Paqman on 2011-02-07
> **Hairywings said:**
> Thanks a lot for your replies!
It seems like applying "pending operations" takes some 2 hours and still not finished. I just created new swap (didn't have any before). Should it be so long??? After it's done I'll try to follow your recommendations. I don't know if it matters, I have dual-boot with win7.

Modifying partitions can be really slow, especially if you're moving a big one.

---

### Post by Hairywings on 2011-02-12
Dear all,

I have finally made my swap with GParted, then followed **mcduck's** suggestion and finally checked as **srs5694** advised. Seems like it works! I've understood that my swap should be twice as big as my ram if possible (in perfect world), so I let it be perfect :). 
Thank you so much!

__

---

