---
title: "Accidentally deleted /etc/init/ folder."
date: 2010-10-23
forum: New to Ubuntu
---

### Post by Lightsword on 2010-10-23
Hi everyone, I'm just getting started with Ubuntu, and linux in general. I was in the process of creating a media server using the ubuntu desktop edition. My filesystem is a software raid1 that I installed ubuntu on using a live CD and mdadm. 

While trying to remove a networking program, I accidentally deleted the /etc/init/ folder by issuing the rm -r /etc/init/ while logged in as the root user. As far as I can tell, I deleted the actual init folder instead of the init.d folder; because the init folder didn't show up when examining the /etc/ folder using the ls -a command. 

I haven't restarted the system or made any major changes; and I was hoping someone could give me some guidance in what to do next. Ideally I would like to be able to recover all the files and continue on. I know that apt-get is still working so I can download from the repositories; but the system acts like webpages won't load in any of the browsers. 

Before posting, I did some research on google, and searched the treads but couldn't find any exact matches to my problem. ](*,) I hope I posted this to the correct thread, but if not, would someone tell me where to post it? I really would appreciate any help or suggestions anyone has to offer. 

Thanks! 
Lightsword :-)

---

### Post by spikoley on 2010-10-24
WOW!!!  That is a big mistake.  If you reboot it might cause some big issues.  There really isn't a fix for something like this.  You could try booting into the live CD and then copying the files from the live CD to the hard drive.  Its worth a shot.

---

### Post by trikster_x on 2010-10-24
Have you managed to fix this problem yet?

---

### Post by Lightsword on 2010-10-24
Well, my fix is to reinstall the OS. The system was a RAID 1 array, and after I rebooted the system I couldn't mount the RAID array so no copying files at all. couldn't seem to get anything else working with the limitations of hardware for backing up the data, and I couldn't find any other solutions that appeared workable. I've already formatted the disks and I'm going to reinstall here soon. Thank you for asking.

---

### Post by trikster_x on 2010-10-24
Okay, I was just going to suggest I send you a /etc/init archived from my install, since it seems like everything in it is pretty much a standard for all comps, but if you already wiped, nevermind.  Glad to hear you worked it out though.  Some people would have just let their comp run in the hopes there was an easy fix.

---

### Post by Lightsword on 2010-10-24
Thanks for the offer and I'll keep it in mind for the future. I would've just kept it up, but I didn't see any chance of recovery a few hours ago, so I decided it was time to begin rebuilding my software system. I'll remember that next time and leave it running longer before i do anything then :D

---

