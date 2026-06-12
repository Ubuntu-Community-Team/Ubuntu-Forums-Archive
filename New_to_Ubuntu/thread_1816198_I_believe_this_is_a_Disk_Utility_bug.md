---
title: "I believe this is a Disk Utility bug"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by dixcuxx on 2011-08-01
Even I use gparted to make all partitions,  the "exteneded" is still "the partition is misaligned by 1024 bytes...". Even individual partition is fine without misaligned, just the "extended" at the top of the logical drives has this message. 

I use a software in windows to check, each partition is totally fine without misaligned problem.

If this is really a bug, hope ubuntu team can fix it.

---

### Post by amjjawad on 2011-08-01
> **dixcuxx said:**
> Even I use gparted to make all partitions,  the "exteneded" is still "the partition is misaligned by 1024 bytes...". Even individual partition is fine without misaligned, just the "extended" at the top of the logical drives has this message. 

I use a software in windows to check, each partition is totally fine without misaligned problem.

If this is really a bug, hope ubuntu team can fix it.

I'm sorry but what are you trying to say here?
What are you trying to do? resize? create partition?

---

### Post by dixcuxx on 2011-08-01
> **amjjawad said:**
> I'm sorry but what are you trying to say here?
What are you trying to do? resize? create partition?

I start with a new harddisk which has nothing inside, then I use gparted to create 1 primary drive and 1 logical drive, and then I create one NTFS partition in the primary drive and one NTFS partition in logical drive, and install ubuntu in the 10G free space which I have left in logical drive.

The problem is what I have said in the topic body, if you cannot understand, I have no idea why you cannot.

---

### Post by FormatSeize on 2011-08-01
I've experienced this as well. I largely ignored it thinking that I had done something wrong. I partition manually for the most part, but being that I do occasionally use something like Gparted and still get the problem, in addition to now knowing that I am not the only one with the problem, hopefully it's addressed at some point. 
 
Most of the time it doesn't really bother me. But when it does, it irritates me to no end. I try to run cfdisk, and then it yells at me about misaligned. OK. Fine. But what really burns me up is that this prevents cfdisk from starting. 
 
Why does this happen? How can I correct the error that the program is telling me exists if it, a partition editor, won't launch? Then I have to use fdisk, which yells about being deprecated (or something). From what I can tell, the partitions are just fine. But anyhow...

---

### Post by uRock on 2011-08-01
> **dixcuxx said:**
> Even I use gparted to make all partitions,  the "exteneded" is still "the partition is misaligned by 1024 bytes...". Even individual partition is fine without misaligned, just the "extended" at the top of the logical drives has this message. 

I use a software in windows to check, each partition is totally fine without misaligned problem.

If this is really a bug, hope ubuntu team can fix it.

Have you filed a bug report? [https://launchpad.net/](https://launchpad.net/) The developers do not read the forums.

---

### Post by amjjawad on 2011-08-01
Well, sorry but never had problems with partitions.
Also GParted works perfectly :)

---

### Post by dixcuxx on 2011-08-01
> **FormatSeize said:**
> I've experienced this as well. I largely ignored it thinking that I had done something wrong. I partition manually for the most part, but being that I do occasionally use something like Gparted and still get the problem, in addition to now knowing that I am not the only one with the problem, hopefully it's addressed at some point. 
 
Most of the time it doesn't really bother me. But when it does, it irritates me to no end. I try to run cfdisk, and then it yells at me about misaligned. OK. Fine. But what really burns me up is that this prevents cfdisk from starting. 
 
Why does this happen? How can I correct the error that the program is telling me exists if it, a partition editor, won't launch? Then I have to use fdisk, which yells about being deprecated (or something). From what I can tell, the partitions are just fine. But anyhow...

Glad to know that someone in the world has the same thought too. I use program in windows to check, it is 100% perfect.

---

### Post by dixcuxx on 2011-08-01
> **amjjawad said:**
> Well, sorry but never had problems with partitions.
Also GParted works perfectly :)

If you only use Ubuntu without any extended drive, this problem should not happen.

---

### Post by dixcuxx on 2011-08-02
Can I check did anyone report this possible bug before?

---

### Post by amjjawad on 2011-08-02
> **dixcuxx said:**
> If you only use Ubuntu without any extended drive, this problem should not happen.

Had it installed with 7 systems - total 8 distro - and every thing was working perfectly. 

