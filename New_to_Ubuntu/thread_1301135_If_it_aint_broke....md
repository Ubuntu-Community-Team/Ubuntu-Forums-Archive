---
title: "If it aint broke..."
date: 2009-10-25
forum: New to Ubuntu
---

### Post by psy-moon on 2009-10-25
greetings all,
 I am feeling like an absolute beginner again so here I am.

My system has evolved in a kind of organic way so it seems complicated and Im sure there is a better way to set it up,
 but this is how it is and it has worked fine until I messed with bios settings

Ide pimary master is nfts with a windows mbr so I can boot it by setting bios to boot hd0
Ide primary slave is nfts , has a windows mbr but cannot boot unless I swap the jumpers to make it a master but I have no need to do that.

When I started running short of space I added a SATA card and drive.
So the first Partition on the sata is nfts.

Then I discovered ubuntu
so the next partition is an extended
containing  logical drives for ubuntu distros in different flavors

the sata mbr is grub, the grub folder is in /boot on sda5

to get grub to handle booting I set bios to boot from scsi

 Grub boots my two current linux distros no problem but
when I try to boot windows with grub I get 
Starting
and then a string of win ding type garbage

Here's the business part of my menu.lst ,
 
title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-rt
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-24-rt root=UUID=f138a259-83f3-4ef6-99f4-60f57d071b23 ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-rt
quiet


title        Ubuntu 8.04.3 LTS, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

# This entry manually added by user to boot linux OS

title        Ubuntu 9.04
root        (hd0,6)
kernel        /vmlinuz root=/dev/sda7 ro quiet splash
initrd        /initrd.img

# This entry  added by the user for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
root        (hd1,0)
makeactive
chainloader    +1

curiously the ide drives are getting scsi type whatnots in /dev i.e. /dev/sda is the sata drive
but /dev/sdb and /dev/sdc are ide primary master and slave.

My thinking is I aught to get myself another sata drive and get my stuff off the ide drives before they go whur whur ticky tick pop.

And the moral of the story is.... If it aint broke...DONT FIX IT

Enlightenment most welcome

---

### Post by tomBorgia on 2009-10-27
I think (don't quote me on this) that some versions of windows (like XP) get a bit upset if they're not on the primary hard disk. 

They'll certainly get upset if the disk layout is changed (i.e. the disk was the "master" device but then changed to "slave") which I think is what you've done here. 

Tom.

---

### Post by rolnics on 2009-10-27
> **tomBorgia said:**
> I think (don't quote me on this) that some versions of windows (like XP) get a bit upset if they're not on the primary hard disk. 


+1

Windows don't play with anything else, but being the first primary partition on the master. Although thinking about it, I'm sure I had windows xp on a slave drive before?! 

I'm not sure about Vista, but XP and previous windows version only like to play if they are the first primary partition. I think they can get fussy if they cross the 8Gb boundary, but I might be wrong on that one.

---

### Post by sandyd on 2009-10-27
> **rolnics said:**
> +1

Windows don't play with anything else, but being the first primary partition on the master. Although thinking about it, I'm sure I had windows xp on a slave drive before?! 

I'm not sure about Vista, but XP and previous windows version only like to play if they are the first primary partition. I think they can get fussy if they cross the 8Gb boundary, but I might be wrong on that one.
it doesnt need to be the first primary partition - i have a win vista oem disk so the partitions are backwards, 500gb ubuntu, then the 8gb swap and win vista. still works. however, i can comfirm that windows does get quite upset if you change the disk layout. for me, i had to run the vista repair disk (search on google) to fix it. after that, it was happily booting again

---

### Post by QLee on 2009-10-27
[QUOTE=psy-moon]

 Grub boots my two current linux distros no problem but
when I try to boot windows with grub I get 
Starting
and then a string of win ding type garbage[/QUOTE]

An exact error message here would have been a bit more informative, if you wanted us to understand, even if Windows error messages aren't as detailed as Ubuntu's.

[QUOTE=psy-moon]# This entry  added by the user for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
root        (hd1,0)
makeactive
chainloader    +1[/QUOTE]

And this is probably the root of your problem, the actual root for Windows isn't necessarily going to remain the same after you have changed the order of the drives.

[QUOTE=psy-moon]curiously the ide drives are getting scsi type whatnots in /dev i.e. /dev/sda is the sata drive
but /dev/sdb and /dev/sdc are ide primary master and slave.[/QUOTE]

Yeah, device nodes, newer kernels identify this this way. 


[QUOTE=psy-moon]My thinking is I aught to get myself another sata drive and get my stuff off the ide drives before they go whur whur ticky tick pop.[/QUOTE]

Why would you think that what you have described means that "...tick pop" stuff, all you did was change boot order.

My suggestion is to learn about mounting by UUID rather than device node. Using the unique identifier avoids the problem you have described. An example is the first entry in your menu.lst.

One of these might help:
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)
[http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/](http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/)



[QUOTE=psy-moon]Enlightenment most welcome[/QUOTE]

Hope this helps.

---

### Post by philinux on 2009-10-27
Easy way round this in grub is to put the map command in the stanza to make windows think it is on the first hard drive.

Works in one of my boxes.

[http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html](http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html)

Example stanza
[http://www.troubleshooters.com/linux/grub/specialboots.htm#_Making_a_Simple_grub_Booter_Floppy](http://www.troubleshooters.com/linux/grub/specialboots.htm#_Making_a_Simple_grub_Booter_Floppy)

---

### Post by Mark Phelps on 2009-10-27
As philinux indicated, you will need to add Map commands to your MS Windows stanza in your menu.lst file.  Exactly what they need to contain depends on what disk number (based on "zero" being the first disk) contains your MS Windows boot files.

They're NOT on disk zero because your menu.lst shows Ubuntu being on disk 0.

From a terminal, do "sudo fdisk -lu" (that's a lowercase L) to get a list of disks and partitions.

However ...

Having the wrong entries in your menu.lst file is not likely to generates lots of error information when trying to boot into MS Windows.  There's a possibility that your MS Windows installs are hosed in some way.

Suggest you disconnect the drives and, reconnecting the MS Windows drives, confirm that you can still boot into MS Windows.

---

