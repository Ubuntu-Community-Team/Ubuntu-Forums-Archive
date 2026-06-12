---
title: "Recover Data from RAID 1 with Ubuntu?"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by x C0MMAND0 x on 2011-06-28
I am working on a client computer that completely crashed and will not boot, won't even go to bios so I can not use a live-cd to do anything.  There are 2 hard drives that were setup in a RAID 1 configuration.  

I am wondering if there is any software/tools/anything that will let me mount one of the drives externally?  One of the drives is currently showing up as "ddf_raid_member".  Is there a way to get into the drive from a different machine?

Any help/thoughts/suggestions/ideas are appreciated,

Thank you.

---

### Post by jtarin on 2011-06-29
Can you not mount both drives? What is preventing you?
[Breaking the mirror]("https://encrypted.google.com/#sclient=psy&hl=en&source=hp&q=breaking+raid+mirror&aq=f&aqi=g1&aql=&oq=&bav=on.2,or.r_gc.r_pw.&fp=386d06466be45f5e&biw=1366&bih=639")

---

### Post by x C0MMAND0 x on 2011-06-29
I can only mount them externally on another machine; the machine in question does not boot up at all, so I can not get into the interface controls at all to do anything with.

Additionally, after mounting each of the drives separately, the partition tables are completely different which leads me to believe that they may not be set up in a mirror but they are set up in RAID 0 where part of the data is on each of the hard drives...

I'm not sure how I would be able to mount them together on another machine without the RAID controller, because the controller is built into the motherboard on this particular system; it is not a  PCI or other that can be transferred to a working machine.

Any other thoughts/ideas?

---

### Post by jtarin on 2011-06-29
> **x C0MMAND0 x said:**
> 
I'm not sure how I would be able to mount them together on another machine without the RAID controller, because the controller is built into the motherboard on this particular system; it is not a  PCI or other that can be transferred to a working machine.

Any other thoughts/ideas?I can only think the only possible way from another machine is with that same model MB.There could be another way...I don't know.

---

### Post by collisionystm on 2011-06-29
> **x C0MMAND0 x said:**
> I am working on a client computer that completely crashed and will not boot, won't even go to bios so I can not use a live-cd to do anything.  There are 2 hard drives that were setup in a RAID 1 configuration.  

I am wondering if there is any software/tools/anything that will let me mount one of the drives externally?  One of the drives is currently showing up as "ddf_raid_member".  Is there a way to get into the drive from a different machine?

Any help/thoughts/suggestions/ideas are appreciated,

Thank you.

It was a hardware raid, therefore the same RAID controller needs to be in place to read the drives. 

Replace the Motherboard to get the data.

---

### Post by x C0MMAND0 x on 2011-07-07
Okay, we did replace the motherboard in the computer, and when it boots up bios and the raid management utility both show the drives as setup properly in RAID 0.  I am able to boot to a live Ubuntu CD, but looking at the computer the drives don't show up together at all.

Listing an fidsk -l shows each drive individually.  The system sees the drives, but does not see them together as they should be.  I am unable to mount each drive individually as they need to be mounted together.

Any ideas/thoughts on how this can be done?

Thanks for the help so far.

---

