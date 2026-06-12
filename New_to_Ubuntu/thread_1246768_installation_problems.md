---
title: "installation problems"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by impatientboi on 2009-08-22
hi all
I have had trouble installing unr. I am using an asus 1000h. before installation it had two partitions 1. the xp installation and 2. an additional unused partition.
Rather than use the whole partition i manually selected a smaller partition, and made it to step 5, where u enter in the details, changed my mind about the computer name, hit back, but by this stage the partition that i had selected had already been created, and was labelled (unavailable!) free space, which i was unable to install ubuntu onto in my second attempt, 
i selected a different partition size, next to the free space, hit forward and away i went. 
i left it on overnight to install as it was taking some time, went to sleep, but in my haste knocked out the power cord so of course the install didn't complete, and i know have both these sections of my hdd as "Free space." The only positive for me at this stage is that I hadn't chosen to use the whole partition lol. 

So I tried it a third time, third time is a charm . . . kind of. i am upto step 5 where you enter in your name pc name etc, i pushed next, and now the computer has been churning away for close to 7 hours, which i would have thought was a bit excessive. the flash drive and hard drive sound like they're working like they do when you are doing something heavy duty, but for all i know it's stuck on a loop. Comments/Advice/suggestions anyone?

Secondly, as I haven't completed the installation i can't access 

Given that i haven't been able to successfully install i can't have a look at the drives and partitions re: free space. If anybody has been in a similar circumstance what was the end result. I noticed using the live cd there is a partition management program included. Does anybody know whether it might be able to help in my scenario? I know there are lot's of maybes . . . any advice appreciated

---

### Post by powel212 on 2009-08-22
Boot xp

go to the native partition editor, (right click computer and launch "manage")

Look at your partitions. Organise them, (delete and consolidate any unused partitions, at this point you should only have the one windows partition, everything else can be safely deleted).

Create one and only one partition that is "unformatted space" All other partitions must be formatted in some way, probably ntfs or fat for the windows partition, do not reformat the windows partition. 

boot the live cd

when you get to the partition section of the install select use "largest continuous free space"

do not adjust the slider.

This will install ubuntu to the unformatted free space we created earlier in XP and will give you a nice clean dual boot.

Once installed and running please use Add/remove to install "ntfs-config" then launch it from "system/administration/ntfs-configuration tool"

then on your next boot your windows partition will be mounted to your desktop.

I hope that helps

Powel

---

