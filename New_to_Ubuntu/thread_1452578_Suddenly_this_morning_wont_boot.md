---
title: "Suddenly this morning wont boot"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by old_dog on 2010-04-12
Although I have been using Unbuntu a few years...I am just a desktop user if you get my drift. I am on 9.10 and have been so for months, this morning starts to boot and everything comes to a standstill with the following message:
ALERT! /dev/disk/by-uuid/0ad13337-0f9d-4f03-a7fb-c8b51186b4b9 does not exist dropping to shell
(intraamfs)
What is it trying to tell me? and more importantly how do I recover?
Help old_dog

---

### Post by readycarpenter on 2010-04-12
well for some reason your ubuntu partition will not mount, this could be software related. did you do anything, alter anything, or upgrade recently say since the last successful boot?

if not I believe it is a hard drive failure.

if you still have your ubuntu install disk, boot it and see if your drive shows, and then run system>admin>disk utility, this will tell you is there are errors on your drive.

cheers

---

### Post by J V on 2010-04-12
Yes, please load a live disc open a terminal and paste in: "fdisk -l"

Send the results here...

---

### Post by old_dog on 2010-04-13
Thanks Guys...........
As in the past have had a few messages about dodgy bits of disk I decided to go for a new install...Worked very well actually reduced the old Ubuntu partition down to its minimum size and created a new partition that I am working from now. The good news I can mount the file system in the old partition and access all my old files!!!
Simplistic solution but I regard it as a spot on result.
Cheers old-dog

---

### Post by airtonix on 2010-04-13
**Suddenly this morning wont boot**
Yep, four days ago i tried to boot the evening... the moon just laughed at me.

I wasn't brave enough to try booting the morning.

---

