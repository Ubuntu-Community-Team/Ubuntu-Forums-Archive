---
title: "Increasing size of '/' partition"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by anohs on 2011-06-19
By mistake I  made '/' around 3GB and '/home' as 6GB. Now, if i am trying to install any new program, i am getting error. 'low disk space'.

I tried increasing the size of '/' using gparted. I tried dividing (resizing) '/home' partition, but i am unable to allocate to this newly created partition mount point as '/'

---

### Post by garvinrick4 on 2011-06-19
Make a screenshot or gparted and post it here using attachments paperclip.

---

### Post by Rex Bouwense on 2011-06-19
A quick search of the froums resulted in this:
[http://ubuntuforums.org/search.php?searchid=81611472](http://ubuntuforums.org/search.php?searchid=81611472)
It is a good place to start.

---

### Post by anohs on 2011-06-19
> **garvinrick4 said:**
> Make a screenshot or gparted and post it here using attachments paperclip.

I want to increase size of /dev/sda2. i have created a new partition /dev/sda6. will it be possible to 'merge' /sda2 with /sda6.

I am used Ubuntu from USB, while doing these operations

---

### Post by garvinrick4 on 2011-06-19
You can delete sda2 thru sda6 and make it all a extended partion and make one logical partition with whats inside the extended and save room to make a couple of gig swap.
Extended partition is just a house for logical partiitons where linux can survive comfortably. Looks like you have about 18 gig to work with. Can do this all in gparted then install.

---

### Post by anohs on 2011-06-19
> **garvinrick4 said:**
> You can delete sda2 thru sda6 and make it all a extended partion and make one logical partition with whats inside the extended and save room to make a couple of gig swap.
Extended partition is just a house for logical partiitons where linux can survive comfortably. Looks like you have about 18 gig to work with.

thanks. but I am bit new to ubuntu. can you please elaborate?? doesn't deleting sda2 to sda6 delete my entire ubuntu?? will i have to then re install ubuntu?

---

### Post by garvinrick4 on 2011-06-19
> thanks. but I am bit new to ubuntu. can you please elaborate?? doesn't  deleting sda2 to sda6 delete my entire ubuntu?? will i have to then re  install ubuntu?Yes it will, but you have just a portion of a install there anyway not being able to add
packages.
To install takes about 15 minutes or so then about 30 to 45 minutes to upgrade the install to a full install. Here is a good link to help you out with gparted and install:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

Here are some more gparted sites I had around to help you use:
Gparted sites
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/Ho...sAndPartitionshttps://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/Ho...sAndPartitionshttps://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by pqwoerituytrueiwoq on 2011-06-19
if you don't want to reinstall
you can shrink windows a bit more (however much you want to add to /)
apply after doing that
then move / to the left (may take 5-10 min)
then you can make / bigger
edit looks like you don't have much space i would delete swap (dont forget to remove the swap line form /etc/fstab)

---

### Post by -kg- on 2011-06-19
> **pqwoerituytrueiwoq said:**
> if you don't want to reinstall
you can shrink windows a bit more (however much you want to add to /)
apply after doing that
then move / to the left (may take 5-10 min)
then you can make / bigger
edit looks like you don't have much space i would delete swap (dont forget to remove the swap line form /etc/fstab)

He'd have a heck of a time shrinking sda1, what with all the data in it.  He only has 2 GB of free space...that's barely enough to be able to run Windows.  Now if you can transfer some of that data to an external or another internal drive...  Yes, deleting sda2 through sda6 would be the easy way to do it (what is sda6, anyway?), but it's also possible to preserve what you have.

In order to resize your root partition (sda2), you have to create room to expand it into ***_next to the partition_.***  In order to do this with your present partition scheme, you will need to do some resizing/moving.  You need to resize sda6 (or remove it, if it's not absolutely necessary)and move it to the end of the free space created.

You don't seem to have much room in your /home partition, so really you need to expand that a little bit, as well as move that as far as you can towards the end of the drive.  If you've removed sda6, that would be all the way to the right.  Then you'll need to resize sda4 (the Extended partition) down to transfer the free space from inside the Extended partition to the Primary space.

Once that's done, you will need to move sda3 (the Swap partition) all the way to the right.  That will give you free space into which you can increase the size of your sda2 partition.  For more information on partitioning operations read at the link in my signature block.

Or...you can back up all critical data to an external drive, delete all the partitions (except sda1, of course), ***(Hopefully!)*** store some of the data in sda1 somewhere and resize it to give you more space, then make another Ubuntu installation in that free space, this time with a better scheme.

pqwoerituytrueiwoq does have a point...you barely have enough room for a good Ubuntu installation, though it can be done in that small of space.  Myself, I'd spring for a second hard drive with plenty of room for everything and install Ubuntu on that.  You could always make part of the drive accessible by Windows (NTFS format)...like I said earlier, you barely have enough room in sda1 to run Windows efficiently.  It would be nice to transfer some of that somewhere where it is still accessible but not clogging up your OS partition.

---

