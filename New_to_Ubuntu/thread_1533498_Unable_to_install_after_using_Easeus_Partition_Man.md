---
title: "Unable to install after using Easeus Partition Manager"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by RoseRodent on 2010-07-18
Little background, I am fairly green to Ubuntu but not totally inexperienced. I have a friend who has been "helping" me, but I think his bodges have been leading me further and further from the path, and now I am in a mess. 

I had 9.04 and upgraded to 9.10 then 10.04 but discovered it was best for my needs to try to upgrade to GRUB2. In doing that I missed a step by accident and had the dreaded Error 15. My computer will not boot a Live CD so I fixed it (i.e. made the machine bootable somehow) by using "fix a broken system" on an alternate CD. This left me with a partition containing 24GB of blank space. So I asked my friend how can I get this blank space back again and he said I could tack it on to Windows by formatting it as a FAT drive. Next time I booted GRUB was unable to find any OS at all! Using the CD to keep putting GRUB back was taking another 20GB off my Windows partition each time and I was down to a very small usable partition and lots of partitions of blank space, so I decided not to do that. 

I have restored the Windows parition using Acronis True Image 2009, but was cross to find out this did not write over all the Linux partitions like I had asked it to. So now I decided I didn't really care if I lost Ubuntu at this stage, I'd just delete the info, resize the Windows partition to the full remaining size, then start again and install from a 9.10 disc (10.04 disc will not even work on alternate even though 10.04 is a working system once upgraded) and then I'd have GRUB2 from the start. 

Disaster! The guided resize says it is "unable to resize this partition because of an unknown reason, see virtual console 4 for details" - and I don't know what that means. So I made myself two partitions with Easeus, one for EXT3 and one for Swap, it said it was putting the main system in those, and then it started to say that the files on my CD were corrupted and it was unable to install them!! 

Back to when I said the Live CD will not boot, I actually got 9.10 live CD to boot up a couple of times but I did nothing at all, just viewed that it was working and shut it off. But now when I boot it up it is asking me for a username and password, and telling me that authentication fails when I put them in!! 

Can anyone help me to get this back to normal? I want my Windows partition to be all but about 40GB of the drive (250internal) and Ubuntu 10.04 in the remaining space. I am happy to do reinstalls from the image backup if that will help, but not reinstall from scratch of Windows because I only have the manufacturer hidden partition to go back to, which puts back on all manner of horrible programs, and I'd rather buy W7 and start all over again from a blank C:/ !!

---

### Post by odttopdf on 2010-07-18
> **RoseRodent said:**
> Little background, I am fairly green to Ubuntu but not totally inexperienced. I have a friend who has been "helping" me, but I think his bodges have been leading me further and further from the path, and now I am in a mess. 

I had 9.04 and upgraded to 9.10 then 10.04 but discovered it was best for my needs to try to upgrade to GRUB2. In doing that I missed a step by accident and had the dreaded Error 15. My computer will not boot a Live CD so I fixed it (i.e. made the machine bootable somehow) by using "fix a broken system" on an alternate CD. This left me with a partition containing 24GB of blank space. So I asked my friend how can I get this blank space back again and he said I could tack it on to Windows by formatting it as a FAT drive. Next time I booted GRUB was unable to find any OS at all! Using the CD to keep putting GRUB back was taking another 20GB off my Windows partition each time and I was down to a very small usable partition and lots of partitions of blank space, so I decided not to do that. 

I have restored the Windows parition using Acronis True Image 2009, but was cross to find out this did not write over all the Linux partitions like I had asked it to. So now I decided I didn't really care if I lost Ubuntu at this stage, I'd just delete the info, resize the Windows partition to the full remaining size, then start again and install from a 9.10 disc (10.04 disc will not even work on alternate even though 10.04 is a working system once upgraded) and then I'd have GRUB2 from the start. 

Disaster! The guided resize says it is "unable to resize this partition because of an unknown reason, see virtual console 4 for details" - and I don't know what that means. So I made myself two partitions with Easeus, one for EXT3 and one for Swap, it said it was putting the main system in those, and then it started to say that the files on my CD were corrupted and it was unable to install them!! 

Back to when I said the Live CD will not boot, I actually got 9.10 live CD to boot up a couple of times but I did nothing at all, just viewed that it was working and shut it off. But now when I boot it up it is asking me for a username and password, and telling me that authentication fails when I put them in!! 

Can anyone help me to get this back to normal? I want my Windows partition to be all but about 40GB of the drive (250internal) and Ubuntu 10.04 in the remaining space. I am happy to do reinstalls from the image backup if that will help, but not reinstall from scratch of Windows because I only have the manufacturer hidden partition to go back to, which puts back on all manner of horrible programs, and I'd rather buy W7 and start all over again from a blank C:/ !!

I would use a Boot CD to boot your computer and try using several Partition Tools to restore your Partition. Don't just rely on one software.

I would try Hiren's Boot CD, see here:
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

I've used it with my girlfriend's really messed up laptop and it did miracles.

---

