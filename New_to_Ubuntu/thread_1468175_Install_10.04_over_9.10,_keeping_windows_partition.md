---
title: "Install 10.04 over 9.10, keeping windows partition"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by MorrisseyJ on 2010-05-01
Hi, I am sorry if this is a repeated question. It seems both obvious and common but i am unable to find an answer on here.

I am currently using Ubuntu 9.10 on a hard drive partitioned so that i can dual boot with Windows. I now want to upgrade to 10.04, replacing the 9.10 install with 10.04 but leaving the windows partition alone. When i go to install 10.04 off the live CD i see that the installer wants to make a new partition putting 10.04 along side 9.10. 

I am trying to do a clean install because everyone seems to think its better.

When i first installed 9.10 i made the partition and installed into the empty space. Now i am trying to install 10.04 over 9.10 and i don't know how. The only overwrite option i seem to have pertains to overwriting the entire hard drive. 

Should i first have formatted the partition on which 9.10 is currently sitting, and if so how should i go about that?

If anyone can answer how i install 10.04,replacing 9.10 but keeping windows where it is, i would be very grateful. Otherwise directions to a detailed tutorial would also be appreciated. 

Thanks in advance.

p.s. step by step instructions would be appreciated as i get nervous when setting these things up.

---

### Post by mikewhatever on 2010-05-01
> **MorrisseyJ said:**
> Hi, I am sorry if this is a repeated question. It seems both obvious and common but i am unable to find an answer on here.

I am currently using Ubuntu 9.10 on a hard drive partitioned so that i can dual boot with Windows. I now want to upgrade to 10.04, replacing the 9.10 install with 10.04 but leaving the windows partition alone. When i go to install 10.04 off the live CD i see that the installer wants to make a new partition putting 10.04 along side 9.10. 

Ubuntu live cd is not the way to upgrade. Use System->Admin->Update Manager instead.

> I am trying to do a clean install because everyone seems to think its better.

Someone's having a personality split. Hope it's not me.:P

> When i first installed 9.10 i made the partition and installed into the empty space. Now i am trying to install 10.04 over 9.10 and i don't know how. The only overwrite option i seem to have pertains to overwriting the entire hard drive. 

Should i first have formatted the partition on which 9.10 is currently sitting, and if so how should i go about that?

If anyone can answer how i install 10.04,replacing 9.10 but keeping windows where it is, i would be very grateful. Otherwise directions to a detailed tutorial would also be appreciated. 

Thanks in advance.

p.s. step by step instructions would be appreciated as i get nervous when setting these things up.

You have to select the Manual/Advanced option, and specify the Ubuntu partition by selecting the '/' mount point for it. To do that, right click the Ubuntu partition, select 'Edit', then select the required parameters, most importantly the mount point.

---

### Post by MorrisseyJ on 2010-05-01
Thanks for the info but not all of what you said seems to work, 

When i go to the advanced/manual tab i can see the four partitions that i have on the hard drive. Two are for windows, and two are for Linux. 

When i right click on one of the linux partitions there is no 'edit' option, only 'change', 'delete' and 'revert'.

I presume that you need me to click 'change', but this just offers me the chance to change the size of the partition, which is not what i want to do (is it?).

Am i doing what you had in mind. 

One other thing, could i not just delete the two existing Linux partitions and then do the automatic install into the free space?

---

### Post by Paqman on 2010-05-01
> **MorrisseyJ said:**
> 
Now i am trying to install 10.04 over 9.10 and i don't know how. 

Use Manual Partitioning, and pick the old 9.10 root partition as the root partition for 10.04, and make sure it's checked to be formatted. If you use a seperate /home partition, select the right partition and make the mount point /home, but _do not_ format it.

> **MorrisseyJ said:**
> 
One other thing, could i not just delete the two existing Linux partitions and then do the automatic install into the free space?

Yep, absolutely.

---

### Post by MorrisseyJ on 2010-05-01
Ok, i am still not sure about this. 

Under the manual/advanced tab i have three options: 'change', 'delete' and 'revert'. I appear unable to check the format box in any partition.

When i try and delete the partitions and then use the auto-install it doesn't work. It always just gives about 27mb of space back to 9.10, even after i have deleted it. This leaves me with less than half the space that i want for 10.04. This makes no sense to me.

So now i am trying the manual install.

I have freed up all the space so that i now have two windows (fat32) partitions (/dev/sda1 and /dev/sda2). I have a swap partition (/dev/sda5) for linux (swap). In the rest of the space ('freespace') i want to put 10.04. This swap partition appears to be a hangover from the previous 9.10 install. 

Do i need to delete and recreate the swap partition or will the system know to use the one that is there already?

