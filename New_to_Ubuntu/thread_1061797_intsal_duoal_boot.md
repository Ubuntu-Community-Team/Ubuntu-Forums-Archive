---
title: "intsal duoal boot"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by kimikrishna on 2009-02-06
I tried ubuntu wubui//

I unstalled ubuntu..

now i want to partitition hard disk

I WANT DUAL BOOT..

i read installation giuides..

BUT I AM NOT getting "guide - resize and use free space" option

i get only the next three..

HELP ME asap ..

---

### Post by ubhi on 2009-02-06
give the full detail...

what u want exactly...dual boot with ubuntu or winxp or what else..
& what partition type u have right now...

then anyone can help you...

---

### Post by kimikrishna on 2009-02-06
I have win xp now..

with 4 drives//  [ C D E and F ]

I have windows installed in C 

 I want to partitition C drive and install ubuntu..

but from Live cd "install icon" 

I AM NOT GETTING "guide - resize and use free space"

I have duo core 2 processor with 3 Ghz 

1 Gb ram

80 gb hard disk

LCD monitor

---

### Post by konqueror7 on 2009-02-06
hello! this the guide i used when i tried to dual-boot...

[URL="http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm"]
XP -first, Ubuntu -second[/URL]
or
[Ubuntu -first, XP -second]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")

hope it helps...

---

### Post by kimikrishna on 2009-02-06
no..

i read many guides ..


BUt i am not GETTING "resize and use free space" option..

---

### Post by konqueror7 on 2009-02-06
uhu,,so you want to install ubuntu within the your xp partition? is that right? is there still free space in it?

---

### Post by konqueror7 on 2009-02-06
here,,,check this post, its similar to yours...
[http://ubuntuforums.org/showthread.php?t=1052364]("http://ubuntuforums.org/showthread.php?t=1052364")

---

### Post by ajgreeny on 2009-02-06
Also run the ubuntu live CD, open a terminal and post the output of ```
sudo fdisk -l
```You have 4 partitions but it would be useful to know what they all are before suggesting where to install ubuntu.  We can then probably suggest how best to manually partition your disk for the best setup.

---

### Post by konqueror7 on 2009-02-06
no offense, but you think to much of yourself suggesting that we don't know what we are doing...the guy just needed help installing ubuntu in a dualboot and asking why the auto-partition is not visible...

maybe his partition are full, or maybe in use...

but anyway, its good that you recommended to check his harddrive stats using fdisk...

no offense, where just trying to help here...

---

### Post by kimikrishna on 2009-02-06
:O .. I have 10 gigabyte space left in drive C ..

---

### Post by kimikrishna on 2009-02-06
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb328b328

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9728    57657285    f  W95 Ext'd (LBA)
/dev/sda5            2551        5100    20482843+   7  HPFS/NTFS
/dev/sda6            5101        7650    20482843+   7  HPFS/NTFS
/dev/sda7            7651        9728    16691503+   7  HPFS/NTFS this is what i got

---

### Post by kimikrishna on 2009-02-06
yes.. i need "guided - resize and use free space " option//

i get option "use entire disk" and "manual"..

I WANT to partitition C drive

---

### Post by kimikrishna on 2009-02-06
i have 9.4 gb exact left//

isnt that enuogh for ubuntu ?

---

### Post by konqueror7 on 2009-02-06
it seems strange that the "guided - resize and use free space" option is not available...for now, try booting from the live cd and using gparted to partion c:\. also, don't you have any partition that could be used instead...

just have a back-up just in-case...

---

### Post by kimikrishna on 2009-02-06
> to partion c:\. also, don't you have any partition that could be used instead...

what do this mean ? [:O] [/)]

---

### Post by konqueror7 on 2009-02-06
to partition c:\ i mean...also don't you have some free partition, in which you could instead install ubuntu there using "manual" option?

---

### Post by kimikrishna on 2009-02-06
have 80 gigabyte harddisk..

20 gb in each of  C D E and F

this is all i know..

