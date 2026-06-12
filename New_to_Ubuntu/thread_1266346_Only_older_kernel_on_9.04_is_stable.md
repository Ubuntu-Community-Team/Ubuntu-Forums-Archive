---
title: "Only older kernel on 9.04 is stable"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by StevenUnderwood on 2009-09-14
Linux noob here so it might be something I am doing but here goes...
 
I have an old Dell Inspiron 5000 I was given and am trying to get Linux on to learn, play, and have an additional internet machine for the kids.  After several failed attempts to install 9.04, I was able to install 8.04LTS with no problems and that was working for a couple of days without issues.  Last Friday, I upgraded to 8.10 and used that for a day with no issues.  
 
Over the weekend, I attempted the 9.04 upgrade and did not see any issues during the upgrade or when I installed all the patches.  
 
A short while later, while rebooting, the machine appeared to hang (left it for ~10 minutes with no activity seen).  Tried the recovery kernel option (2.6.28-15) and it would get to the same place every time, but the section it was working on seemed to have scrolled off the screen.  Next I tried the next older kernel (2.6.28-11) and it booted the first time but would again hang on booting a majority of the time and the recovery mode shows it hanging at the same place.  I tried the 3rd kernel (2.6.27-7) and it seems to be stable but I was reading up on that kernel and it seems there was a major bug fixed, so it seems wise to upgrade.  I have searched here and the internet as a whole and am not seeing anything similar, so I am afraid it might be this laptop's hardware, even though the older kernel seems to be woring fine.
 
1. Is there a log generated on the system somewhere to determine why the newer kernels are hanging?  Please point me to the specific location if so.
 
2. Has anyone else seen something similar that I have missed in my searches?  Any troubleshooting methods to try?  Again, specifics would be appreciated.
 
3. (real noob question here) Is it still recommended to compile my own kernel (I did that once with slackware MANY moons ago, the last time I had available hardware and time)?  I do not see that mentioned much anymore.
 
Thank you for your time.  If this question is too adanced to get a good response in this forum, please move it to a more appropriate one.

---

### Post by zerhacke on 2009-09-14
The best advice I think I can give you is to go back to 8.04LTS and leave it at that.  It will be supported longer than 9.04 is going to be so you're going to get a computer that works AND support for longer time than you will with the update to 9.04.

---

### Post by NightwishFan on 2009-09-14
Some kernels just seem to hate some hardware. Short term solution? Use a kernel that works. I had a laptop that would not upgrade to Intrepid, because the kernel would not use the harddisk. I was forced to use the Hardy kernel, until a new kernel patch came out.

Please note I am not an expert, so perhaps wait for another Ubuntu forum Jedi Master to answer you.

---

### Post by StevenUnderwood on 2009-09-14
> **zerhacke said:**
> The best advice I think I can give you is to go back to 8.04LTS and leave it at that. It will be supported longer than 9.04 is going to be so you're going to get a computer that works AND support for longer time than you will with the update to 9.04.
OK, but I upgraded mostly because 8.04LTS only had FireFox 3 Beta5 and was showing me no updates.  Is there a supported way to get a newer FireFox version on 8.04LTS?  All of the sites I saw on using FireFox direct releases suggested not doing that but instead waiting for the Ubuntu release.

---

