---
title: "Making Primary Partition, Error..."
date: 2011-01-17
forum: New to Ubuntu
---

### Post by Linyx on 2011-01-17
You can Guess from the **Screen-Shot** that i had only 3-Primary Partitions, and when ever i want to make another(From **Un-Allocated Space**), It shows me an Error message that you can't make more then 4-Primary Partition, but i have only 3 primary Partitions right now....

Any one knows why this give me an Error Message...?

---

### Post by diablo75 on 2011-01-17
"Because an extended partition is also a primary partition" (so says the box on the screen).

If this is to be believed... you've got a lot of work on your hands if you want to create another partition.

sda1, sda2, sda3 and sda4 are all considered primary partitions.  sda4 is an extended partition (and by definition also considered primary) and within it are several more logical partitions.

It would seem like the easiest way to fix this is expand the "left" (or beginning) of sda4 out towards the left to take up the unallocated space and then create a new logical partition within sda4.

---

### Post by Linyx on 2011-01-17
Ok, I got this Now, i had deleted the Last Allocated space in the Extended one and now it let me to formate that Partition to NTFS, but now i am unable to make the last unallocated space to be formate, because now it shows me the same message as Shown in Screen-Shot....

Looks like i had moved my one of space to extended in past....and it still included in Primary...

---

### Post by Linyx on 2011-01-17
> **diablo75 said:**
> "Because an extended partition is also a primary partition" (so says the box on the screen).

Just create an extended partition instead.

Thanks..but what to do now...Now i had manage to formate that drive as i had shown in my second Post, but now i am unable to make the Last unallocated Space to be formate,

Can i switch to live Cd now in order to make that unallocated space to be join with sda3...?

---

### Post by diablo75 on 2011-01-17
> **Linyx said:**
> Ok, I got this Now, i had deleted the Last Allocated space in the Extended one and now it let me to formate that Partition to NTFS, but now i am unable to make the last unallocated space to be formate, because now it shows me the same message as Shown in Screen-Shot....

Looks like i had moved my one of space to extended in past....and it still included in Primary...

I edited my other post while you were writing this.  Have a look at it.

By the way, I see what you're trying to do, by moving all the partitions to the left to create that 26 GB unallocated partition.  This is dangerous.  Heck, repartitioning in general is dangerous.  BACKUP YOUR DATA before you do anything because this is just a big mess of partitions.

---

### Post by warfacegod on 2011-01-17
Indeed, make a backup. If you want that space to be part of sda3, you'll need to move it next to the partition and then resize sda3.

---

### Post by Linyx on 2011-01-17
Thanks for king Replies, :p

Have a look at the Screen-Shot Plz, 

Their are two Unallocated Spaces, which i want to Resize so that i can **join** both of them to behave as **One-logic Partition** & For that i Resize My **sda4** , it Resize fine but i am unable to join both unallocated Spaces because no One Moves......

Another Question, Will Xp install on Logical Partition...? ?

---

### Post by Quackers on 2011-01-17
In your last screenshot you are proposing to delete sda3, yes? It is not done yet, though, as you haven't yet clicked on the green tick in the toolbar, to apply the proposed change.
Have you backed up what was in sda3?
If you apply the change, you will then be able to extend sda4 (the extended partition) both ways ( to the left AND to the right). This will give free space within sda4 (2 lots of it). When that is done you can move all the logical partitions around so that all of the free space is in one place, and a new logical partition can then be created.
Be aware that only one job should be done at a time (clicking on the green tick mark) - not all at once.
These jobs will take a lot of time - maybe 2 and a half hours each! It is wise to make backups first, as partitioning can go wrong!

EDIT  This is important. These changes should not be done on a mounted system! You should run them from gparted in a live cd desktop! You should also turn swap off before making changes, then turn swap back on after all changes are made.

---

### Post by Linyx on 2011-01-17
> **Quackers said:**
> In your last screenshot you are proposing to delete sda3, yes? It is not done yet, though, as you haven't yet clicked on the green tick in the toolbar, to apply the proposed change.
Have you backed up what was in sda3?
If you apply the change, you will then be able to extend sda4 (the extended partition) both ways ( to the left AND to the right). This will give free space within sda4 (2 lots of it). When that is done you can move all the logical partitions around so that all of the free space is in one place, and a new logical partition can then be created.
Be aware that only one job should be done at a time (clicking on the green tick mark) - not all at once.
These jobs will take a lot of time - maybe 2 and a half hours each! It is wise to make backups first, as partitioning can go wrong!

