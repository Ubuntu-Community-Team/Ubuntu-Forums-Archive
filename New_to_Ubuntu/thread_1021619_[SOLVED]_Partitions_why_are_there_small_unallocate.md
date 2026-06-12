---
title: "[SOLVED] Partitions: why are there small unallocated gaps between them?"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Senesence on 2008-12-25
I've been using gparted to look over my existing partitions (thinking about creating another, for very minimal Linux to experiment on), and I noticed that there are small unallocated chunks that seem to serve as padding.

*Screen-shot of my gparted menu is attached.*

So, my questions are:

[LIST=1]
[*]Am I right in assuming that these unallocated chunks serve as padding?
[*]If so, why is padding necessary/preferable in regards to partitions?
[*]Can I just allocate these chunks with no worry?
[/LIST]

TIA.

---

### Post by cdwillis on 2008-12-25
I'm at my mother's house using her Windows pc right now so I can't check, but neither my or my roommates computers have the unallocated space in the partitions as far as I know. Did you auto partition all of that during the install?

---

### Post by nhasian on 2008-12-25
i dont think you should have the dark gray spaces.  you should be able to resize the partitions to make use of the wasted space.  the light gray areas are just showing the different partitions, they are not taking up space.  here's a screengrab of my gparted:

---

### Post by 73ckn797 on 2008-12-25
> **Senesence said:**
> I've been using gparted to look over my existing partitions (thinking about creating another, for very minimal Linux to experiment on), and I noticed that there are small unallocated chunks that seem to serve as padding.

*Screen-shot of my gparted menu is attached.*

So, my questions are:

[LIST=1]
[*]Am I right in assuming that these unallocated chunks serve as padding?
[*]If so, why is padding necessary/preferable in regards to partitions?
[*]Can I just allocate these chunks with no worry?
[/LIST]

TIA.

1. not padding
2. NA
3. Yes

See screenshot of my system

---

### Post by plucky on 2008-12-25
Is the space gained worth the hassle if anything goes wrong?

To incorporate the 1st un-allocated space of 1Mb would mean having to move 76Gb of data,and moving data would take a very long time.

You can easily expand the /dev/sda1 partition to incorporate the 2nd un-allocated space.If you are using vista,use the vista disk management tool to expand the partition or else use the partition editor on the live CD.

You could then increase the extended to incorporate the 3rd un-allocated space.

The space gained is miniscule compared to the size of the disk.I wouldn't bother unless at some point in the future you do a complete re-install and then you could tidy up the disk.

Just my thoughts.

Good luck.

[color=red]p.s make sure you have backups of your data[/color]

---

### Post by caljohnsmith on 2008-12-25
Just a small word of caution: if you have Windows on your sda1 NTFS partition, and if you try to move the beginning of that partition to claim the 1 MB of unallocated space at the beginning of the drive, doing that will make Windows unbootable and will require a lot of effort to fix it. Thus I would not recommend trying to do that if sda1 is Windows. Those little gaps of unused space on your HDD could be because you used a Windows partition program at some point; Windows partition editors often use different HDD geometries than the standard that Linux uses, and because partitions typically end and start at cylinder boundaries, you can end up with little gaps of unused space if you use a Windows partition editor and Linux partition editor on the same drive.

---

### Post by mkvnmtr on 2008-12-25
I can't answer the original poster but I have found when I try to form partitions GParted will tell me I have so much space to use. If I use it all I get an error saying that partitions can not overlap. I then reform the partition with 1 or 2 Mb in between and GParted forms them fine. I don't mean it happened once, several times. I too had begun to assume that it must be required.

---

### Post by 73ckn797 on 2008-12-25
> **plucky said:**
> Is the space gained worth the hassle if anything goes wrong?

To incorporate the 1st un-allocated space of 1Mb would mean having to move 76Gb of data,and moving data would take a very long time.

You can easily expand the /dev/sda1 partition to incorporate the 2nd un-allocated space.If you are using vista,use the vista disk management tool to expand the partition or else use the partition editor on the live CD.

You could then increase the extended to incorporate the 3rd un-allocated space.

The space gained is miniscule compared to the size of the disk.I wouldn't bother unless at some point in the future you do a complete re-install and then you could tidy up the disk.

Just my thoughts.

Good luck.

[COLOR=red]p.s make sure you have backups of your data[/COLOR]

It would seem that there could be a problem whether using Ubuntu or Windows. I have changed partition allocations several times. Windows always had issues upon the initial reboot. Ubuntu did not. It was more a case of Windows doing a scan of the drive to check for errors due to the changes made. I have not encountered any failure of an OS to reboot. It is a good idea to defrag Windows prior to making any changes.

---

### Post by sofasurfer on 2008-12-25
If you are unsure if they are partitions or unallocated space or whatever, and you don't know which one they are in the list below the graphic representation, just put your pointer on one and click. It will be highlighted in the list below it and you can read what it is.

---

### Post by Senesence on 2008-12-25
> **cdwillis]Did you auto partition all of that during the install?[/QUOTE]

The allocation you see is resultant from the initial partition that the Ubuntu Live CD executes on fresh install.

