---
title: "corrupted files defrag?help"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by benkempf on 2010-12-25
ok... heres my situation.... was using windows 7 on laptop, had some boot issues at start-up, could not get the os to work from either the disk or the hd... booted ubuntu from disk, but os will not reboot from hd... ran a system test and it shows 411 bad sectors.  I cannot run computer janitor, the error message reads:   Essential package dash is missing. There may be problems apt sources.list or Packages files may be missing?...   what do you suggest? is there a way to defrag the disk? how can I fix? is this a major hardware problem?

---

### Post by mikewhatever on 2010-12-25
The one and only thing you should try to do is backup if that is still possible. Just copy whatever files you need using the live cd. After that, run a filesystem check which may or may not fix the problem. Those are general suggestions, since you haven't said clearly what file system or OS give you the problems. Choose your tools accordingly and don't waist time on running janitors or defragmentors.

---

### Post by NightwishFan on 2010-12-25
Go to System -> Administration -> Disk Utility. Computer Janitor does not defrag nor would that help. Find your disk and review the smart data for it. I agree with the user above, save the important data and run a check.

---

### Post by benkempf on 2010-12-25
well luckily it is just a laptop for my sons school work so there really isn't anything important on it... however, I already did a smart scan, thats where i got the previous information regarding how many bad sectors there were, but it won't let me do anything that seems like a "problem solving" test... I'm really  a beginner in linux and am easily confused by exactly what I am doing...

---

### Post by NightwishFan on 2010-12-25
That is quite alright. Bad sectors are a sign the disk is ready to fail though. So it might need replacing soon.

---

### Post by dFlyer on 2010-12-25
Time to backup data if possible and replace the drive.

---

### Post by benkempf on 2010-12-25
computer is 4 mos old!    and these are obviously big issues if I can't get the computer to boot up... last time I check that was pretty important      :P

---

### Post by benkempf on 2010-12-25
error checking file system  " Device is mounted and no online capability in fsck tool for file system "

---

### Post by NightwishFan on 2010-12-25
You need to unmount a filesystem to check it.

---

### Post by benkempf on 2010-12-25
Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=bced0ae3-c5d7-43f6-8cf8-7c1b8a8260f9 from /

---

### Post by mikewhatever on 2010-12-25
Actually, bad sectors are not necessarily a sign of disc failure. A manufacturing defect can render some sectors unreadable, they are then marked as bad, and the hard drive keeps working. If the number of bad sectors climbs, that's a different story.

Note for the OP. Ubuntu is not a Windows7 recovery tool. Please use appropriate Windows tools to solve Windows related problems.

---

### Post by NightwishFan on 2010-12-25
True, but that along with the other problems he has been mentioning, of course.

Also, to umount a disk you need to be root, if you are doing this from a life CD press alt+f2 and input the command below and hit run.
```
gksudo palimpsest
```

Then you should be able to unmount the disk from that interface.

---

