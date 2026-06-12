---
title: "If I buy another hard drive and Install Ubuntu on it"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by psam3 on 2009-08-03
Will Ubuntu still make the grub list and will it include Windows Vista even if it is on a different hard drive? Is there anything I should know ahead of time if I want to dual boot by using two hard drives? 

Thanks

---

### Post by oldfred on 2009-08-03
It found my XP without problems, I assume it will find Vista also.
Think about how you want to partition your drive. Default works, but some suggest a separate /home so when you do a major update your local configurations and files do not change. If you think you may install several different distributions you should keep /home in root and make a /data for data but the config files may be different and should not be in a common /home. If not sure you can keep some space unallocated for future use.  I like to manually partition and do manual install but if it is you first install selecting defaults is probably best. 
Partitioning:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
Dual boot:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
More directed to one drive but useful to review:
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

---

### Post by psam3 on 2009-08-03
> **oldfred said:**
> It found my XP without problems, I assume it will find Vista also.
Think about how you want to partition your drive. Default works, but some suggest a separate /home so when you do a major update your local configurations and files do not change. If you think you may install several different distributions you should keep /home in root and make a /data for data but the config files may be different and should not be in a common /home. If not sure you can keep some space unallocated for future use.  I like to manually partition and do manual install but if it is you first install selecting defaults is probably best. 
Partitioning:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
Dual boot:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
More directed to one drive but useful to review:
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

Thank you for your tips. I have always dual booted from one hard drive and wasn't sure if it was quite the same. I may install other distributions, there are some I'm interested in such as Fedora and OpenSuse, although I like Ubuntu the best really out of all that I have tried.

---

### Post by powel212 on 2009-08-03
If you want to try Suse and Fedora I would suggest trying them in a virtualbox before installing them to the boot disc. Then you can at least see if you like it before you commit. There are a lot of Linux distros out there and it is much easier to test them in a virtual environment first.

I run a windows 7 guest in a virtualbox instead of having a dual boot. Also a great way to test for viruses. 

I hope that helps. 

Powel

---

### Post by Numer0bis on 2009-08-16
maybe he wants to try out how good the distro works with his hardware and in that case there is actually no way around installing it into different parition except maybe trying out the live cd first.

---