Hope you'll manage to fix that or get a better answer than mine :)

---

### Post by amjjawad on 2011-08-02
> **dixcuxx said:**
> Can I check did anyone report this possible bug before?

[http://launchpad.net/](http://launchpad.net/)
Check the above link.

---

### Post by dixcuxx on 2011-08-02
> **amjjawad said:**
> [http://launchpad.net/](http://launchpad.net/)
Check the above link.

How to ues it to check?

---

### Post by dixcuxx on 2011-08-02
> **amjjawad said:**
> Had it installed with 7 systems - total 8 distro - and every thing was working perfectly. 

Hope you'll manage to fix that or get a better answer than mine :)

Can you somehow show me how your disk utility look like in ubuntu?

---

### Post by dixcuxx on 2011-08-02
> **amjjawad said:**
> [http://launchpad.net/](http://launchpad.net/)
Check the above link.

I mean can you show even you click on the "extend" part, still have no realign warning?

---

### Post by amjjawad on 2011-08-02
> **dixcuxx said:**
> I mean can you show even you click on the "extend" part, still have no realign warning?

I'll get back to you soon. I'm on my cell now. 

Yours is 11.04?

Can you please post a screen shot too ?

---

### Post by dixcuxx on 2011-08-02
> **amjjawad said:**
> I'll get back to you soon. I'm on my cell now. 

Yours is 11.04?

Can you please post a screen shot too ?

Yes I am using 11.04, here is a screen shot which I just took. Other than this "extend" has this warning message, other partitions all have no problem and no warning.

---

### Post by amjjawad on 2011-08-02
> **dixcuxx said:**
> Yes I am using 11.04, here is a screen shot which I just took. Other than this "extend" has this warning message, other partitions all have no problem and no warning.

I have a test HDD and it has XP, Ubuntu 11.04 and Fedora 15. I had to wipe the HDD to use different partitions scheme. 
The old scheme has no extended partition.

I'll get back to you with a screen shot once I'll finish installation. It might take 1 hour MAX.

I've been testing many things for the last 3 days and I don't mind doing that again ;)

---

### Post by psusi on 2011-08-02
Your initial description was rather vague and unclear.  Now I can see from the screen shot that what you meant to say is that you set up the partitions in gparted, and then look at them with the "Disk Utility" and it warns that the extended partition is misaligned.

My guess is that gparted aligned the logical partition inside the extended partition, and to do that, the extended partition had to start 1 kb to the left, making it misaligned.  This isn't really a problem though, and so the disk utility is incorrect in complaining about it.  The output of fdisk -lu will confirm.

---

### Post by dixcuxx on 2011-08-02
> **psusi said:**
> Your initial description was rather vague and unclear.  Now I can see from the screen shot that what you meant to say is that you set up the partitions in gparted, and then look at them with the "Disk Utility" and it warns that the extended partition is misaligned.

My guess is that gparted aligned the logical partition inside the extended partition, and to do that, the extended partition had to start 1 kb to the left, making it misaligned.  This isn't really a problem though, and so the disk utility is incorrect in complaining about it.  The output of fdisk -lu will confirm.

I just run fdisk -lu, here is the result:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000741d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   102402047    51200000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2       102404094   625141759   261368833    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       102404096   604661759   251128832    7  HPFS/NTFS
/dev/sda6       604663808   620953599     8144896   83  Linux
/dev/sda7       620955648   625141759     2093056   82  Linux swap / Solaris

Disk /dev/dm-0: 2143 MB, 2143289344 bytes
255 heads, 63 sectors/track, 260 cylinders, total 4186112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc91a55ae

---

### Post by dixcuxx on 2011-08-02
> **amjjawad said:**
> I have a test HDD and it has XP, Ubuntu 11.04 and Fedora 15. I had to wipe the HDD to use different partitions scheme. 
The old scheme has no extended partition.

I'll get back to you with a screen shot once I'll finish installation. It might take 1 hour MAX.

I've been testing many things for the last 3 days and I don't mind doing that again ;)

are you the owner of the googleubuntu? What does it do?

---

### Post by psusi on 2011-08-02
Yep; that's what is going on.  Bad disk utility!  *Smack!* ;)

---

### Post by amjjawad on 2011-08-02
> **dixcuxx said:**
> are you the owner of the googleubuntu? What does it do?

What? of course I'm not :)
I put it there so everyone can see it and use it. It's by Google and the search result will be about Ubuntu only. It's for Ubuntu.
USE it and you'll understand everything ;)

---

### Post by amjjawad on 2011-08-02
> **dixcuxx said:**
> Yes I am using 11.04, here is a screen shot which I just took. Other than this "extend" has this warning message, other partitions all have no problem and no warning.

As promised, there you go :)

