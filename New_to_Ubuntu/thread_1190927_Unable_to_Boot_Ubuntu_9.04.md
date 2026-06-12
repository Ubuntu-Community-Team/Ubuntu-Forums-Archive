---
title: "Unable to Boot Ubuntu 9.04"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by SandyM on 2009-06-18
**SORRY, BUT THIS STORY IS LONG. PLEASE BEAR WITH ME.**

Recently I did some editing in my drives through G-Parted in Ubuntu Jaunty but ultimately did not end up with any significant changes as the number of drives are same as before .I had some swap area which was insufficient so I decided to extract some more disk space from my other existing drive and get it merged with the already existing swap area.

I deleted my swap Partition (and that was my primary partition).
In the next step I resized my other drive to extract some unused disk space to be used by Linux Swap.

But this unallocated area did not merge with the area vacated by SWAP (PRIMARY) PARTITION I deleted in previous steps.

Now since I failed to merge the two unallocated disk area, I resorted to convert the bigger space (extracted from other drive) into my Swap Area.

THATS IT, IT WAS THE LAST TIME I WAS SEEING MY UBUNTU 9.04.

Later when I rebooted, I was not able to do so and was receiving the following error message




 [B] [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> 
[/B]


I tried everything and even used EASY BCD 1.7.2, as I normally do to restore my boot related problems with ubuntu. It has never failed but this time I am Disappointed as it failed this time.

**PLEASE HELP.............................**

---

### Post by caravel on 2009-06-18
I don't really follow you...  Partitions have to be contiguous blocks, so perhaps you expected two unadjoined partitions to join into one?

Did you delete the primary partition altogether?

It looks like Grub cannot find your / partition.  Unless anyone has some better advice or unless you want to go into a lot more detail I think you should boot from the LiveCD, mount the partition containing your data and back it up, then just bite the bullet and reinstall, this time setting up your partitions correctly from the start.

---

