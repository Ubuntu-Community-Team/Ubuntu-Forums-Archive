---
title: "Cannot Resize Partition"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Bandanna on 2009-01-15
I'm using an HP Pavillion dv1000
I have downloaded ubuntu 8.10 and burned onto a disc
When I boot from disc and run installation at step 4/7 
I pick guided partition as it looks most suitable because I want to dual-boot windows XP + Ubuntu.
I get an error saying that it can not resize the partition.

I have a clean install of XP on my computer, defragging is not necessary.
I have ran CHKDSK /l and CHKDSK /R rebooted and tried reintalling ubuntu, no success.
I have opened live version of ubuntu used the Gparted application and received same error that occurs during installation.

I have googled and found out that many people have problems partitioning the dv1000.

I'm at a loss... help would be appreciated, thank you.

---

### Post by vegetarianshrimp on 2009-01-15
Maybe [this]("http://gparted.sourceforge.net/") will help?

---

### Post by earthpigg on 2009-01-15
> **vegetarianshrimp said:**
> Maybe [this]("http://gparted.sourceforge.net/") will help?

he is already using gparted... and it should work ok if he is booting from live cd...

---

### Post by vegetarianshrimp on 2009-01-15
Oh right. Sorry. I did not read his/her post well enough. lol

---

### Post by Bandanna on 2009-01-15
If I try to use Gparted to make about 45GB of Unallocated space is there a way I can... like.. Get Ubuntu to install into that unallocated partition?
Or would I have to format it through computer managment and if so should it be into FAT32?
But if windows formats that partition won't it just act like A seperate hardrive running off my XP?

What to do??? I have 80GB disc space BTW

---

### Post by 2hot6ft2 on 2009-01-15
Can you take a screenshot of the partitions using the livecd and gparted so we can see what's going on?
System>Administration>Partition Editor
and
Applications>Accessories>Take Screenshot
You can save it to a flash drive or something so you can move it to an online pc and attach it to your post.

---

### Post by Bandanna on 2009-01-15
Just tried to shrink my partition and make some unallocated space no luck 
Ill go take screenshots now let me boot up CD again

---

### Post by 1packer on 2009-01-15
Is your xp partition mounted? I know a lot of people have issues using gparted when they haven't cleanly shut down their xp partition. In order to prevent data loss I would load Windows and then properly shut it down, to see if it works that way.

---

### Post by 2hot6ft2 on 2009-01-15
> **1packer said:**
> Is your xp partition mounted? I know a lot of people have issues using gparted when they haven't cleanly shut down their xp partition. In order to prevent data loss I would load Windows and then properly shut it down, to see if it works that way.
That's one of the things the screenshot will show along with any extended partitions.

---

### Post by Bandanna on 2009-01-15
OMG! Well, I went and took screen shots and everything but..
It didn't stay on my flash drive?????????????I definitely
saved it there because I checked before I rebooted.

...Whats happening is
Im opening Gparted
I have a large partition which is my system partition
and then I have a recover partition
I tried to shrink the large partition because I don't want to touch my recovery partition because I have no discs.
But I guess I can't shrink it and make any unallocated because it is my (system) partition.


In windows from computer managment It lists 3 partitions
C: system
D: recovery
1 gig unallocated space
I have the option to format and delete my recovery (d:) but not my system (C:)

---

### Post by 1packer on 2009-01-15
Does your large partition have some keys by the name? You can use firefox within the live cd, so you should be able to try a few times. I think there is a decent chance the problem is that Windows was not properly shut down. This would prevent you from saving to the internal hard drive.

---

### Post by 2hot6ft2 on 2009-01-15
> **Bandanna said:**
> OMG! Well, I went and took screen shots and everything but..
It didn't stay on my flash drive?????????????I definitely
saved it there because I checked before I rebooted.

...Whats happening is
Im opening Gparted
I have a large partition which is my system partition
and then I have a recover partition
I tried to shrink the large partition because I don't want to touch my recovery partition because I have no discs.
But I guess I can't shrink it and make any unallocated because it is my (system) partition.


In windows from computer managment It lists 3 partitions
C: system
D: recovery
1 gig unallocated space
I have the option to format and delete my recovery (d:) but not my system (C:)
What I think is happening is that there is an extended partition as well and the other partitions are inside it. Namely C and D are inside the other one making 3 partitions. The unalocated area is most likely before them.
Make sure you shut windows down cleanly as stated above. And you'll have to look at them. If any of the have keys icons by them then they are still mounted and can't be changed unless you unmount them which can be done by right clicking on them and selecting unmount.

If C and D are both at the beginning of the drive you may be able to resize the extended partition to the left once everything is unmounted.

If C is on the beginning of the drive and D is on the end and they are both inside an extended partition you may be able to move D to the left all the way next to C and then resize the extended partition.

Guessing here without seeing what's going on.

---

### Post by 2hot6ft2 on 2009-01-15
By the way with a new pc these days it's best to create the recovery dvd's first thing. Once they are created the recovery partition is pretty useless since that's what it's for is to create the recovery discs.

---

### Post by Bandanna on 2009-01-15
Here's some screen shots 

Pay attention to titles.

the last  one is the first step

then the top is second 
then 3rd and 4th as it goes down








----------------------------------------------------------------

I believe I fixed it, I just did a clean boot because I actually have been cold booting my laptop this whole time =/
*Feels not so intelligent now*
I'm shrinking the large partition now-
Actually it just finished thank your for the help guys.
I'm a dumb face =p
----------------------------------------------------------------

We'll see though I just now figured out how to repartition, I haven't began setting up ubuntu in a partition. So..
stay tuned please =]

---

### Post by Bandanna on 2009-01-15
> **2hot6ft2 said:**
> By the way with a new pc these days it's best to create the recovery dvd's first thing. Once they are created the recovery partition is pretty useless since that's what it's for is to create the recovery discs.

...No DVDS 
It takes 13 CD's =[
only 2 DVD's...
need to go to store I suppose Im  broke though.
Im only 16 no work during school year for me.

---