```
Disk /dev/sda: 40.0 GB, 40027029504 bytes
240 heads, 63 sectors/track, 5170 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008b727

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         732     5533888+   7  HPFS/NTFS
/dev/sda2             733        1287     4194304   83  Linux
/dev/sda3            1287        1426     1048576   82  Linux swap / Solaris
/dev/sda4            1426        5171    28309505    5  Extended
/dev/sda5            1426        1981     4194304   83  Linux
/dev/sda6            1981        2536     4194304   83  Linux
/dev/sda7            2536        3091     4194304   83  Linux
/dev/sda8            3091        3633     4096000   83  Linux
/dev/sda9            3633        4175     4096000   83  Linux
/dev/sda10           4175        4676     3788800   83  Linux
/dev/sda11           4676        5171     3739648   83  Linux


```
As I posted previously, I have never had any issue with GParted, Partitions, etc. I always create my partitions before installing anything, even Windows. Sometimes, I do that while installation and I always choose "Manual" Installation. I don't want the OS to do whatever it likes, I want to do what I like and want. Therefore, I have never faced any issue.

The problems I have got so far is all about Boot-Loaders, etc and it has NOTHING to do with your issue :)

[B]
_Edit_[/B][U]**:**
[/U]For those who are wondering why I have many partitions in 40GB HDD, please be informed that it's just a test HDD on a test machine ... I use it for such purposes (learning and help others when needed).

---

### Post by psusi on 2011-08-02
amjjawad: you don't get the warning because you don't have a 4kb sector drive that wants 4kb alignment.

---

### Post by egalvan on 2011-08-02
> **dixcuxx said:**
> 
```
Disk /dev/sda: 320.1 GB,

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   [COLOR="Blue"]102402047 [/COLOR]   51200000    7  HPFS/NTFS
[COLOR="Red"]Partition 1 does not end on cylinder boundary.[/COLOR]
/dev/sda2       [COLOR="Blue"]102404094[/COLOR]   625141759   261368833    5  Extended
[COLOR="Red"]Partition 2 does not start on physical sector boundary.[/COLOR]
/dev/sda5       102404096   604661759   251128832    7  HPFS/NTFS
/dev/sda6       604663808   620953599     8144896   83  Linux
/dev/sda7       620955648   625141759     2093056   82  Linux swap / Solaris
```

The parts in red show that the boundaries are off.

gparted has the option to align to different specs...
check those options.

(sadly I'm on XP right now, and cant show screenshot of those alignment options.)

---

### Post by psusi on 2011-08-02
> **egalvan said:**
> The parts in red show that the boundaries are off.


Cylinders don't exist, so just ignore that meaningless message.  It is cruft from 25 years ago when cylinders meant something.

---

### Post by amjjawad on 2011-08-02
> **psusi said:**
> amjjawad: you don't get the warning because you don't have a 4kb sector drive that wants 4kb alignment.

Hi, can you please explain more  about that?
I'm interested to know more about it.

Thank you!

---

### Post by psusi on 2011-08-02
> **amjjawad said:**
> Hi, can you please explain more  about that?
I'm interested to know more about it.

Thank you!

New large drives like that of the OP use 4kb physical sectors instead of the conventional 512 byte ones, but continue to support logical addressing in 512 byte sectors for backward compatibility.  Attempts to access the drive work best when they are aligned to a 4kb boundary, otherwise part of the physical sector before and after the requested logical sectors has to be read.  The warning shown in the picture is warning that the partition is not aligned to a 4kb boundary, and so access to it will not be optimal.

Since it is just an extended partition though, you don't access it, but rather it just contains logical partitions, so as long as those are aligned, any misalignment of the extended partition doesn't matter.

---

### Post by dixcuxx on 2011-08-02
> **psusi said:**
> New large drives like that of the OP use 4kb physical sectors instead of the conventional 512 byte ones, but continue to support logical addressing in 512 byte sectors for backward compatibility.  Attempts to access the drive work best when they are aligned to a 4kb boundary, otherwise part of the physical sector before and after the requested logical sectors has to be read.  The warning shown in the picture is warning that the partition is not aligned to a 4kb boundary, and so access to it will not be optimal.

Since it is just an extended partition though, you don't access it, but rather it just contains logical partitions, so as long as those are aligned, any misalignment of the extended partition doesn't matter.

So does that mean only the extended partition "table" which is very small does not aligned!? And the function of this table is the structure of the real logical partiitons, so would not affect the performance..am I correct?

---

### Post by dixcuxx on 2011-08-02
> **amjjawad said:**
> As promised, there you go :)

