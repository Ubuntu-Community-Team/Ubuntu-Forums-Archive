---
title: "Having a couple problems..."
date: 2010-04-28
forum: New to Ubuntu
---

### Post by Saito Chikara on 2010-04-28
Okay, I'm having two problems at the moment...


1: My husband's laptop has Kubuntu and Windows installed, and he wants Kubuntu gone without re-installing windows. We have no way to back up the data. 

and

2: I need to put windows back on my desktop PC for some specific software needed for my culinary courses. Is there some way I can make a partition that won't get formatted with a re-install of windows, that I can place all of my files in, and be able to access it from windows? As stated before, I have no way to back up my important data.
Thanks to anyone who can help me!

Warm Regards,

Saito

---

### Post by jvc26 on 2010-04-28
> **Saito Chikara said:**
> 
1: My husband's laptop has Kubuntu and Windows installed, and he wants Kubuntu gone without re-installing windows. We have no way to back up the data. 


Right, well, for a start, would be good to know whether his data on the windows partition or on the kubuntu partition.

J

---

### Post by Saito Chikara on 2010-04-28
His Kubuntu is empty, Windows has all the files he wants to keep.

---

### Post by Saito Chikara on 2010-04-28
Seriously, could someone give me a hand please?

---

### Post by k3rnelmustard on 2010-04-28
What do you mean you have no way to backup the data?  What are you looking for, a backup program?  This is a one-time backup or on-going?  If it's one-time, just boot-up into windows, kubuntu or a livecd and copy the files you want over to somewhere that's safe.  If I'm not understanding the question correctly, please clarify.

If it's on-going, all I do is write a quick script that uses robocopy on the folders I want to sync to sync them to another drive, and run this as a scheduled task daily.  I've tried a few windows GUIs, but haven't found one I like.

As for a partition that won't be wiped, sure, just create the partition at the END of the drive (windows likes being installed at the beginning) and just choose the empty partition to install windows to, it won't erase the other partition unless you tell it to.

---

### Post by Saito Chikara on 2010-04-29
By "Backup" I mean, what I want to do, is make an empty partition for Windows, install it, and make a second partition for all my data, (because I don't have an external Drive or anything), remove Ubuntu, and merge the two partitions (Windows, and the cleaned Ubuntu Partition), or just have the clean partition as "another drive" as it were, under My Computer (C:, E:, F:, etc.).

---

### Post by PriceChild on 2010-04-29
1. Follow the instructions at [http://support.microsoft.com/kb/307654/](http://support.microsoft.com/kb/307654/) to run the **fixmbr** command. Once done, ensure that windows boots normally "as though Ubuntu weren't there". Once you are sure that that is the case, you may delete the ubuntu partition using your favourite tool.

2. Yes, see [http://support.microsoft.com/kb/313348](http://support.microsoft.com/kb/313348)

---

### Post by eriktheblu on 2010-04-29
If your culinary software is not graphically heavy, and you have a sufficiently powerful machine, it might be easier to virtualize instead of setting up a dual boot.

---

### Post by roger_1960 on 2010-04-29
Hi

If you have no other way to backup why not use dropbox [www.getdrpbox.com](www.getdrpbox.com) or even ubuntuone?  You really should backup before repartitioning...

---

