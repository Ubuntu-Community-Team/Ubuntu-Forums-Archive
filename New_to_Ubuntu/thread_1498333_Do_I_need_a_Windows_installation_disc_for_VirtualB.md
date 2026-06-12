---
title: "Do I need a Windows installation disc for VirtualBox?"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-05-31
or an .iso For creating a partition for windows, I want to test some things out. I'm also using it to try out different distros.

---

### Post by halitech on 2010-05-31
you will only need a windows iso or disk if you are installing windows. If you arent installing windows then you don't need a windows disk or iso

---

### Post by Legendary_Bibo on 2010-05-31
They should really put that notice on the first page when they let you select the Windows installation.

---

### Post by halitech on 2010-05-31
Did you think they would provide the iso in order to do an install for every OS they support?

---

### Post by Legendary_Bibo on 2010-05-31
> **halitech said:**
> Did you think they would provide the iso in order to do an install for every OS they support?

It would have been nice :D Yeah before creating a partition I figured I should double check.

---

### Post by halitech on 2010-05-31
your download would have been a few gigs in size in order for them to provide the isos, not to mention copyright issues with Microsoft for providing the isos without their permission.

---

### Post by CharlesA on 2010-05-31
Just use gparted to create partitions.

---

### Post by cgroza on 2010-05-31
You need the cd or the iso... for virtualbox is the same thing.

---

### Post by Legendary_Bibo on 2010-05-31
> **halitech said:**
> your download would have been a few gigs in size in order for them to provide the isos, not to mention copyright issues with Microsoft for providing the isos without their permission.

good point :popcorn:

---

### Post by halitech on 2010-05-31
> **Legendary_Bibo said:**
> It would have been nice :D Yeah before creating a partition I figured I should double check.

wait a minute, you don't need partitions to install an OS using virtual box. Everything is in virtual drives which are just files and folders in your home folder.

---

### Post by wilee-nilee on 2010-05-31
> **halitech said:**
> wait a minute, you don't need partitions to install an OS using virtual box. Everything is in virtual drives which are just files and folders in your home folder.

This is correct to some extent, but if you want to install a specialized distro such as arch which is part of creating multiple partitions in the Vbox you have to partition. Personally I just let it install like a standard install, it is pretty straight forward. They are files but there are virtual partitions.

---

### Post by halitech on 2010-05-31
> **wilee-nilee said:**
> This is correct to some extent, but if you want to install a specialized distro such as arch which is part of creating multiple partitions in the Vbox you have to partition. Personally I just let it install like a standard install, it is pretty straight forward. They are files but there are virtual partitions.

okay but you would still start with a blank virtual drive and each virtual machine would have separate drives. Not like you would need to partition the actual hard drive to install the virtual OSes.

---

### Post by wilee-nilee on 2010-05-31
> **halitech said:**
> okay but you would still start with a blank virtual drive and each virtual machine would have separate drives. Not like you would need to partition the actual hard drive to install the virtual OSes.

Try installing arch to a virtual you will be partitioning manually. It is the nature of that distro, as I said the standard install will do this for you in XP and many other distro's. I'm not trying to argue with you it is just that it is more then just a file, after you have installed something into it. I think this is a matter of technicalities in the description. And there are very good instructions provided with Vbox if a person has troubles and this forum and a Vbox forum for help.

You have to do some of the hard work yourself rather then rely on scattered information on a forum, if you want to actually understand how it works.

---

### Post by halitech on 2010-05-31
I'm not disagreeing with you on the manual partitioning required by arch but the partitioning will still be done on a virtual drive, not the physical drive where he has his host OS installed.

---

### Post by wilee-nilee on 2010-05-31
> **halitech said:**
> I'm not disagreeing with you on the manual partitioning required by arch but the partitioning will still be done on a virtual drive, not the physical drive where he has his host OS installed.

A virtual drive on the HD where the OS resides, and is any of this really helping the OP I have to ask. You can respond if you need to but I think your not recognizing the wording your using is inaccurate. Hey I'm not taking the English majors clause as even on a good day my grammar is suspect at best. ;)

---

### Post by kelvin spratt on 2010-05-31
when you install Arch in vbox you can use auto prepare to partition the same as you can with any distro. To install windows you need a install disc, not a upgrade disc, nor a recovery disc,.

---

### Post by wilee-nilee on 2010-05-31
> **kelvin spratt said:**
> when you install Arch in vbox you can use auto prepare to partition the same as you can with any distro. To install windows you need a install disc, not a upgrade disc, nor a recovery disc,.

Yes but you have to choose the sizes of the partitions within the limitations that have been set to the size of the Vbox setup for that install. It will not just automatically install, in the same way other distros' do hands off.

---

### Post by sdennie on 2010-05-31
The answer to the original question is, yes, you will need a Windows CD to install Windows in VirtualBox.

I think the clarification to the slightly bizarre discussion that followed is 1) You don't have to re-partition your hard drive to use virtual box because it presents a single file as a virtual disk to the VM.  2) Within a virtual disk created by virtualbox, some operating systems required manual partitioning.

---

