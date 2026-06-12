---
title: "advantage in putting /home on primary rather than logical"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by jimmy the saint on 2009-03-27
I intend to give /home its own partition on a new system.  Is there any advantage to putting /home on a primary partition as opposed to a logical one?

Thanks for any input

---

### Post by Locutus_of_Borg on 2009-03-27
been using logical for /home for the last year

no problems here

also have my / on a logical volume these days

---

### Post by doas777 on 2009-03-27
overall, i avoid extended partitions and logical volumes. they sometimes cause problems when installing OS's or altering partitions. it's rare, but I just started aboiding them a decade ago and haven't regreted it yet.

---

### Post by jimmy the saint on 2009-03-27
@doas777

That is my concern.  What issues have you seen?  My concern is that, since they are all grouped together, an issue on one partition can mess up the others as well.  I have no idea if that is a real concern, or just based on a lack of understanding of the nature of extended/logical partitions though.

---

### Post by Locutus_of_Borg on 2009-03-27
well ideally i too would avoid extended partitions, but i needed more than four for what i wanted to do on this computer

---

### Post by lovinglinux on 2009-03-27
> **doas777 said:**
> overall, i avoid extended partitions and logical volumes. They sometimes cause problems when installing os's or altering partitions. It's rare, but i just started aboiding them a decade ago and haven't regreted it yet.

+1

---

### Post by doas777 on 2009-03-28
> **jimmy the saint said:**
> @doas777

That is my concern.  What issues have you seen?  My concern is that, since they are all grouped together, an issue on one partition can mess up the others as well.  I have no idea if that is a real concern, or just based on a lack of understanding of the nature of extended/logical partitions though.

well the big problem is that you can't have an extended partition without a primary on the drive. In past i've removed the primary and the extended went with it. some os installers react badly to existing extended partitions, and will wipe the drive rather than just formatting the section i want to overwrite.

you also can't set a logical drive as active, so if you need to move your system partition, you won't be able to move it to a volume within an extended.

your specific concern is valid albeit uncommon. It's been many years since i saw a partition table eat itself, but it can happen, and in that case, yes there is a risk to all your extended drives. this same risk applies to primarys, but should only affect that one partition.

please note, the above is just an amalgam of many frustrating experiences. I'm not sure if it is technically supposed to work that way, I've just seen these problems with one OS or another.

good luck,
franklin

---

### Post by doas777 on 2009-03-28
> **Locutus_of_Borg said:**
> well ideally i too would avoid extended partitions, but i needed more than four for what i wanted to do on this computer

you have just hit on the only really good reason for using extended partitions. if you really need more than 4 partitions on the same drive, then you don;t have much choice. 

just be careful with your data next time you put an os installer in your PC or open the partitioner.

---

### Post by jimmy the saint on 2009-03-28
The only reason I need one (or use one anyway) is because of a vista dual boot.  I hate to do it, but I'm playing with a new blackberry and barry just isn't there yet, as it cannot upgrade the os.  I have vista at the beginning of the drive (I couldn't even load it with a boot partition at the beginning because it just HAS to be first) which means the extended partiton has to hold /boot, /, /home and swap partitions.  

Thanks for the input.  I just wish it was easier to copy the home directory.  For some reason there were a lot of hidden symlinks and even though the partition was only 2 Gigs full, it kept trying to tranfer 30+ Gigs.  oh well, nothing is ever as easy as it should be!

---

### Post by ranch hand on 2009-03-28
I, personally, do not like primary partitions at all.

I use cfdisk and creat 1 extended partition on my drives and then one swap logical at the end of that.

I use gparted for other partitioning but this way I have on primary  and can creat and delete partitions on my whim.  I like to play and use 320G drives.  I can have several installations this way.

When I gat hooked on this Ubuntu stuff I screwed my system fatally several times before thinking that if I had 2 I would be able to play with one and actually use the other.  This works for me.

I also like to have a separate home partition and a root.  With a Swap partition this makes a minimum of 5 with 2 installations.  I also like to have some small instalations of other flavors of linux.

This has not caused me any problems at all.

---

### Post by CatKiller on 2009-03-29
> **doas777 said:**
> well the big problem is that you can't have an extended partition without a primary on the drive. In past i've removed the primary and the extended went with it. some os installers react badly to existing extended partitions, and will wipe the drive rather than just formatting the section i want to overwrite.

I think you've got that backwards. An extended partition **is** a primary partition. You can have one extended partition and three other primary partitions. The extended partition is a container for the logical drives that you create inside it, as a means to overcome the 4 partition limit. Deleting the extended partition will necessarily remove the logical drives that you've created. If you throw a box away, you also throw away what's inside it.

There's no argument that the Windows installer is crap, but that's no reason to avoid a perfectly valid configuration for your Ubuntu install.

To the OP: There's not really much to sway it either way. If your partitioning scheme means that you need more than 4 partitions, then you're going to have to put some of them in an extended partition. If you aren't, then you might as well use primary partitions, since a new OS install, or re-partitioning, will necessarily mean that you'll be shuffling partitions around anyway, and you can re-evaluate whether you need an extended partition then. If you're at four partitions then it might be worth putting one in an extended partition so that if, in the future, you decide you need another partition then you don't have the problem that you can't create an extended partition because you've already got your four primary partitions.

---

