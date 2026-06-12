---
title: "Ubuntu gets slow like Windows over time ?"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by Delawaredave on 2009-05-28
Installed Ubuntu - it "zipped" and responded quickly.  I never installed any additional programs (don't know how).

Over time (6 months approx.) the system is no longer as fast as it used to be. 

Is this common ?  Any maintenance (disk defrag,etc) I need to be doing ?

Thanks.

---

### Post by Paqman on 2009-05-28
> **Delawaredave said:**
> I never installed any additional programs (don't know how).


Just go to Applications > Add/remove and pick some! 

> 
Over time (6 months approx.) the system is no longer as fast as it used to be. 

Is this common ?  Any maintenance (disk defrag,etc) I need to be doing ?


As an experiment, can you create a new user account (System > Admin > Users & Groups) and log in to it. Is it quicker than your other one?

As for defrags, the default filesystem doesn't really get that fragmented, so there's no real need to manually defrag it. Maintenance-wise the main thing is to keep installing the updates you receive. Some people go around and clear out unneeded files every so often, but that's just a tidiness/disk space thing rather than to help performance.

---

### Post by Vunutus on 2009-05-28
Ubuntu (for the most part) does not clutter itself in the same way Windows does. Left alone, the operating system will run virtually unchanged. Ubuntu, by default, uses the ext3 file system which will not fragment itself in the same way NTFS does. ext3 only encounters fragmentation when operating at near-full capacity (90% and up generally).

Over time, natural usage of Ubuntu does generate a lot of excess filesystem junk that could theoretically slow down operation. Check out [this]("http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07/") link to see a few ways to clean that up.

Other considerations in Ubuntu slowing down are major system changes like upgrading distro versions. Some people report lots of quirky issues like lag and other slowing downs after distro upgrades, particularly with the Jaunty upgrade.

---

### Post by freeman2000 on 2009-05-28
> **Vunutus said:**
>   Check out [this]("http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07/") link to see a few ways to clean that up.  


Go to that link and pay particular attention to items #3 & 4.  That will get rid of most of the unnecessary stuff. Also go to System --> Preferences --> Startup Applications and un-click any apps that you don't need to run at startup.  These processes eat up RAM as you work.  Good luck.

---

### Post by Steelmourne on 2009-05-28
Watch out that you don't disable essential services by mistake. Most of the services don't take much RAM anyway.

---

