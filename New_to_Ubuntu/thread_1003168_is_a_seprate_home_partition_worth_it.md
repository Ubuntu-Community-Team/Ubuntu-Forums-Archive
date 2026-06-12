---
title: "is a seprate /home partition worth it?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by DBrocks on 2008-12-05
Well, as you read in my title, is a separate /home partition worth it? I'm getting a new Ubuntu box, so I can do anything to it. (Except for stack some thermite on top of it and light it on fire). Thanks in advance.

---

### Post by snova on 2008-12-05
Worth what? It's easy to do from the installer.

I'm sure there are many advantages, but the only one I know of is that if you need to reinstall, you can keep /home as-is, which removes the bother of backing it up and then putting it back. And of partitioning again.

---

### Post by fooman on 2008-12-05
absolutely...and give it lots of room.  you will not be sorry.  :D

---

### Post by aysiu on 2008-12-05
It depends on your situation.

If you have a very small hard drive (my Eee PC, for example, has only 4 GB of total space), a separate /home partition is a very bad idea. I wouldn't put a separate /home on anything smaller than 30 GB.

When I had a bigger hard drive and used to keep a separate... partition of some kind, I quickly moved from having a separate /home partition to having a separate data partition. I actually wanted to do a fresh reinstall of every release and have it look fresh (no lingering old themes and settings).

But... if you have a very large hard drive and you actually want to keep your settings when you reinstall, a /home partition is definitely "worth it."

---

### Post by bumanie on 2008-12-05
A separate /home is useful if one has to do a reinstallation for some reason, because then you only have to reinstall to / and your data in /home is untouched.

---

### Post by DBrocks on 2008-12-05
Alright thanks alot guys. Im getting this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16883104035]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883104035") as a christmas present to myself. Wanted to see what you guys thought of a seperate /home partition.

---

### Post by squeabs on 2008-12-05
Let's suppose you install something that screws up your ubuntu install, so you reinstall. Won't having the home folder on a different partition, carrying over to a new install, still have those problems?

---

### Post by handydan918 on 2008-12-05
Definitely. The only thing better might be a separate data partition with a symlink from /home....but that's a whole 'nuther discussion.

---

### Post by DBrocks on 2008-12-05
Out of curiosity, how does one go about making a seprate data partition?

---

### Post by nhasian on 2008-12-05
you can easily setup a /home partition during install.  the same place you make your / and swap partitions during setup.  what are you going to use that pc for?  its pretty low end and doesnt even have an DHMI output so wouldnt be very good for a HTPC...

> **DBrocks said:**
> Alright thanks alot guys. Im getting this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16883104035]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883104035") as a christmas present to myself. Wanted to see what you guys thought of a seperate /home partition.

---

### Post by aysiu on 2008-12-05
> **squeabs said:**
> Let's suppose you install something that screws up your ubuntu install, so you reinstall. Won't having the home folder on a different partition, carrying over to a new install, still have those problems?
No.

When you install programs, they install to /etc and /usr directories (possibly others as well).

Only your personal user settings for those programs are stored within /home

---

### Post by tahitiwibble on 2008-12-05
> **squeabs said:**
> Let's suppose you install something that screws up your ubuntu install, so you reinstall. Won't having the home folder on a different partition, carrying over to a new install, still have those problems?

> **handydan918 said:**
> Definitely. The only thing better might be a separate data partition with a symlink from /home....but that's a whole 'nuther discussion.

In other words your corrupted /home partition is going to screw up your fresh / installation? Is this correct?

---

### Post by sheishkabob on 2008-12-05
> **squeabs said:**
> Let's suppose you install something that screws up your ubuntu install, so you reinstall. Won't having the home folder on a different partition, carrying over to a new install, still have those problems?

Not likely. The most crashes come from elsewhere. In some situations, I suppose it's possible though.

---

### Post by Papa-san on 2008-12-06
I cannot even begin to tell you how much I would have lost without a separate /home partition. I am a writer, and have been doing all my work for two years now in Ubuntu. I work on several books at the same time, and cannot afford to lose anything. (I still save it to a jump-drive, but this is mostly because I can take it to write on other systems if necessary.)

I've had update manager enabled in the past, and lost about two months of data before I got wise because  the updates broke my system. So you will want to occasionally run an update manually after making a backup of your / partition. Now, even if my system does get trashed, I have everything saved on it's own partition. 

Additionally, I'd like to suggest that you pull the memory from your current system to add to your new one. I'm pretty sure your new motherboard has additional slots for it, and 512MB isn't really a lot. 

Either way, I wish you the best!

---

### Post by DBrocks on 2008-12-06
> **nhasian said:**
> you can easily setup a /home partition during install.  the same place you make your / and swap partitions during setup.  what are you going to use that pc for?  its pretty low end and doesnt even have an DHMI output so wouldnt be very good for a HTPC...

Because I need a personal computer. Been stuck with windows for too long. Have a CLI server, its time for a gui.

---

### Post by malacoda on 2008-12-24
> **DBrocks said:**
> Out of curiosity, how does one go about making a seprate data partition?

In a nutshell:  Pop in LiveCD, run QtParted, make a new partition.  If you're dual booting, you might want to make it a fat32 partition -- that way, you'll be able to access anything you save to it from both Linux and Windows.

I'd suggest doing a search for on the forum for How-To's or threads that describe the process in a bit more detail though because. while the steps above are all you need to create the partition, you may need to edit fstab in order for it to be automounted and accessible by Ubuntu (been a LONG time since I set mine up so I can't really remember the details of this).

---

### Post by kansasnoob on 2008-12-24
> **aysiu said:**
> It depends on your situation.

If you have a very small hard drive (my Eee PC, for example, has only 4 GB of total space), a separate /home partition is a very bad idea. I wouldn't put a separate /home on anything smaller than 30 GB.

When I had a bigger hard drive and used to keep a separate... partition of some kind, I quickly moved from having a separate /home partition to having a separate data partition. I actually wanted to do a fresh reinstall of every release and have it look fresh (no lingering old themes and settings).

But... if you have a very large hard drive and you actually want to keep your settings when you reinstall, a /home partition is definitely "worth it."

Excellent answer! I've done it both ways, but the thing is I'm downright paranoid about data loss!

In my defense it's not just a mental condition because I've lost data not only due to computer malfunctions but also fire, flood, and a vindictive ex-wife! So all important data is kept on external drives, in Tupperware, in my fire-proof gun safe!

And if it's super important copies are shared with family members on CD or DVD, or in some cases kept in my safe deposit box at the bank!

One thing I've found about having a separate /home is that "hidden" files can be hosed that need to be replaced upon re-installation, so reformatting /home may still be necessary.

---

