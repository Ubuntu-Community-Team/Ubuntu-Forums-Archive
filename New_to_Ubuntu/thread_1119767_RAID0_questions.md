---
title: "RAID0 questions"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by furialis on 2009-04-08
I'm planning on setting up a RAID 0 array using two [SSD](http://benchmarkreviews.com/index.php?option=com_content&task=view&id=318&Itemid=60) drives and this being my first time I have a few questions.

My bios supports RAID, but I was told unless I was dual booting, I should use software to control the RAID array. What's the difference between Native IDE mode and ACHI? Is there a HOWTO?

Also the SSD drives are recommended to be formated with a different [geometry](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379) than standard. Do I make those adjustments with a LiveCD and then install without formatting? 

Thanks in advance.

---

### Post by ronparent on 2009-04-08
First point: The live cd will do you little good in installing to a raid array. The software/drivers are not included on the standard distro. 

Secondly, raid0 is a so called stripped array. It is reputedly 'faster' than a standard drive, but, the speed improvement is marginal. Using it without a solid back-up strategy is dangerous. The failure of one drive will wipe out all data on BOTH DRIVES.

This is not to discourage you from proceeding but a caution that an install will have to be from an 'alternate cd' and that you will probably hqve to read up on it beforehand. I have winXP installed on my raid0 array, but ubuntu installed on a seperate IDE to avoid the hurdles.

---

### Post by mazato on 2009-04-08
It's better if you use RAID 5

---

