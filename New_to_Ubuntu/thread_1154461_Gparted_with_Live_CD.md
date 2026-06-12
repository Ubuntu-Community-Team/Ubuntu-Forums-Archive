---
title: "Gparted with Live CD"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by hungryOrb on 2009-05-09
Hi all,
Trying to shrink a defragged NTFS from roughly 70gb, to 30-40. But Gparted is having none of it, and spits this at me. (see screen)

Any tips? :O
TFC
Orb

---

### Post by Didius Falco on 2009-05-09
Please do another screen shot with the main Gparted window showing.

Regards,

Didius

---

### Post by hungryOrb on 2009-05-09
Thanks for reply Didius, please may I ask you to check the post in half a day? I'm landed with a ton of stuff :( but will get another ss asap!
TFC..!
Orb

---

### Post by -kg- on 2009-05-09
That is indeed strange, especially with a GPartEd Live CD.  I've never had this kind of problem with it.

I'm posting this so I can keep track of this thread to see what the outcome is, and to help if I can.

---

### Post by hungryOrb on 2009-05-10
Hi again :]

Here are some more screens surrounding my procedure.
And some info:

The NTFS partition is entirely **Windoze XP**. It's been defragmented twice, but the log reported that small sections couldn't be defrag'd. I couldn't understand why.. Would a screenshot of that be helpful?

---

### Post by hungryOrb on 2009-05-10
..a last screenshot for the set:

Ubuntu and Live CD are so cool :O!

---

### Post by -kg- on 2009-05-10
OK, I'm not sure what's going on, but according to your screen shots, you're not violating the "4 Primary partition" rule.  Here is what I want you to do.

First, are you trying to do this from GPartEd in your installation, or from the Live CD (either Ubuntu or the GPartEd Live CD)?  You want to do this from a Live CD (preferably the [GPartEd Live CD]("http://gparted.sourceforge.net/"), but the Ubuntu Live CD will do).

I notice that, in the last screen shot, you have 2 partitioning operations that you are set to apply; the shrinking operation and creating operation.  Cancel this, shrink the ntfs partition, and apply this operation.

Then delete the swap partition and apply this operation.  Once you have deleted the swap partition, move the ntfs partition over into the space freed and apply that operation.

Then select the free space and create an Extended partition that encompasses that free space.  Apply this operation.  Once the Extended partition is created, re-create the swap partition inside the Extended partition at the end of the space as a Logical partition at around the same size.  Apply this operation.

Once this is done, *then* try creating your extra ntfs partition in the remaining free space in the Extended partition as a Logical partition.

I seriously don't understand why you can't do what you're trying to do, but I would think that what I've told you should enable you to create your extra ntfs partition.  For extra information on partitioning operations and conventions, read the following page:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by Hobgoblin on 2009-05-10
I suspect something which can't be moved, such as Windows swap file is preventing the resize.

---

### Post by kansasnoob on 2009-05-10
You are working from a live CD, eh?

If so right click the SWAP partition and choose to SWAPOFF!

---

### Post by Didius Falco on 2009-05-10
> **Hobgoblin said:**
> I suspect something which can't be moved, such as Windows swap file is preventing the resize.

That sounds like a distinct possibility. It's easy to check - boot into Windows and set it to no swap file. I think, were it I, I'd reboot into Windows again, which will clear any remnants of the swap file, and defrag it again. If it's already pretty unfragmented, it won't take long.

Then you can go on with your partition management.

---

### Post by gfk on 2009-05-10
Try scanning the ntfs partition for errors.

---

### Post by hungryOrb on 2009-05-10
> **-kg- said:**
> OK, I'm not sure what's going on, but according to your screen shots, you're not violating the "4 Primary partition" rule.  Here is what I want you to do.

First, are you trying to do this from GPartEd in your installation, or from the Live CD (either Ubuntu or the GPartEd Live CD)?  You want to do this from a Live CD (preferably the [GPartEd Live CD]("http://gparted.sourceforge.net/"), but the Ubuntu Live CD will do).

I notice that, in the last screen shot, you have 2 partitioning operations that you are set to apply; the shrinking operation and creating operation.  Cancel this, shrink the ntfs partition, and apply this operation.

Then delete the swap partition and apply this operation.  Once you have deleted the swap partition, move the ntfs partition over into the space freed and apply that operation.

Then select the free space and create an Extended partition that encompasses that free space.  Apply this operation.  Once the Extended partition is created, re-create the swap partition inside the Extended partition at the end of the space as a Logical partition at around the same size.  Apply this operation.

Once this is done, *then* try creating your extra ntfs partition in the remaining free space in the Extended partition as a Logical partition.

I seriously don't understand why you can't do what you're trying to do, but I would think that what I've told you should enable you to create your extra ntfs partition.  For extra information on partitioning operations and conventions, read the following page:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

Thanks for all comments and suggestions! Much appreciation..!
Ubuntu Live CD yeah.. 8.04. 

I'll try those! :D

---

### Post by hungryOrb on 2009-05-10
> **Didius Falco said:**
> That sounds like a distinct possibility. It's easy to check - boot into Windows and set it to no swap file. I think, were it I, I'd reboot into Windows again, which will clear any remnants of the swap file, and defrag it again. If it's already pretty unfragmented, it won't take long.

Then you can go on with your partition management.

Man, can I ask, how do you turn off the swap in windows? :O
Is it cool to just erase my linux swap for now?

---

### Post by Elfy on 2009-05-10
I've erased swap before now - bear in mind that when you boot it will complain that it can't be found. Even if you recreate a swap before you boot, it will still be looking for the old one. Use a cli editor at recovery mode to edit fstab or do so from the livecd.

To get rid of the win pagefile - you used to right click computer - properties - advanced (I think) - one of the tabs there gets you to the pagefile - you can remove it there.

---

### Post by hungryOrb on 2009-05-10
Thanks ForestPixie :)

Edit: KG, latest is that I simply cannot do the simple step of shrinking the NTFS. Tried with Swapoff, and Windows pagefile set to none. I'm having a mess and i'll keep the thread updated. :)

---

### Post by gfk on 2009-05-22
Try using SDelete to zero all the free space on your NTFS partition.

[http://technet.microsoft.com/en-us/sysinternals/bb897443.aspx](http://technet.microsoft.com/en-us/sysinternals/bb897443.aspx)

Hopefully then you will be able to resize you partition.

---