On the free space partition the 'add' button lights up and i can also 'revert'. When i click 'add' it takes me to a 'create partition' screen. However I don't think that i want to do this a i now have  all the partitions i want, i just want to fill the free space with  10.04.

The screen won't let me click forward because i have not yet defined a root file system.

So, with the buttons at hand, how do i 

> pick the old 9.10 root partition as the root partition for 10.04

If i need to 'create a partition' can you tell me if these specs are correct:

Type of new partition: Logical
Location for new partition: beginning 
Use as: Ext4 journaling file system
Mount point: /home

I don't think i know whether i have a  

> use a seperate /home partition

---

### Post by sid90 on 2010-05-01
for people with slow internet connections,it ll take 5 hours to upgrade to 10.04 from 9.10...so is there any there way to upgrade?I mean through a Live CD...:confused:..

---

### Post by MorrisseyJ on 2010-05-01
> for people with slow internet connections,it ll take 5 hours to upgrade  to 10.04 from 9.10...so is there any there way to upgrade?I mean through  a Live CD

Thats what i am trying to do through a clean install.

---

### Post by crjackson on 2010-05-01
> **MorrisseyJ said:**
> One other thing, could i not just delete the two existing Linux partitions and then do the automatic install into the free space?

That's exactly how I do it every time.  This ensures you get a new grub installed properly.

---

### Post by MorrisseyJ on 2010-05-01
> Quote:
 	 	 		 			 				 					Originally Posted by **MorrisseyJ** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9209905#post9209905") 				
 				*One other thing, could i not just  delete the two existing Linux partitions and then do the automatic  install into the free space?*
 			 		 	 	 
That's exactly how I do it every time.  This ensures you get a new  grub installed properly. 	

Problem is the partitions don't seem to delete. Should i be deleting them in GParted. If so, is there a way that i can access GParted through the live CD. At the moment it won't let me because i don't have root privileges.

---

### Post by SwatKat on 2010-05-01
> **MorrisseyJ said:**
> 
I have freed up all the space so that i now have two windows (fat32) partitions (/dev/sda1 and /dev/sda2). I have a swap partition (/dev/sda5) for linux (swap). In the rest of the space ('freespace') i want to put 10.04. This swap partition appears to be a hangover from the previous 9.10 install. 

Okay, lets start from here. Boot into lucid using the live cd and open gparted ( system -> administration -> gparted). Your unallocated 'freespace' should appear in gray if you have deleted the partition which contained 9.10 . 
Right click on this unallocated space -> New. You can change the size of the partition ( which I guess you dont want) and change the type of filesystem to ext3 or ext4. Then click apply(the green check mark). This should create a new logical partition in which you can install 10.04. Note down the name of the partition.( Probably  dev/sda6)

> **MorrisseyJ said:**
> Do i need to delete and recreate the swap partition or will the system know to use the one that is there already?
You dont need to do anything. Lucid will recognize the swap partition.

Now you can install Lucid from the install icon on the desktop. When you get to the '**Prepare disk space**' part, choose** 'specify partitions manually(advanced)' **and go forward**.**

Here you'll get a list of partitions on you hard disk. Now choose to '**change **' the partition you just created and set the mount point as / and continue with the installation. 

If you want a separate home partition, create 2 partitions instead of 1 in the free space you have using gparted as explained above before installing , and mount one of the partitions as / and the other as /home.  The /home partition can be ext3 or 4 .  Just keep it bigger than the / partition ( Which normally doesnt need more than 10 gigs)

Good luck!

---

### Post by sadaruwan12 on 2010-05-01
> **crjackson said:**
> That's exactly how I do it every time.  This ensures you get a new grub installed properly.

Yes I also agree, If you have any needed files on your Ubuntu just back them up to a external drive then delete both of the existing Linux partitions.

Create new partitions and select the file format as EXT4 when your creating your new partitions. That'll make your system much more stable.

---

### Post by mikewhatever on 2010-05-01
I think Gparted may be a better way to delete partitions. The installer doesn't really delete or format anything unless you confirm the action.

---

### Post by MorrisseyJ on 2010-05-01
Great, thanks for all the info on this.

Now enjoying an installed version of 10.04

In the end i had to use GParted as the installer wouldn't take care of deleting.

For those who might have the same issue:

I opened GParted
Turned off swap partition - right click on swap and hit 'swapoff'
Deleted all partitions other than windows partitions
Installed into the open space using the installer

I don't know why i managed to get so confused with this, but does anyone know of a tutorial which goes through these (now fairly simple) steps.

One thing however, does anyone know why GParted would not open in the live CD when i tried Alt-F2, run GParted. It said i needed root privelages. Then when i went through system --> administration--> GParted it would work. 

Thanks again for all of the help.

---

