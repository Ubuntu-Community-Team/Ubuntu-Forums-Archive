---
title: "Raid 1 Question."
date: 2009-05-18
forum: New to Ubuntu
---

### Post by DBrocks on 2009-05-18
Hey guys, I got a question for you.
I'm planning out building a media server for my house, and I want to run a software RAID 1 (2x1tb) with mdadm. After doing my homework pertaining to RAID, I stumbled across something from WD (the manufacturer I'm planning on using). They sell 2 different drives, one for standard use and one for RAID. The only difference between the standard and RAID edition is that in the RAID version, it disables Deep Recovery Cycle. Deep Recovery Cycle normaly runs for about 30-40 seconds, and this can cause the array to detect a problem, and drop the drive out of the array. In the RAID version, the Deep Recovery Cycle is limited to 7 seconds, which will prevent the RAID array from dropping the drive. I want to know if mdadm has a way of changing the time a drive is detected "dead" before it fails? If not, I guess I will shell out the extra dough for RAID edition. Thanks in advance!

---

### Post by DBrocks on 2009-05-18
Solved.
Turns out the problem is caused by WD's TLER (Time Limited Error Recovery). TLER is enabled in the RAID edition HDDs, and limites the time for bad-sector recovery to 7 seconds or less, thus preventing the drive from being dropped from the array. TLER is enabled in the (more expensive) RAID edition drives, but disabled in (less expensive) normal desktop drives. Western Digital offers a utility that allowes you to enable/disable TLER on your disk. Anyone interested in it can google it or email WD. Also, If you are planning on building an array out of Desktop Drives, check out DBAN to completly 0 out your drive and fix any bad sectors before using this utility. DBAN in conjunction with enabling TLER will preserve the robust-ness of your RAID. If you are a business/corporation with alot of money, invest in the YS series of WD drives. More expensive, but with a larger cache, 5 year warrantee, and TLER enabled by default.

---

