---
title: "i want to install ubuntu {dual boot}"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by jimbean on 2008-12-28
i am using the live cd 8.04

i am at the live cd desktop

i have a 300 gig hd

half of it is partitioned ntfs with vista

i have not partitioned the second half

THE QUESTIONS ARE

i have clicked the install icon on the linux live cd desktop

i am at create a new partition menu

type for new partition ????

location for new partition ?????

mount point ?????

---

### Post by stephenrs on 2008-12-28
type of new partition should be ext3 mount point /

just think of / as the equivalent of installing windows to C:\

---

### Post by inxygnuu on 2008-12-28
Here are some answers:

ext3 for partition type

"/" for the mount point

I am not sure where the partition will go, but put it in the largest available free space, or the other half of your hd.

Hope I helped,
3v4n

---

### Post by appi2012 on 2008-12-28
If you go back one menu, it should have various options for partitioning. There should be one called: "guided: use all largest contiguous free space" or something like that. That should automatically install it in the half of your hard drive that is not partitioned.

Hope that helps!

---

### Post by inxygnuu on 2008-12-28
> **stephenrs said:**
> type of new partition should be ext3 mount point /

just think of / as the equivalent of installing windows to C:\

yes! but / can also be considered your hard drive\"my computer"

---

### Post by jimbean on 2008-12-28
sorry did not explain it well

{my life story}

its says at the box i am looking at right now is

\\\\\Prepare Partitions\\\\



what should i put in the 5 {fields}  or you could call them  5 options

so i dont destroy vista




ive screwed this up before

---

### Post by noerrorsfound on 2008-12-28
He should at least make a swap partition in addition to root.

---

### Post by appi2012 on 2008-12-28
If you are worried about accidentally messing up, then the best bet for you would be to hit the back button, and then choose the guided option that uses the available free space.

---

### Post by inxygnuu on 2009-01-04
I would personally do the partitioning manually, but make sure you have swap, and review your settings multiple times. Guided is fine, but I don't trust it.

Best Regards,
3v4n=P~

---

### Post by joshmuffin on 2009-01-04
You may want to consider using a logical partition as you have a limited number of primaries available < if you are going to be install more OS's

Your swap should be logical and the ratio of ram to swap space should be 1Gb:1Gb

I would have it like this:

5Gb, logical, Ext3, Mount point '/'  < where you install ubuntu

150Gb (im guessing), Primary, ntfs, Mount point '/windows'  < Vista partition Make sure you don't format

1-4 Gb, logical, swap area < Swap space (like page file in windows)

Hope my post wasn't to late but you'll know for next time.

The rest of Gb, ext3, Mount Point /Home < this is where all your data goes so that if you ever re-install Ubuntu your home (like 'my documents') where all your data is, doesn't get lost.


If you don't understand PM me and I'll be more then glad to help, Ive stuffed this up enough times. I know how frustrating it is.

---

### Post by semi_fiction on 2009-01-04
You want to create a partition in the free space about 150 MB, format as ext3 and mount it at "/boot" Then create an 1024 MB partition in the free space, and under mount point, select "swap" Then use the remainder of free space formatted as ext3 and mounted at "/"
Make sure your Vista partition's "format" box is NOT checked!
This worked for me!
EDIT: It is very important to create the /boot partition otherwise you won't be able to boot into Vista!!

---

### Post by Miljet on 2009-01-04
> 
EDIT: It is very important to create the /boot partition otherwise you won't be able to boot into Vista!!

That is absolutely not true! I have set up numerous dual-boot systems and have never created a separate /boot partition.

---

### Post by joshmuffin on 2009-01-04
Bump > Miljet
/boot > there is no need for it

---

### Post by semi_fiction on 2009-01-05
Hmm that's interesting. On the 3 Seagate 500GB Drives I have dual-booted Ubuntu on, I have needed to make a "/boot" partition otherwise I would get "Grub Error 17." Must be that model of drive interacting with pheonix BIOS, since they are all identical. Maybe it has something to do with the "Auto/LBA/Large" option?

---

### Post by wizardzg on 2009-01-12
Hi all. I do not have any replay really, but do have similar question. Need help with installation also. I have 4 HDD-s, 2x250 gb in RAID 1 and 2x 500 gb also RAID 1. On my 1. partition on 250gb disks I have Win XP, and on second primary partition on 500 gb wanted to install ubuntu I also made thrid primary partiton for swap on 500 gb. I successfully finished installation but after reboot my computer doesn't display boot manager so it directly boots win XP. I also noticed that when it boots in win xp my Gigabyte RAID manager shows that it found errors on the first RAID arrey that is on my 250 gb disks. I understand that the MBR is on that disk but for some reason ubuntu didn't install its loader. I would thought that the problem is a driver for my RAID controller which is on my motherboard but during installation it read all of my partitions with no problem, and I also managed to partiton second disk and create 2 partitions for my Ubuntu. Why is that??? :confused:
How to solve this problem. PLS help !

---