```
Disk /dev/sda: 40.0 GB, 40027029504 bytes
240 heads, 63 sectors/track, 5170 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008b727

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         732     5533888+   7  HPFS/NTFS
/dev/sda2             733        1287     4194304   83  Linux
/dev/sda3            1287        1426     1048576   82  Linux swap / Solaris
/dev/sda4            1426        5171    28309505    5  Extended
/dev/sda5            1426        1981     4194304   83  Linux
/dev/sda6            1981        2536     4194304   83  Linux
/dev/sda7            2536        3091     4194304   83  Linux
/dev/sda8            3091        3633     4096000   83  Linux
/dev/sda9            3633        4175     4096000   83  Linux
/dev/sda10           4175        4676     3788800   83  Linux
/dev/sda11           4676        5171     3739648   83  Linux


```
As I posted previously, I have never had any issue with GParted, Partitions, etc. I always create my partitions before installing anything, even Windows. Sometimes, I do that while installation and I always choose "Manual" Installation. I don't want the OS to do whatever it likes, I want to do what I like and want. Therefore, I have never faced any issue.

The problems I have got so far is all about Boot-Loaders, etc and it has NOTHING to do with your issue :)

[B]
_Edit_[/B][U]**:**
[/U]For those who are wondering why I have many partitions in 40GB HDD, please be informed that it's just a test HDD on a test machine ... I use it for such purposes (learning and help others when needed).

I start with a clean with nothing harddisk and then use gparted to create every partition too, don't know why this would happen.

---

### Post by dixcuxx on 2011-08-02
> **psusi said:**
> New large drives like that of the OP use 4kb physical sectors instead of the conventional 512 byte ones, but continue to support logical addressing in 512 byte sectors for backward compatibility.  Attempts to access the drive work best when they are aligned to a 4kb boundary, otherwise part of the physical sector before and after the requested logical sectors has to be read.  The warning shown in the picture is warning that the partition is not aligned to a 4kb boundary, and so access to it will not be optimal.

Since it is just an extended partition though, you don't access it, but rather it just contains logical partitions, so as long as those are aligned, any misalignment of the extended partition doesn't matter.

So why my extended partition is not aligned? I used gparted to create it.......:confused:

---

### Post by dixcuxx on 2011-08-02
Info for reference: I just bought my 2,5" new notebook harddisk few days ago, so it should be using the new kind of 4K section structure....

---

### Post by wildmanne39 on 2011-08-03
Hi, here is a link for aligning your drive.
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

---

### Post by dixcuxx on 2011-08-03
> **wildmanne39 said:**
> Hi, here is a link for aligning your drive.
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

This is not the issue that we are discussing....see the detail of this post....

---

### Post by amjjawad on 2011-08-03
> **psusi said:**
> New large drives like that of the OP use 4kb physical sectors instead of the conventional 512 byte ones, but continue to support logical addressing in 512 byte sectors for backward compatibility.  Attempts to access the drive work best when they are aligned to a 4kb boundary, otherwise part of the physical sector before and after the requested logical sectors has to be read.  The warning shown in the picture is warning that the partition is not aligned to a 4kb boundary, and so access to it will not be optimal.

Since it is just an extended partition though, you don't access it, but rather it just contains logical partitions, so as long as those are aligned, any misalignment of the extended partition doesn't matter.


Hi, are we talking about this:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
[COLOR=Red][B]Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/B][/COLOR]
```


```
Disk /dev/sda: 40.0 GB, 40027029504 bytes
240 heads, 63 sectors/track, 5170 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
[B][COLOR=Red]Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes[/COLOR][/B]

