---
title: "Trouble after 10.10 install"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by Alaex on 2010-11-11
Upgraded to 10.10 on two machines. One machine is fine and performs well, the other one (Core i7 960, EVGA MB, Nvidia) runs horrible. All the CPUs are spiked to almost 100% yet the process monitor shows nothing running. The machine lags terribly. Must be some issue with this hardware combination as it does not happen on my other machine. Is there a way to remove 10.10 and revert to 10.04LTS until there is a fix? I would start over, but the machine is dual-booting win7 and I do not want to crash my boot manager and lose my Win7 build. So basically downgrade to 10.04LTS.. Is this possible?
Thank you :)

---

### Post by kesman on 2010-11-11
Have you applied all updates? Maybe a new kernel has better support for the cpu.
Also upgrading isn't as good as a fresh install, so you might want to try that too.

---

### Post by Alaex on 2010-11-11
I did apply all updates. I read on EVGA forums that it may be an issue with X58 hardware and the present kernel. If I boot to the earlier kernel it is ok. The very latest kernel causes issues.

---

### Post by Alaex on 2010-11-11
And yes, I would love to do a fresh install, I am concerned about my dual boot scenario and cannot afford to lose my ability to boot into Windows 7.
Thank you for the quick reply.

---

### Post by rmockler on 2010-11-11
I am dual booting Win 7 and various Linux distributions as well.  I have deleted the Linux partition several times in the past few months to install another version of Linux, and whenever I installed a new distribution in the unused space, the boot manager has been completely rebuilt each time without problems, and Win 7 continues to function just fine.

---

### Post by [::AP::] on 2010-11-11
Best of luck, and I am not sure if this will help you - 
 
 
There shouldn't be a problem with the partition. You just need to shrink your Windows Se7en partition (if neccessary). Unless it is full, you should not expirence loss of data. 
 
A clean install should work without problem. 
I did a fresh install of 10.10 last night, no problem. I just reformatted my partition, and installed with the disk. I had no issues with booting into Windows. 
 
Best of luck (again),
 
[::AP::]

---