### Post by Gone fishing on 2010-07-18
Hi it's a bit hard to follow where you are at the moment. However, if you create partitions in free space it is quite possible that you will brake your grub configuration as you may change the root partition.

I don't know Easeus and would suggest using an opensource Linux alternative my favorite is parted magic [http://partedmagic.com/](http://partedmagic.com/) it will have all the tools needed to fix your problem.

I would suggest booting on the parted magic CD mounting your Linux partitions saving every thing you need then deleting them.  Then using gparted (on parted magic) create the partitions you want one for root one for home one for swap leaving your Windows partition alone. Then rebooting and re-installing  ubuntu. If the live CD doesn't start make another it should work.
 
If you have a problem re-post

---

### Post by RoseRodent on 2010-07-18
Thanks, not entirely sure I understand... to make it clearer where I am at the moment, I have only Windows Vista 32bit and the manufacturer's hidden recovery partition on my disc just now. I do not currently have *any *copy of Ubuntu or other Linux because I deleted them when I was trying to get the Windows partition back to its potential size without all that dead space. I am not trying to get my GRUB to recognise the Linux, I am trying to put a whole brand new Linux installation on, using the Linux install to resize the partition in the normal way that the installation should do so, preferably using the guided partition option. But now that I have used the manual resize option it has upset Linux somewhat, so now I have Vista in 240-odd GB of the disc and hidden partition in 11.9GB of the disc and no Linux at all anywhere. Does that help? 

I am not trying to restore a partition that has anything at all in it, I am trying to make a brand new one with a new install, a new GRUB, everything from scratch, but it just will not work because it won't resize the partitions any more.

---

### Post by odttopdf on 2010-07-18
> **RoseRodent said:**
> But now that I have used the manual resize option it has upset Linux somewhat, so now I have Vista in 240-odd GB of the disc and hidden partition in 11.9GB of the disc and no Linux at all anywhere. Does that help? 

The Hiren's Boot CD has Linux Boot Features likewise. Just make a Boot CD of this Disc and use it to boot into Linux installation, you would be able to get Linux installed on your computer, it's really easy.

1) Get the Hiren's Boot CD
2) Boot your comptuer (the one you want to remove Windows and install Linux)
3) You would be able with the Boot CD to partition and get the computer to be clean for Linux installation
4) Install Linux

Just do it, you would see that it works.

---

### Post by RoseRodent on 2010-07-18
> **odttopdf said:**
> 
2) Boot your comptuer (the one you want to remove Windows and install Linux)


I don't want to remove Windows! :shock: That would be my worst nightmare. No, I want to resize windows down from 240GB to 190GB then install Linux in the leftover space.

Incidentally, I should point out that I have a devil of a job writing bootable discs. That is the main thing I use my Ubuntu for becuase it writes discs fine, but Windows is a disaster at writing discs. I got it with Nero already installed, and it's overridden all the Windows stuff but doesn't actually work. I can't fix it by removing Nero and I don't have a clean Windows. Solutions that do not involve writing bootable discs are preferable, though if it is the only way then I can probably do it, just have to invest about 2 hours and 10 disposable discs.

---

### Post by Gone fishing on 2010-07-18
Download parted magic - make the boot CD and then delete the partitions you don't want using gparted. If that doesn't work and I would be surprised we can look at plan B

---

### Post by RoseRodent on 2010-07-18
OK, downloading that one. I am on that special broadband service for people who live in the middle of nowhere (nosebleedingly expensive and slow as watching paint dry) 

But I don't have any partitions I don't want, so what do I do with it when I get it in order to make the Linux start working? I just have the recovery partition and the Windows partition, I want both of them, I just want the Windows partition smaller so I can put on Ubuntu. 

I'd really rather do it using guided partitioning if I can do something that will make that work, failing that I will need to make manual partitions to put Ubuntu into - what sort do I have to make and how exactly do I put Ubuntu in them? I followed some instructions yesterday saying use the larger one as / and EXT3 and the other as swap but not sure what precisely I am meant to be selecting from the menus, and whether primary or logical to make that work.

---

### Post by Gone fishing on 2010-07-18
The minimum no of partition you need is 2 root and swap I would go for 3 root home and swap.

Slow connections ahh I'm in the UK and its bliss at home in Lesotho US $ 300 per month for 1 meg.

---

### Post by RoseRodent on 2010-07-18
> **Gone fishing said:**
> The minimum no of partition you need is 2 root and swap I would go for 3 root home and swap.



Does this mean I must now use this separate partition manager to put these all on? Before I used Easeus I didn't have to create these things myself, I just put in the Ubuntu disc and it said how big do you want your Windows partition, it put Ubuntu in the rest of the space, I sat back and watched. I am after a process that will put my disk back to how it was so that I can do the Ubuntu install like that again. A sort of a partitioning "undo" 

> **Gone fishing said:**
> 
Slow connections ahh I'm in the UK and its bliss at home in Lesotho US $  300 per month for 1 meg.

I dream about 1meg...

---