```

---

### Post by Luke M on 2011-08-03
> **dixcuxx said:**
> So why my extended partition is not aligned? I used gparted to create it.......:confused:

 As psusi explained, the extended partition (which is just a container for the real partitions) does not need to be aligned. Everything is fine. The message about misalignment is spurious.

---

### Post by dixcuxx on 2011-08-03
> **Luke M said:**
> As psusi explained, the extended partition (which is just a container for the real partitions) does not need to be aligned. Everything is fine. The message about misalignment is spurious.

I see. So basically all new harddisk with have this warning with ubuntu!?

---

### Post by psusi on 2011-08-03
> **dixcuxx said:**
> So does that mean only the extended partition "table" which is very small does not aligned!? And the function of this table is the structure of the real logical partiitons, so would not affect the performance..am I correct?

Bingo.

> **dixcuxx said:**
> I see. So basically all new harddisk with have this warning with ubuntu!?

Not all; so far it looks like only most of the 1TB+ class drives have moved to 4kb sectors.

---

### Post by dixcuxx on 2011-08-03
> **psusi said:**
> Bingo.



Not all; so far it looks like only most of the 1TB+ class drives have moved to 4kb sectors.

Mine is only a 320GB notebook harddisk...but bought few days ago.....I think you can see the harddisk model from my provided information before...is it a real 4kb sectors harddisk? I don't even know.

---

### Post by psusi on 2011-08-03
> **dixcuxx said:**
> Mine is only a 320GB notebook harddisk...but bought few days ago.....I think you can see the harddisk model from my provided information before...is it a real 4kb sectors harddisk? I don't even know.

Take a look at your fdisk output for the differences that amjjawad highlighted.

---

### Post by dixcuxx on 2011-08-03
> **psusi said:**
> Take a look at your fdisk output for the differences that amjjawad highlighted.

That's cool, I can get the concept from the red words. 

Is that my partitions in extended can be in the primary? I remember primary can store 4 partitions, then may be I don't even need to use the logical sector?

---

### Post by psusi on 2011-08-03
> **dixcuxx said:**
> That's cool, I can get the concept from the red words. 

Is that my partitions in extended can be in the primary? I remember primary can store 4 partitions, then may be I don't even need to use the logical sector?

It sounds like you are conflating two unrelated concepts.  The disk is always accessed in logical sectors.  Logical vs physical sectors has nothing to do with primary vs logical partitions.  Primary partitions are the first 4 partitions, which have fixed slots for their descriptions in the MBR.  Logical partitions are subdivisions of an extended partition, which occupies one of the primary slots.

---

### Post by dixcuxx on 2011-08-03
> **psusi said:**
> It sounds like you are conflating two unrelated concepts.  The disk is always accessed in logical sectors.  Logical vs physical sectors has nothing to do with primary vs logical partitions.  Primary partitions are the first 4 partitions, which have fixed slots for their descriptions in the MBR.  Logical partitions are subdivisions of an extended partition, which occupies one of the primary slots.

So I can have my logical partitions all in primary then no need to use the extended table?

---

### Post by psusi on 2011-08-03
> **dixcuxx said:**
> So I can have my logical partitions all in primary then no need to use the extended table?

If they are primary, then they aren't logical, and vice versa.  If you only need 4 partitions, then yes, you don't need an extended, and can make all 4 primary, with no logical partitions.  Of course, if you later want to add a partition, you won't be able to without deleting one of the primary partitions and creating an extended instead.

---

### Post by amjjawad on 2011-08-03
I suggest to read this for a better understanding because I see you're confused a little bit :)

[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by dixcuxx on 2011-08-03
> **amjjawad said:**
> I suggest to read this for a better understanding because I see you're confused a little bit :)

[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

yeah I should:p

---

### Post by dixcuxx on 2011-08-03
If there any performance different if I have all my four partition in the primary area comparing with the setting I have now? I have the windows OS in a drive in primary, then 3 in extended, while 2 of these 3 are created by ubuntu installation.

---

### Post by egalvan on 2011-08-04
> **psusi said:**
> Cylinders don't exist, so just ignore that meaningless message.  It is cruft from 25 years ago when cylinders meant something.

Cylinders are not used to calculate disk capacities anymore, but they still exist. 


Its the swept area under all heads.
(they can also be called "tracks", although this is strictly true only for a single layer (side))
Platters are symmetrical lay-outs top and bottom,
and the different platters (in multi-platter drives) are identical to each other...

the translation algorithms use the physical lay-out to obtain the logical lay-out. Cylinder (track) and head number define the physical parts.

---

### Post by amjjawad on 2011-08-04
> **dixcuxx said:**
> If there any performance different if I have all my four partition in the primary area comparing with the setting I have now? 

Looks like you didn't have a look at the link I posted for you :)
You're confused again.

First of all, it's not going to be "Performance Differences" if you will have 4 Primary Partitions in your Hard Disc Drive BUT you will be come back and start a new thread asking us "I need to create more Partitions but I can't, HELP!" :)

The MAX number of Primary Partitions that you are allowed to create is "4", period.

Now, it could be:

a) 4 Primary Partitions [ sda1, sda2, sda3 and sda4 ]
b) 3 Primary Partitions + [COLOR=Red]1 Extended Partition[/COLOR] [ sda1, sda2, sda3 and [COLOR=Red]sda4[/COLOR] ]
c) 2 Primary Partitions + [COLOR=Red]1 Extended Partition[/COLOR] + Unallocated Space [ sda1, sda2 and [COLOR=Red]sda3[/COLOR] ]
d) 1 Primary Partition + [COLOR=Red]1 Extended Partition[/COLOR] + Unallocated Space [ sda1 and [COLOR=Red]sda2 [/COLOR]]

ANY Logical Partition will be INSIDE the Extended Partition.
Extended Partition count as 1 Primary Partition.

Again, make sure to check the link I posted previously. You will Understand what is going on :)

And then, make sure to have a look here: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)


> I have the windows OS in a drive in primary, then 3 in extended, while 2 of these 3 are created by ubuntu installation.There is NO way in any case that someone could have "3 Extended Partitions", period. :)

I suggest to open GParted, take a screen shot and then post it here. We'll explain to you what exactly you have and what scheme you followed to partition your HDD.

Please have a look at the screen shot.

---

### Post by dixcuxx on 2011-08-04
> **amjjawad said:**
> Looks like you didn't have a look at the link I posted for you :)
You're confused again.

First of all, it's not going to be "Performance Differences" if you will have 4 Primary Partitions in your Hard Disc Drive BUT you will be come back and start a new thread asking us "I need to create more Partitions but I can't, HELP!" :)

The MAX number of Primary Partitions that you are allowed to create is "4", period.

Now, it could be:

a) 4 Primary Partitions [ sda1, sda2, sda3 and sda4 ]
b) 3 Primary Partitions + [COLOR=Red]1 Extended Partition[/COLOR] [ sda1, sda2, sda3 and [COLOR=Red]sda4[/COLOR] ]
c) 2 Primary Partitions + [COLOR=Red]1 Extended Partition[/COLOR] + Unallocated Space [ sda1, sda2 and [COLOR=Red]sda3[/COLOR] ]
d) 1 Primary Partition + [COLOR=Red]1 Extended Partition[/COLOR] + Unallocated Space [ sda1 and [COLOR=Red]sda2 [/COLOR]]

ANY Logical Partition will be INSIDE the Extended Partition.
Extended Partition count as 1 Primary Partition.

Again, make sure to check the link I posted previously. You will Understand what is going on :)

And then, make sure to have a look here: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)


There is NO way in any case that someone could have "3 Extended Partitions", period. :)

I suggest to open GParted, take a screen shot and then post it here. We'll explain to you what exactly you have and what scheme you followed to partition your HDD.

Please have a look at the screen shot.

I see dudes...then your a, b, c, d cases all have the same performance!?

---

### Post by psusi on 2011-08-04
> **egalvan said:**
> Cylinders are not used to calculate disk capacities anymore, but they still exist. 

As far as software is concerned, no, they don't exist.

> **egalvan said:**
> Its the swept area under all heads.
(they can also be called "tracks", although this is strictly true only for a single layer (side))
Platters are symmetrical lay-outs top and bottom,
and the different platters (in multi-platter drives) are identical to each other...

Who says a drive has heads, platters, or tracks?  Think SSDs or flash sticks.

> **egalvan said:**
> the translation algorithms use the physical lay-out to obtain the logical lay-out. Cylinder (track) and head number define the physical parts.

Such translations are entirely internal to the drive, and even for conventional rotational hard disks, cylinders have not had a fixed number of sectors for years ( outer tracks have more ).  As far as anyone outside of the drive is concerned, there is no such thing as cylinders.  The cylinder information that fdisk reports is completely bogus; it just makes it up out of thin air.

Once upon a time, the software had to know the number of sectors and heads per cylinder and do the math to tell the drive "get me the second sector on cylinder x, track y".  Fortunately those days are over 20 years behind us.

---