EDIT  This is important. These changes should not be done on a mounted system! You should run them from gparted in a live cd desktop! You should also turn swap off before making changes, then turn swap back on after all changes are made.

Thanks Quakers, But i had deleted that Partition and Clicked apply, thats Done fine but what i am trying to say that it wasn't moving once i Resize my Extend Partition,

However, I am Able to Successfully add that drive to Extended partition, but i wasn't able to **Move** that Added unallocated Space towards the** Bottom** one, so that i can join them both, Moreover, i had Un-Mounted them before i was Doing the Process....

Sorry 4 my Bad English,

---

### Post by Quackers on 2011-01-17
Then you must have clicked on the green tick after, as the deletion of sda3 is still showing as pending in the bottom left of the window.
I'm not sure I'm understanding you, but here goes. Once sda3 is deleted you have unallocated space before sda4. To include that unallocated space inside the extended partition you need to resize sda4 "to the left".
Then to include the unallocated space that is after sda4, you need to resize sda4 "to the right".
When this is done, both unallocated spaces will become free spaces within sda4.
You may be there already - not sure.
You can't then move those free spaces. You move sda5,6,7 and 8 so that they leave one free space at the end of sda4. Each of these moves will take 2 hours or more, and should be done separately.
Have you turned off swap?

---

### Post by Linyx on 2011-01-17
> **Quackers said:**
> Then you must have clicked on the green tick after, as the deletion of sda3 is still showing as pending in the bottom left of the window.
I'm not sure I'm understanding you, but here goes. Once sda3 is deleted you have unallocated space before sda4. To include that unallocated space inside the extended partition you need to resize sda4 "to the left".
Then to include the unallocated space that is after sda4, you need to resize sda4 "to the right".
When this is done, both unallocated spaces will become free spaces within sda4.
You may be there already - not sure.
You can't then move those free spaces. You move sda5,6,7 and 8 so that they leave one free space at the end of sda4. Each of these moves will take 2 hours or more, and should be done separately.
Have you turned off swap?

I am Getting your Words, and i had already done Resizing via Gparted, but one thing where i am Stuck is Once i add both unallocated Spaces to Extended(Means both are now a part of extended partition, and i had Clicked apply, it done fine),but.................the Problem is, **none of them moves**.....!!

Yes, i had** un-mounted** all the drives including swap....

It will take much of my time as you had said....Is their any Other easy and LESS-TIME Consuming method...? So that i can Join them Both...

And another thing, Can i install XP in Logic-Partition..?

---

### Post by Quackers on 2011-01-17
The only way that I'm aware of to make the two free spaces contiguous is to move the other partitions to the left (or all to the right). It is a slow process, but you are moving a lot of data.
If you already have a Windows system, I think XP can be installed to a logical partition, as XP's boot files are stored in the other Windows system,s partition. But you would need to check that.
If you don't have a Windows system already, I suspect you would need a separate boot partition to do that.
Maybe somebody else could confirm that for us?

---

### Post by Linyx on 2011-01-17
> **Quackers said:**
> If you already have a Windows system, I think XP can be installed to a logical partition, as XP's boot files are stored in the other Windows system,s partition. But you would need to check that.
If you don't have a Windows system already, I suspect you would need a separate boot partition to do that.
Maybe somebody else could confirm that for us?

Yes, i have Win-7 on my PC, but i Want to know whether XP will Accept Logic-Partition or not....

---

### Post by Quackers on 2011-01-17
In that case, I think it will be ok in a logical partition. XP's boot files should go in with Windows 7's boot files, which are on a primary partition. That should make XP bootable.

---

### Post by srs5694 on 2011-01-17
> **Linyx said:**
> i wasn't able to **Move** that Added unallocated Space towards the** Bottom** one, so that i can join them both, Moreover, i had Un-Mounted them before i was Doing the Process....

First, you can't do anything with unallocated space except move it. It's unallocated. Trying to move it is like saying "I'd like to move this empty space between these two chairs" -- that's backwards. You move the chairs (partitions), not the empty space between them. (A partial exception is moving unallocated space between the primary table and the extended partition, which is done by resizing the extended partition.)