[quote=caljohnsmith]Just a small word of caution: if you have Windows on your sda1 NTFS partition, and if you try to move the beginning of that partition to claim the 1 MB of unallocated space at the beginning of the drive, doing that will make Windows unbootable and will require a lot of effort to fix it. Thus I would not recommend trying to do that if sda1 is Windows.[/quote]

Wow, thanks, that's good to know. And yes, as clearly marked in my attached screen-shot, /dev/sda1 is indeed an ntfs partition.

[quote]Those little gaps of unused space on your HDD could be because you used a Windows partition program at some point said:**
> 

Well, this machine shipped with Vista, but I never did any repartitioning from that OS. The one and only time where the partitions were modified were when Ubuntu was installed, using the partition tools that come on the Live CD (gparted as well..I think).

[quote=plucky]Is the space gained worth the hassle if anything goes wrong?

No, but then again I never planned to mess with that first 1MB of unallocated space.

Although, I appreciate the heads-up on the lengthy data copy that would have to be executed if partitions were resized by moving their "starting point" - I sort of assumed as much.

**@Everyone**

I only have a few more questions, and then I'll mark this thread as solved. If I understood you guys correctly, these would be considered safe procedures:

[LIST=1]
[*]Shrink /dev/sda1 to make the second unallocated chunk larger.
[*]Make the resulting larger chunk into a new partiton to host some other distro.
[/LIST]

Am I assuming correctly?

---

### Post by plucky on 2008-12-26
> @Everyone

I only have a few more questions, and then I'll mark this thread as solved. If I understood you guys correctly, these would be considered safe procedures:

   1. Shrink /dev/sda1 to make the second unallocated chunk larger.
   2. Make the resulting larger chunk into a new partiton to host some other distro.


Am I assuming correctly?

From your screenshot,it makes more sense to not touch your vista partition but incorporate the unallocated space into the extended partition and shrink the ubuntu partition to make enough space for a new distro.This also leaves you with the capability of adding another primary partition in the future.

Your vista partition is already half full,whereas your ubuntu partition is only using 5Gb,so moving the ubuntu partition should not take too much time.Also linux on the whole will require less disk space than vista.

But again only you know what your requirements are about how you are going to use the different operating systems so only you can decide the best options for yourself.

Anything is possible. Good Luck

---

### Post by caljohnsmith on 2008-12-26
> **Senesence said:**
> 
Although, I appreciate the heads-up on the lengthy data copy that would have to be executed if partitions were resized by moving their "starting point" - I sort of assumed as much.

Just a small note, because I don't want to mislead you in case I wasn't clear; only Windows is really sensitive to having the beginning point of its partition moved, not linux. If you want to move the starting point of any linux partitions, that in itself should not be a problem :)
> **Senesence said:**
> 
**@Everyone**

I only have a few more questions, and then I'll mark this thread as solved. If I understood you guys correctly, these would be considered safe procedures:

[LIST=1]
[*]Shrink /dev/sda1 to make the second unallocated chunk larger.
[*]Make the resulting larger chunk into a new partiton to host some other distro.
[/LIST]

Am I assuming correctly?
If you want to shrink the Vista partition, it is safer to use Vista's Disk Management to do so. One of the forum members, meierfra, recently did a few experiments about shrinking Vista with gparted (Ubuntu's partition editor); at least in his case, he found the issue was if the Vista partition originally used a HDD geometry (CHS or cylinders/heads/sectors) different from Linux's standard, then when you go to resize the *end* of the Vista partition, gparted will also nudge the *beginning* of the Vista partition so that the Vista partition falls on a cylinder boundary according to a Linux CHS geometry. He found that you can circumvent the problem by unchecking the "Round to cylinders" option in the gparted resize dialog box. So it would be safer to use Vista's own Disk Management to shrink Vista, but if you want to use gparted, I would recommend unchecking the "round to cylinders" option; if you take that precaution, I think most likely you should be fine. Good luck and let us know how it goes. :)

---

### Post by Senesence on 2008-12-26
[quote=plucky]From your screenshot,it makes more sense to not touch your vista partition but incorporate the unallocated space into the extended partition and shrink the ubuntu partition to make enough space for a new distro.This also leaves you with the capability of adding another primary partition in the future.[/quote]

Right. Actually, I decided not to touch the unallocated "gaps", and instead went on to just shrink my ext3 filesystem to make room for another logical partition.

*For those interested, the new allocation can be seen in the attached screen-shot.*

The gaps are only a few MBs, so they don't really bother me; I was just wondering if that was something that gparted did for a reason, but ultimately my plan was simply to create a "sand-box chunk" for distro testing, without messing up any other areas.

Anyway, thanks to everyone who pitched in. I learned a lot.

---

### Post by kansasnoob on 2008-12-26
Quite simply:

Don't sweat it!

I never see that happen on my newer drives, but my older hard drives show that a lot.

It has something to do with "rounding to cylinders", but when I've chosen not to do that things do NOT work out well!

Just consider them tiny spaces that the DRIVE decoded NOT to use to ensure the integrity of the data!

---

