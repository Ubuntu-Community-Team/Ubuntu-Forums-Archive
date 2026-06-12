---
title: "Vista won't show up in GRUB bootloader!"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by crazyflax on 2008-12-06
Hi, so I'm a complete noob and I installed Ubuntu 8.10 onto my Vista Ultimate laptop. It's a Toshiba A200-TH7. I can get into Ubuntu fine, but Vista is not being detected by the GRUB bootloader. I'd use Gparted, but the synaptic manager gives me issues about not being able to install Gparted onto my i386 system. What do I do to get Vista to load, while keeping my Ubuntu install?

---

### Post by caljohnsmith on 2008-12-06
How about first opening a termimnal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And find your Windows partition, it will be type NTFS or FAT32, and most likely it will be sda1. Then do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the very end add:
```
title Windows Vista
root [COLOR="Blue"](hdX,Y)[/COLOR]
chainloader +1
```
And replace (hdX,Y) with the Vista partition, given that:
```
(hd0,0) = sda1
(hd0,1) = sda2
(hd0,2) = sda3 
...etc.
```
And you should be all set. Let me know how it goes or if you run into problems.

---

### Post by crazyflax on 2008-12-06
sudo fdisk -lu doesnt show my vista partition. i tried adding the vista partition in hd(0,0) to the /boot/grub/menu.lst but it gives me error 13: invalid or unsupported executable type when i try to load it from the grub bootloader. when i installed ubuntu, i used that partitioner on the livecd to make the partitions and i think i overwrote vista's mbr.

---

### Post by caljohnsmith on 2008-12-06
So you overwrote your Vista partition? How about posting the results of the fdisk command just so I can see what happened.

---

### Post by crazyflax on 2008-12-06
what filetype does the text editor in ubuntu use?

---

### Post by treesurf on 2008-12-07
I'm not sure exactly how you did your installation, but check out the following howto on how to dual boot Ubuntu on top of existing Vista.  It's an excellent howto and has the info on how to bring up Vista in your grub menu.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by crazyflax on 2008-12-15
> **treesurf said:**
> I'm not sure exactly how you did your installation, but check out the following howto on how to dual boot Ubuntu on top of existing Vista.  It's an excellent howto and has the info on how to bring up Vista in your grub menu.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

I used the Linux partitioner off the Live CD and then installed. From sudo fdisk -lu I get (I'm retyping everything off the screen so I apologize ahead for mistakes):

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifir: 0x74ed76ea
Device   Boot   Start      End  Blocks Id System
/dev/sda1 *        63 19727819 9863878 83 Linux
/dev/sda2    19727820 23631614 1951897  5 Extended
/dev/sda5    19727883 23631614 1951866 82 Linux swap / Solaris

---

### Post by crazyflax on 2008-12-15
After using sudo gedit /boot/grub/menu.lst, I added this entry as there was no Vista entry, only three Ubuntu ones:
Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
make active
chainloader +1

and when I reboot I get:
Error 13: Invalid or unsupported executable format

So how do I get to my Vista partition? And if I can't get into it like that, is it even worth it to try and make it an external?

---

### Post by crazyflax on 2008-12-15
I'm done for the night, but I'll be back tomorrow. If anyone replies thank you so much for your help!

---

### Post by caljohnsmith on 2008-12-15
> **crazyflax said:**
> 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifir: 0x74ed76ea
Device   Boot   Start      End  Blocks Id System
/dev/sda1 *        63 19727819 9863878 83 Linux
/dev/sda2    19727820 23631614 1951897  5 Extended
/dev/sda5    19727883 23631614 1951866 82 Linux swap / Solaris
According to the fdisk output above, you no longer have your Vista partition; you only have your main sda1 Ubuntu partition and the swap partition. If you want Vista back, it looks like you would have to repartition the drive and reinstall Vista.

---

### Post by adam_kimber on 2008-12-15
> **caljohnsmith said:**
> According to the fdisk output above, you no longer have your Vista partition; 

Unfortunately I agree with this. :( Looks like you no longer have a Vista partition. (I hope you backed up before installing.....) 

At this point you can do one of two things.

1) Try Ubuntu for a while. It might do everthing you want and therefore you won't need Vista. 

2) If you have a manufacturer's copy of Vista, e.g. a System Restore disk or the like, or a Vista install CD you can wipe off Ubuntu, install Vista and then follow the dual boot guide above. That way you will get both. Put Vista on first, then Ubuntu, as it is much easier to add a Vista/XP entry to GRUB than trying to get GRUB back after Windows wipes it. 

Hope this helps!

---

### Post by crazyflax on 2008-12-15
Does this mean that the data that I had on my Vista partition is actually gone? If I take it to a computer repair shop, will they be able to even get any data from the hard drive or is it completely wiped?

---

### Post by caljohnsmith on 2008-12-15
> **crazyflax said:**
> Does this mean that the data that I had on my Vista partition is actually gone? If I take it to a computer repair shop, will they be able to even get any data from the hard drive or is it completely wiped?
A normal computer repair shop probably won't be able help you since the Vista partition was completely overwritten by Ubuntu. You would have to pay a professional data recovery service, and even they won't be able to get all your Vista files back since you overwrote at least part of the Vista partition with Ubuntu's files. You could try using a program like "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" on your own to see what it can recover, but you will need another drive that has at least as much space as your sda drive for photorec to put the files it finds. Also, it will take a long time to sort through all the files photorec finds, because the original names of the files are often not recovered; so photorec has to give them a generic name. Sorry about your loss.

---

### Post by crazyflax on 2008-12-15
Alright, well thank you everyone for your help.

---

### Post by billgoldberg on 2008-12-15
Rule one before installing a new OS:

Back up your data

Rule 2:

Make sure you know what you are doing (or have the guide next to you)

It seems like you just formatted the entire drive and installed Ubuntu on it.

You should have done your homework.

---

