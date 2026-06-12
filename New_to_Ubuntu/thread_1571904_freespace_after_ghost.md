---
title: "freespace after ghost"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by yatir on 2010-09-10
After having only 1.9 GB left on my hard drive on my laptop. I installed a new one and copied my old system using a ghost program.
Ubuntu works great on my new hard drive, but it still thinks that I have only 1.9 GB of freespace. It even informs me of that after I reboot.


Thanks,
Yatir

---

### Post by spcwingo on 2010-09-10
First I recommend to BACKUP, then boot from a live CD.  Upon booting from the live CD open gparted and expand your Ubuntu partition to fill the free space.  After that, just boot normally with your roomy new partition.  :)

---

### Post by yatir on 2010-09-11
I am not an expert with partitions, so maybe you can guide me.

I have /dev/sda1 as ext3

and I have the rest of the GB as unallocated.
How do I add them to /dev/sda1/ ?


Yatir

---

### Post by yatir on 2010-09-11
Just to make think clear, here is a screenshot.

---

### Post by rolnics on 2010-09-11
The screen shot's a little unclear, but what I can see is you are going to have to move your swap area (/dev/sda5).

As spcwingo said BACKUP your data first! Then probably easiest way is to boot via livecd and then delete the swap area using gparted, then resize your Ubuntu partition and leave about a 1GB or what ever is 1.5 times the amount of ram you have. Then create a new swap are here and then reboot and you'll have a roomy install.

---

### Post by yatir on 2010-09-11
Why do I need to delete the swap?
 
I run it on LiveCD, and the 'Lock' symbols are gone.
Can't I just resize the extended and thus move the unallocated into the extended.
If this is something that you recommend, do I now have to format it as a logical partition ext3 or ext2?
 
 
thanks,
Yatir

---

### Post by rolnics on 2010-09-11
From what I see from your screen shot, your Ubuntu install is on a primary partition, is that correct? Gparted will only resize partitions if there is unallocated space next to the said / selected partition. Also, I might be wrong here, but I'm sure primary partitions won't just move / change to extended / logical partitions.

Deleting the swap was just a suggestion, you could just move it, but it would probably end up being more time consuming, well it would on my pc!!

---

### Post by yatir on 2010-09-11
in that case, there is something I don't understand.
When I delete the swap, it just turns grey and into unallocated.
Why do I need to resize sda1?
 
Could you please be a little more specific on what exactly I need to do.
 
thnx.

---

### Post by rolnics on 2010-09-11
> **yatir said:**
> 
When I delete the swap, it just turns grey and into unallocated.


Yes that is what is supposed to happen when you delete a partition. This will help in adding more space to your install, don't worry you can add the swap partition back in gparted again.

> **yatir said:**
> 
Why do I need to resize sda1?


In your original ghost image it copied your old partition size, but you have xxxGB unallocated space now (greyed out area). To add this space to your install you will need to resize sda1, as this is your /(root) partition the installed system.

---

### Post by yatir on 2010-09-11
Ok, I deleted the swap.
It doesn't let me resize sda1.

---

### Post by rolnics on 2010-09-11
Ok, I see now, I didn't notice the extended partition (sda2). Delete the extended partition (sda2), this will then allow you to resize sda1 remember to leave space to put a swap area in.

---

### Post by yatir on 2010-09-11
thanks.
Works perfectly.

---

### Post by rolnics on 2010-09-11
No problem, if that's all ok now, then please mark this thread solved.

---