### Post by Mark Phelps on 2010-07-18
Do NOT use the Ubuntu installer to shrink the Windows partition.  That could have been the start of all the trouble.  If you need to make space for Ubuntu, use the Vista Disk Management utility to shrink the Vista partition to make room for Ubuntu.  Then, boot into the Ubuntu CD and select the "largest free space" option and let Ubuntu do its own partitioning.

---

### Post by Gone fishing on 2010-07-18
Deleting the old Linux partitions using the live CD then opting to install Ubuntu into the largest Freespace would probably be the easiest (although I would go for having a home partition too). The installer will then create the root partition and the swap.

I guess you don't need to change the Windows ntfs partition if you do changing it from within Windows would probably be best.

---

### Post by candtalan on 2010-07-18
> **RoseRodent said:**
> But I don't have any partitions I don't want, so what do I do with it when I get it in order to make the Linux start working? I just have the recovery partition and the Windows partition, I want both of them, I just want the Windows partition smaller so I can put on Ubuntu. 


I have read that on some vista versions, third party partitioners have given trouble and it has been advised to manage the vista partitions from within vista itself, It has its own tools?

To 'normalise' things, what about using said vista tools whatever they are to reduce the partition size, making sure you leave the rest of the disk as unused, unpartitioned unformatted space. If the space is somehow giving trouble, maybe use gparted live cd to create a new partition in the space, apply, and in a subsequent process, use gparted to delete the empty partition leaving known 'good' empty space.

Then using a Ubuntu live CD to install a dual boot of ubuntu, notice the installer (partitioner stage) has an option for guided partitioning 
 'use the largest unused space on the drive' 
note this has to be a space which is not partitioned, that is it does NOT mean an empty partition.

I use this option a lot it is a useful way to get ubuntu into a slot.

hth

---

### Post by RoseRodent on 2010-07-18
> **Mark Phelps said:**
> Do NOT use the Ubuntu installer to shrink the Windows partition.  That could have been the start of all the trouble.  If you need to make space for Ubuntu, use the Vista Disk Management utility to shrink the Vista partition to make room for Ubuntu.  Then, boot into the Ubuntu CD and select the "largest free space" option and let Ubuntu do its own partitioning.


I have to say I never had a problem installing using Ubuntu installer to shrink Windows, not until I used this Easeus thing... OK, problem now is that I have never seen an option for "largest free space" - remember I can only use alternate CD, I am usually offered guided partitioning - shrink existing partition and install Ubuntu in remaining space (sic - it goes off the edge of the screen), guided - use entire disk, guided - use entire disk and set up LVM and Manual. 

I have seen the "use the largest continuous free space" on the Live CD edition screenshots, but my live CD does not work. What might it want me to put in as username and password from a live CD? There is no Ubuntu install on this whole computer and in any case neither the network ID nor user that I normally use is recognised, they both say "Authentication failure" so I cannot use the live CD unless I can get around this problem of it asking me to match a username and password. 

Either: A: How can I get into the Live CD version? or B: How do I get this use largest free space option via the alternate install CD?

> **candtalan said:**
> 
note this has to be a space which is not partitioned, that is it does  NOT mean an empty partition.




OK, so when I look in Vista tools should it be green and referred to as  "free space" ? There is also an option for "Unallocated" but no idea how  to turn it into that. Is green the right thing?

---

### Post by Gone fishing on 2010-07-19
You could do it the way I suggested using a live gparted CD like parted magic and make the partitions before running the installer. It may be best to shrink the Windows partition in Windows first. See screen shot (taken from my daughters netbook running Mint)

If you wish to use the use largest freespace option and this is only available on the live CD which for some reason wont work on your computer is is possible to make a bootable flash disk installer using start up disk creator?

---

### Post by RoseRodent on 2010-07-19
Since I already have the partition via Vista I'd like to know if "green" is the correct variety of space to run the installer rather than play around with any more partitioning unnecessarily. I can have another go at the live CD I just have no idea what it wants me to put in as an ID and password! I can only imagine I'd have the same problem with booting it from USB if I am booting the same thing. I am hesitating on how much effort to throw at this just now because I am waiting for a Windows 7 CD to come and will just write over everything anyway. Maybe it's a good time to play with the system since it doesn't matter if I break it, though.

---

### Post by Elfy on 2010-07-19
If you had problems with the livecd in the past and it's now asking for the username and password I would be inclined to check the integrity of the cd at the cd's boot menu.

---

### Post by RoseRodent on 2010-07-19
> **forestpiskie said:**
> If you had problems with the livecd in the past and it's now asking for the username and password I would be inclined to check the integrity of the cd at the cd's boot menu.

Pardon my innocence, but that would mean doing what exactly?

---

### Post by RoseRodent on 2010-07-22
Thanks for your help, I hope I have done the right thing to mark the thread as solved. The problem has not exactly gone away, so if someone else is searching the forums they would find it not solved, but for my own purposes it is solved because I now started booting from an external drive so I don't have to do anything with partitions, and also means I can put my SecureZone back on, which I like to have. 

Thanks all.

---

