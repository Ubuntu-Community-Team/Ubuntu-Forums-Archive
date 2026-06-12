---
title: "partition help!"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by Qualia on 2010-01-05
ok, right now I am trying to install Ubuntu 9.10 on my hard drive on a partition, and in installation it gives me this message:

"The test of the file system with type ext3 in partition 3 of SCSI (0,0,0) (sda) found unexpected errors."


what should I do? :(

---

### Post by tom.swartz07 on 2010-01-05
> **Qualia said:**
> ok, right now I am trying to install Ubuntu 9.10 on my hard drive on a partition, and in installation it gives me this message:

"The test of the file system with type ext3 in partition 3 of SCSI (0,0,0) (sda) found unexpected errors."


what should I do? :(

Hiya!

No need to fear, its fixable!
Im basically slowly becoming the go-to guy for partition help here on the forums, so youre in luck i guess :D

Okay, before we begin, I need some information about your computer and setup.


1. What brand/model computer are you using? This is useful for determining BIOS options when we get started.

2. Do you have any other OS's on your computer before you began? Windows XP, Vista, etc?

3. Referring to #2, If so, do you have any important information that you need stored elsewhere? While there is a high probability that everything should be safe, there is always a chance for a catastrophic crash- especially when you are performing actions like installing new OS's on your computer. We could custom tailor this guide to show you how to back up these files, just in case.

4. What methods or guides you used when you installed Ubuntu to get you to this point. For example, did you use WUBI or a LiveCD? Was there an online guide you used? 

5. If you can boot into a LiveCD, and select 'try w/out making changes', Open a terminal (applications>accessories>terminal) and type the following command
```
sudo fdisk -l
``` 
(lowercase L) and paste the stuff it spits back here too.

After I could get at least most of this info, we could get started with your fix! Until then, we should hold off on any major tweaking, as you may lose data.

You will need a LiveCD, which is just the Ubuntu .iso file burned to a CD. This will allow you to get back into the system and make the changes needed.

---

### Post by Qualia on 2010-01-05
1. I am using a Dell Latitude D520, with two partitons (not including the one I want to use for Ubuntu)

2.Yes, I have Windows XP on another partition, and i have a Dell ultility partition as well, and of course a partition in ext3 which I plan on using for Ubuntu.
 My BIOS is A04 

3. I would like to keep my window xp partition! The Ubuntu install wont mess with it right? I had it to be instlled on seperate partition that I made earlier

4. I am using a Ubuntu Live CD (9.10), through the "try without changes" selection and I was following a guide I found on youtube: [http://www.youtube.com/watch?v=GhnLk3gviWY](http://www.youtube.com/watch?v=GhnLk3gviWY)
Earlier, with the help of a guide on youtube as well, I also used the CD to use an app called "clamtk" to get rid of some viruses that were on my XP partition.

5.

---

### Post by Qualia on 2010-01-05
Whoops, I'll post 5 later on...

---

### Post by tom.swartz07 on 2010-01-06
> **Qualia said:**
> Whoops, I'll post 5 later on...

Alrighty. Sounds okay so far. Just to clarify, you havent installed Ubuntu yet?

Its starting to sound like you have a old BIOS. Look and see if you have any updates available for your BIOS. This should clear up any of the problems you experience with the LiveCD not recognizing your drives, etc.

---

### Post by Qualia on 2010-01-06
I had to unmount my windows partition earlier in order to resize it, could that have to do with anything? The windows partition is the nfts one

and as for the sudo thing.. here is the output:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        4654    37335060    7  HPFS/NTFS
/dev/sda3            4655        9729    40764937+  83  Linux

(nope, i have not installed Ubuntu, only unmounted my windows partition off a Ubuntu 8 version CD using Gparted to resize it and make a partition for Ubuntu. I am using a 9.10 Live CD right now, and plan to install this. I have not installed anything on the new partition (sda3)

---

### Post by tom.swartz07 on 2010-01-06
> **Qualia said:**
> I had to unmount my windows partition earlier in order to resize it, could that have to do with anything? The windows partition is the nfts one

and as for the sudo thing.. here is the output:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        4654    37335060    7  HPFS/NTFS
/dev/sda3            4655        9729    40764937+  83  Linux

(nope, i have not installed Ubuntu, only unmounted my windows partition off a Ubuntu 8 version CD using Gparted to resize it and make a partition for Ubuntu. I am using a 9.10 Live CD right now, and plan to install this. I have not installed anything on the new partition (sda3)

Great! Its nowhere near as bad as I though it would be. The problem is coming from the fact that you 'already' have Linux filesystem on your drive. You should just delete partition SDA3. Select 'Use largest continuous free space' from the Ubuntu liveCD installer when youre going to it then.



Just for future reference, normally you dont have to manually resize your partitions before you install. The install CD will help walk you through the process too.

Hope this helps! Good luck!

---

### Post by Qualia on 2010-01-06
Thank you! :D

---

### Post by tom.swartz07 on 2010-01-07
> **Qualia said:**
> Thank you! :D

Great! let us know how it worked!

If everything works great, and you dont have anything more to add, please mark the thread as [solved] from the thread tools. This way, others could read it and learn from your post! :D

---

### Post by Qualia on 2010-01-07
It has worked fine! I now have Ubuntu installed next to Windows XP! No problems whatsoever! :D

---

### Post by VraiChevalier on 2010-01-07
Way cool. Nice fix tom.swartz07 ! Well done. =D>
(I feared we may be witness to a disaster in the making.):(

---

### Post by kekebay on 2010-01-07
Great! let us know how it worked!
Thanks for sharing it

---

