---
title: "Could Linux have made my USB Hd unreadable by windows?"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by Fidelio on 2010-07-06
Hi all,
I'm pretty new to using windows,but for reasons of comaptibility, a few games for the family etc, I'm now running a dual boot Windows 7/Ubuntu 10.04 machine, but ubuntu is still my basic OS. I have an external USB drive ( a fujistu 250Gb thing) which I used with linux, using an ext3 filesytem. I've tried using linux to delete all partitions, and also to format it to FAT and NTFS, but windows won't recognise it whatever I do. I just get an error saying that my USB device has malfunctioned.
Any ideas what I can do to get Windows to see it again? It works fine in linux. It couldn't be that Linux has somehow rendered it unreadable could it? I'm posting the smae thing on a windows 7 forum. It would be annoying if each camp blamed the other!!!;)
Any ideas?
Thanks
F

---

### Post by arsenic23 on 2010-07-06
Does it have an msdos label?
Have you tried formating it in Windows? (Use the computer management thing in the administrative tools.)

---

### Post by Fidelio on 2010-07-06
> **arsenic23 said:**
> Does it have an msdos label?
Have you tried formating it in Windows? (Use the computer management thing in the administrative tools.)
Thanks, Do you know where that is in Window7. Sorry if this is turning into a windows support question....

---

### Post by arsenic23 on 2010-07-06
I don't know where anything is in Vista or 7 since they added that program search thing into the start menu.  Just type [COLOR="DarkRed"]computer manag[/COLOR] and it should come up.  Otherwise I think you have to go into the start menu properties and add administrative tools and find it there....  or something similar.  I just use the search bar.

Here's an image I found off google:
[IMG]http://www.sevenforums.com/attachments/general-discussion/659d1226918804-create-mount-vhd-s-windows7-compmgt.png[/IMG]

Once you get into it you should see your drive in the disk management section.  Just right click and format.

---

### Post by Fidelio on 2010-07-07
Thanks for that. Same reply I got on a windows forum actually, but my disk just doesn't show up at all in Windows, which is weird, as it's currently formatted as NTFS and I can write to and from it in linux. Very odd, isn't it?

---

### Post by arsenic23 on 2010-07-08
OK.  I have only one other idea.  I've seen a few SATA drives that for some reason or another don't get detected right away in Windows 7 when you hot plug them after being mounted in linux, but they still work.  Maybe you are experiencing something similar.

What you can try is insert your drive, and then after about 30 seconds go to the [COLOR="DarkRed"]device manager[/COLOR] and hit the detect new hardware button.  Check back in the disk management console to see if your disk is visible now.

Just to double check:  Other USB disks are working with your windows install, right?

---

### Post by nothingspecial on 2010-07-08
I have no idea if this will work or not, it`s just a shot in the dark really, but have you tried ntfsfix

```
sudo apt-get install ntfsprogs
```

unmount the drive then

```
sudo ntfsfix /dev/sd??
```

From the man page```
**Name**

 ntfsfix - fix common errors and force Windows to check NTFS  **Synopsis**

 ntfsfix [options] device  **Description**

 ntfsfix is a utility that fixes some common NTFS problems. ntfsfix is NOT a Linux version of chkdsk.   It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows.  You may run ntfsfix on an NTFS volume if you think it was damaged by  Windows or some other way  and it cannot be mounted.  

```

It`s got to be worth a shot.

Don`t forget to unmount the drive first.

---