now , i want "guide -resize & use free space" .. :( :(

---

### Post by overdrank on 2009-02-06
> **kimikrishna said:**
> have 80 gigabyte harddisk..

20 gb in each of  C D E and F

this is all i know..

now , i want "guide -resize & use free space" .. :( :(

Please use the live cd and you can find the partition manager located under system, administration I believe. Then post a screen shot so we can see your partitions. You must have a extended partition. :)

---

### Post by ajgreeny on 2009-02-06
> **deuphil.kaufmann said:**
> no offense, but you think to much of yourself suggesting that we don't know what we are doing...the guy just needed help installing ubuntu in a dualboot and asking why the auto-partition is not visible...

maybe his partition are full, or maybe in use...

but anyway, its good that you recommended to check his harddrive stats using fdisk...

no offense, where just trying to help here...
I don't know if this comment was leveled at me, but if so, where did I suggest you do not know what you are doing?  All I suggested was for him look at the partitions on the disk, which were not known at that point, and then we, other forum users, could try to help by suggesting how best to use them.  I was trying to help with another idea, not maligning your helpful suggestion

---

### Post by kimikrishna on 2009-02-06
ajgreeny  ?? 

give solution for this.. /

---

### Post by kimikrishna on 2009-02-06
> [http://i42.tinypic.com/n3ku3a.jpg](http://i42.tinypic.com/n3ku3a.jpg)
here is Gparter

---

### Post by kimikrishna on 2009-02-06
i dont know 

it shows my E with krishna has Nothing stored and Empty..

but i have only 5 gb left in krishna E out of 20

---

### Post by konqueror7 on 2009-02-07
hey, could you try defraging you windows partition first, then probably scan disk it first for errors? because it was mentioned in some ubuntu manual, that if the windows partition is too fragmented, it will not be able to properly parition you hardrive during ubuntu installation...

---

### Post by overdrank on 2009-02-07
> **kimikrishna said:**
> here is Gparter

I will have to agree with deuphil.kaufmann in post #23. 
Also in the screen shot you provided the partition sda 6 has no data then you can use manual partition and install Ubuntu on that partition. :)

---

### Post by kimikrishna on 2009-02-07
no.. 

it shows wrongly..

i have 15 gb of content [out of 20 gb ] in krishna [sda6]

---

### Post by kimikrishna on 2009-02-07
and i have defragmented with a tool called DEFRAGGLER 

here its is 

> [http://www.defraggler.com/](http://www.defraggler.com/)

**I TRIED DEFRAGMENTING BEFORE I TRIED TO INSTALL UBU DUAL BOOT**

---

### Post by kimikrishna on 2009-02-07
how do i scan windows disks for errors ??

---

### Post by konqueror7 on 2009-02-07
right click the harddrive and click properties, click on the tab that says "Tools", there you can find scan disk...it usually request for you to scan it during boot if its the main partition...

---

### Post by kimikrishna on 2009-02-07
and what about that E drive thing ??

it has 15 gb and it shows empty ???

---

### Post by kimikrishna on 2009-02-07
and also I GOT KUBUNTU CD to home today..

tried installing Kubuntu..

the same option [guided resize and use free space] is missing there too

---

### Post by konqueror7 on 2009-02-07
> and what about that E drive thing ??

it has 15 gb and it shows empty ???

what do you mean by this? as i see it in you screenshot, its empty, why not install ubuntu there instead, if everything else does not?...have you finished the scan disk of the main partition?...

---

### Post by kimikrishna on 2009-02-08
my E drive has total size of 20 gb 

and i have used 16 gb of it by now...

but gpater shows that it is empty.

some problem w\ith gparter..

yes  i tried scan disk but of no use in getting that option

---

### Post by kimikrishna on 2009-02-08
its not empty

it has 16 gb of contents inside it.. 

i mean, in the drive named KRISHNA  [E]

---

### Post by konqueror7 on 2009-02-08
mmm...what i think the problem is either the installer, or you harddrive,,,but since it has no error and only gparter displays it as empty...

you could try this parition manager instead, i used it when i edited my partition when i also wanted to install ubuntu...[here]("http://www.partition-tool.com/personal.htm")

try to use it to resize your partition so you could get a chunk of free space that you will create as a new partition, then try installing ubuntu again...

(just make a backup of your files, i don't mean that its not safe to use it, i've used it also with having all my data still inside)

---

### Post by kimikrishna on 2009-02-08
whats the next step ?

i have dloaded it..

so what to do now ?

---

### Post by konqueror7 on 2009-02-08
install it, and repartition/resize you hardrives...in this way, you could install ubuntu in a separate partition without waiting for the "auto-resize" function in the installer to function...

---

### Post by kimikrishna on 2009-02-08
will it del the contents inside my drive c ?

---

### Post by kimikrishna on 2009-02-08
do i need to resize it 

and create a new drive in that freed space ?

---

### Post by kimikrishna on 2009-02-08
i have 8 gb left in drive C ..

if i resize and free that 8 gb, what to do with it ?

create a new drive in that 8gb ?

---

### Post by konqueror7 on 2009-02-08
yes, its the same concept as with "auto-resize" in the live-cd,,,create a new partition from this freed space, then you can install ubuntu there...

---

### Post by kimikrishna on 2009-02-08
what about the 10 gb content inside C ?

will all those get deleted ?????????

---

### Post by konqueror7 on 2009-02-08
no, you will just resize it,,,i've used it to resize several of my partition, no problem,,,but as a precaution, you can backup...

---

### Post by kimikrishna on 2009-02-08
ok.. thanks i will do this..

I have exams tomorrow ! 

so, i will let you know after i resize drive C..

thanks

---

### Post by kimikrishna on 2009-02-08
as for now, i reinstalled WUBI..

later ,  i will resize with that tool ..

---