Second, there are a lot of key icons in your screen shots. These denote partitions that are "locked" -- you can't change them. The usual reason is that they're mounted or otherwise in use. If a logical partition is in use, the extended partition that contains it is also in use. To fix this, you'll need to reboot using an Ubuntu live CD or some other recovery disc, such as [PartedMagic](http://partedmagic.com/) or [System Rescue CD.](http://www.sysresccd.org/) You must use such a solution whenever you need to change your Ubuntu boot partition (or the extended partition that contains it, if it's on a logical partition).

---

### Post by Linyx on 2011-01-17
> **Quackers said:**
> In that case, I think it will be ok in a logical partition. XP's boot files should go in with Windows 7's boot files, which are on a primary partition. That should make XP bootable.

And what if i want to reinstall Win-7 in Future or Remove it,,, will XP boot then...?I think it will not,...Maybe i am wrong...

---

### Post by Quackers on 2011-01-17
I don't know. Maybe we could cross that bridge if we come to it :wink:
Did you see srs5694's post, one above yours?

---

### Post by Linyx on 2011-01-17
> **srs5694 said:**
> First, you can't do anything with unallocated space except move it. It's unallocated. Trying to move it is like saying "I'd like to move this empty space between these two chairs" -- that's backwards. You move the chairs (partitions), not the empty space between them. (A partial exception is moving unallocated space between the primary table and the extended partition, which is done by resizing the extended partition.)

Second, there are a lot of key icons in your screen shots. These denote partitions that are "locked" -- you can't change them. The usual reason is that they're mounted or otherwise in use. If a logical partition is in use, the extended partition that contains it is also in use. To fix this, you'll need to reboot using an Ubuntu live CD or some other recovery disc, such as [PartedMagic]("http://partedmagic.com/") or [System Rescue CD.]("http://www.sysresccd.org/") You must use such a solution whenever you need to change your Ubuntu boot partition (or the extended partition that contains it, if it's on a logical partition).

Thanks,

But the Screen-Shot which i had Attached was from my Current OS,that was just to shows you my Partitions, Actually i had tried that from Live-Cd , But it wasn't moving like the One which i had Showed in the Screen-Shot below...

From the Screen-Shot you can now see that I i had Added the Above unallocated Space to Extended, right?

Before this i had Done same Process from Live-Cd, and i had un-mounted all drives(Everyone)...but i wasn't able to move the Added partition to the Bottom, i had shown that in the Screen-Shot, same that happens in the Live-cd that i wasn't moving.....

---

### Post by Quackers on 2011-01-17
Yes, the unallocated spaces now appear to be within the extended partition.
If you now want to make those two unallocated spaces into one space, you need to move sda5, sda6, sda7 and sda8 "upwards", so that all the space is at the end.
These need to be run one at a time, not altogether, and from the live cd.
And you need to right-click the swap partition and select "swapoff".
Then you will be able to make a new logical partition from that space.
Then right-click swap and select "swapon"

---

### Post by Linyx on 2011-01-17
> **Quackers said:**
> Yes, the unallocated spaces now appear to be within the extended partition.
If you now want to make those two unallocated spaces into one space, you need to move sda5, sda6, sda7 and sda8 "upwards", so that all the space is at the end.
These need to be run one at a time, not altogether, and from the live cd.
And you need to right-click the swap partition and select "swapoff".
Then you will be able to make a new logical partition from that space.
Then right-click swap and select "swapon"

Thanks for support Quaker...:p

I will give it a try,but not now...and will post back if i got Errors....

---

### Post by Quackers on 2011-01-17
You're welcome :-)
Be careful :wink: Any questions come back. There are always people here who will help you. It's much better to ask than make a mistake!

---

### Post by oldfred on 2011-01-17
While it should work, I never like moving partitions around that much.

The windows boot loader in the MBR will only boot a primary active (boot flag) partition. But lilo does not not care. And you can manually edit boot.ini and use testdisk to edit XP boot parameters.

Way to boot windows in extended logical partition with lilo's MBR post#5
[http://ubuntuforums.org/showthread.php?t=1367323](http://ubuntuforums.org/showthread.php?t=1367323)
Major windows repair with dual boot and logical partition
[http://ubuntuforums.org/showthread.php?t=1411495](http://ubuntuforums.org/showthread.php?t=1411495)
You mean ntdetect and ntldr can't be on a logical partition, that is right. Yes the boot is via sda1. sda1 is there only for that purpose.
But it still needs a primary to boot from.
[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)
[http://support.microsoft.com/kb/306559#f1](http://support.microsoft.com/kb/306559#f1)
Create small FAT Primary to boot windows in logical
[http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition](http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition)

---

