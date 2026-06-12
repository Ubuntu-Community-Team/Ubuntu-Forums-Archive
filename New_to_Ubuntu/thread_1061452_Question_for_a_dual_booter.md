---
title: "Question for a dual booter"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Atallicus on 2009-02-05
I'm not even entirely sure if this has anything to do with Ubuntu, but I thought I would throw it out there in case anyone else has had this issue.

I have 4 hard drives in my computer, 1 with windows Vista on it (C), 1 with all my stuff on it for windows(D), 1 with Ubuntu 8.10 on it, and 1 that is unused(had linux on it).

Here's my problem. When I log into Windows, it keeps trying to tell me that the D drive is not formatted. The only way to fix it is to log into Ubuntu, mount it, and log back into Windows. The drive works until the computer is shut off, then if you turn the computer on and go back to windows, it tells me again that the drive is not formatted, even though I can go to Ubuntu and see the data on it just fine.

Has anyone ever had this problem? Any idea how to fix it? I'm basically afraid to use the D drive at all for fear this problem is going to wipe the drive. Any help you could offer would be great. Thanks.

---

### Post by raydeen on 2009-02-05
Try doing your little trick to get it working with Windows and then log into Windows and do a disk check on that drive (or schedule one at boot up if necessary). There might be something funky with the partition or file structure. I haven't played with Vista but if it's like XP, right click the drive and choose Properties, look for a Tools tab, and then for an Error Checking box. It will take a while, but I'd recommend a full check (surface scan).

---

### Post by Atallicus on 2009-02-05
Scanning it now, I'll let you know in a few :D

---

### Post by Atallicus on 2009-02-05
Ran the full scan and no errors were found with the drive.  Any other suggestions?

---

### Post by raydeen on 2009-02-05
Bit of a head scratcher there. I Googled a litte bit and there seems to be a Vista issue that can pull up this error. My advice would be to format that 4th drive that used to be Linux to NTFS and copy everything from D: to that drive just in case there's something going wrong with D:. The only things that I can think that are happening are A.) the drive letters aren't being correctly assigned when initially booting into Vista or B.) Vista isn't properly writing drive info when shutting down. In any case, backup your stuff while you can.

---

### Post by Atallicus on 2009-02-05
Well thankyou for looking around on google for me.  I googled what I could but it's such an odd error to search for.  I have my stuff backed up on the first linux drive and the c drive also, we may have to set up that 4th drive to add a backup to until we get this sorted.  My husband is the genius with this stuff so he's going to try plugging that hard drive into different ports to see if it's the drive letters.

Thankyou for your help, I'll try to keep you posted :D

---

### Post by Kellemora on 2009-02-06
Hi Attallicus

I think the problem may be that your Ubuntu drive is formatted in EXT3 which is GREAT for Ubuntu, but the Doze can't see it.

I know how one other fellow fixed this same problem, but don't know if you want to go through that much trouble or not.

What he did was shift all the partitions to the right and added a new very small 100MB Partition 1 (sdb1) and formatted it to NTFS.
What I don't remember is if he added anything to this partition or not.  And I don't know how it stopped the Doze from looking at the second partition and saying it was not formatted.

TTUL
Gary

---

