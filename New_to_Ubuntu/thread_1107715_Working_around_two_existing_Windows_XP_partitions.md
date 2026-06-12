---
title: "Working around two existing Windows XP partitions"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by span237 on 2009-03-27
I've only just started using Ubuntu as a part of a uni course, and have managed to successfully install it on an old laptop.

My Dad is also interested in learning how to use it, however wants to install Ubuntu in a way that I am not sure is possible.

His hard disk has 3 partitions as follows:

C: NTFS 24.4GB XP PRO PRIMARY ACTIVE

EXTENDED:
D: NTFS 19.5GB XP HOME LOGICAL NOT ACTIVE
E: NTFS 30.5GB XP PRO LOGICAL NOT ACTIVE

He wants to install Ubuntu on the 24.4GB of the C: drive, without affecting/disturbing the other two logical XP installations.

My partitioning knowledge/experience is very limited (I've been reading threads/sites for the last two hrs trying to improve my understanding).

What I'm not sure about is:
[LIST]
[*]is it possible to have Ubuntu on the first (currently C: ) partition and still have the other two logical XP partitions functional and accessible?
[*]do we need to make one of the logical partitions primary and/or active before we wipe the C: drive?
[*]if we get to the stage where we can continue, should we re-format the C: drive or delete it ? (i assume this will return it to unallocated space where i could then reallocate it)
[/LIST]

I realise these are very simple questions to some. Please excuse my noobiness.

Thanks :)

---

### Post by jakupl on 2009-03-27
well, I would just pop in the live cd, and create a fourth partition. But if he wants to install it on the C: drive, than use wubi. That is - insert the cd while on windows, and then install from there. I am not that familiar with wubi, but as far as I know, it will become a single file inside windows which is easily removable.

check this for additional information: [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by theozzlives on 2009-03-27
> **jakupl said:**
> well, I would just pop in the live cd, and create a fourth partition. But if he wants to install it on the C: drive, than use wubi. That is - insert the cd while on windows, and then install from there. I am not that familiar with wubi, but as far as I know, it will become a single file inside windows which is easily removable.

check this for additional information: [http://wubi-installer.org/](http://wubi-installer.org/)

One word, WUBI.

---

### Post by span237 on 2009-03-27
Thanks for the quick replies.

I was thinking more along the lines of completely removing Windows from the partition, but I'll give Wubi a go.

---

### Post by stderr on 2009-03-27
Wubi is incredibly easy, but it won't perform quite as well as a pure installation. If he's looking to format the C partition and install Ubuntu, that should be fine. Just ensure you don't make any mistakes when choosing which partitions to format, and go and format one of his other Windows partitions!

It will install the GRUB boot loader by default, which should recognise the 2 other Winblows installations and add them as options in the boot menu. 

Shouldn't need to set any other partiton as active first. Let the GRUB boot laoder install to the same primary partition as Ubuntu, and that should be fine.

---

### Post by mlentink on 2009-03-27
Before you run off: does your father want to retain windows? Because afaik running windows from an extended partition is problematic.

So my 2 cts:
- running ubuntu through a Wubi install is feasible. I sincerely doubt very much wether you would be able to notice a performance hit by running on a virtual partition rather than a real physical one
- Your father's pc seems to have only one primary partition. Two more should be no problem, provided he has enough disk space left. Would he be prepared to shrink the extended partitions by a large enough amount?

---

### Post by span237 on 2009-03-27
Thanks stderr and mlentink for your help.

mlentink, yes he still wants to retain the other two Windows partitions. I'm also not sure how much free space he's got left on the logical paritions, but I don't think there is much.

I've searched a bit about booting XP from logical partitions and found [this post]("http://ubuntuforums.org/showthread.php?p=4701367#post4701367") by Herman and [this one]("http://ubuntuforums.org/showthread.php?t=813628") by meierfra describing how to fix the loss of the required boot files from the primary windows partition.

Should I expect to have to do this fix? 

Will the fact that there are 2 XP installations on logical partitions make things considerably more difficult?

---

### Post by mlentink on 2009-03-27
Seems to me Herman and meierfra know more about it than I do, but yes, you will definitely have to follow their guides. Pay special attention to the GRUB 'hiding' and 'unhiding' of windows partitions. This I have never done, so I should not be your guide on this.

---

### Post by stderr on 2009-03-27
> **span237 said:**
> Thanks stderr and mlentink for your help.

mlentink, yes he still wants to retain the other two Windows partitions. I'm also not sure how much free space he's got left on the logical paritions, but I don't think there is much.

I've searched a bit about booting XP from logical partitions and found [this post]("http://ubuntuforums.org/showthread.php?p=4701367#post4701367") by Herman and [this one]("http://ubuntuforums.org/showthread.php?t=813628") by meierfra describing how to fix the loss of the required boot files from the primary windows partition.

Should I expect to have to do this fix? 

Will the fact that there are 2 XP installations on logical partitions make things considerably more difficult?

I don't think so. You already have 2 copies of XP installed. They're both fine. So, if you format C partition, you no longer have an active partition, so you can't boot Windows. Then you install Ubuntu to the correct partition, which will also install GRUB boot loader.This should detect both Windows OSs and add relevant boot entries. Your C partition with Ubuntu & GRUB would be the active partition.

I don't really see the relevance of the posts you're looking at, as they are featuring NTLDR corruption etc. This is when you install Windows, and then install another older Windows to another partition, and it rips out some necessary files. And it doesn't matter that your Windows partitions will no longer be active, since your GRUB partition is active.

As for hiding and unhiding Windows' partitions, again, nope, I don't see the point. You only boot one Windows partition at a time! and they don't conflict once booted. Since you're only installing Linux & GRUB, those partitions shouldn't be edited anyway by the installation process, so as far as I can see there's no need to hide/unhide. That's surely when you're installing multiple copies of Windows... but personally, I'd usually just replace the files anyway instead of using that hide/unhide technique. 

Like I say, I would expect the process to work fine. I don't think much special preparation is needed.

---

### Post by mlentink on 2009-03-27
I beg to differ
> **stderr said:**
> I don't think so. You already have 2 copies of XP installed. They're both fine.
Sure they are, as long as that one primary Windows partition with its boot flag exists.
> **stderr said:**
>  So, if you format C partition, you no longer have an active partition, so you can't boot Windows. Then you install Ubuntu to the correct partition, which will also install GRUB boot loader.This should detect both Windows OSs and add relevant boot entries. Your C partition with Ubuntu & GRUB would be the active partition.
 
True. Ubuntu will do this fine. But as far as I know, Windows will not. Please correct me if I'm wrong, but you seem to overlook the significance of two windows installs in ***logical ***partitions, of equal precedence, with their own bootloaders.

---

### Post by span237 on 2009-03-27
Thanks guys, it's great to get a couple of opinions on the matter. 

I take this info and explain it to my dad.

I think i'll suggest he tries Wubi first on the primary partion, and then a proper install over XP on the primary partition.

---

