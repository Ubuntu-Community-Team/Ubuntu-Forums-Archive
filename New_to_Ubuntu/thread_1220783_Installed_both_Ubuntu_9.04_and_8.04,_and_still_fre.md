---
title: "Installed both Ubuntu 9.04 and 8.04, and still freezes"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by jestonb on 2009-07-23
Hi,
 
I am trying to install and run Ubuntu on a Sony VAIO PCG-K17.  I have installed both 9.04 and 8.04 (at seperate times), I have run from the live disk, and I have logged in just the terminal.  No matter what I do the system just freezes on me after a few minutes (some times really quick sometimes after 10 minutes).
 
Ideas?  Am I doing something wrong?
 
Also I read that it might be the ATI card, I have tried to download and run envyng but it always freezes up before I can finish.

---

### Post by ajgreeny on 2009-07-23
Start in recovery mode and try to install the envyng packages you need with the console that recovery mode gives you with ```
apt-get install envyng-core envyng-gtk
```It's so long since I had to use it that I can't remember if you need sudo or not for that command, but if it doesn't work without sudo, try with.

Good luck with this.

---

### Post by philinux on 2009-07-23
> **jestonb said:**
> Hi,
 
I am trying to install and run Ubuntu on a Sony VAIO PCG-K17.  I have installed both 9.04 and 8.04 (at seperate times), I have run from the live disk, and I have logged in just the terminal.  No matter what I do the system just freezes on me after a few minutes (some times really quick sometimes after 10 minutes).
 
Ideas?  Am I doing something wrong?
 
Also I read that it might be the ATI card, I have tried to download and run envyng but it always freezes up before I can finish.

How did the live cd run?

---

### Post by kpkeerthi on 2009-07-23
Deactivate the ATI driver from System -> Admin -> Hardware Driver and then try with envy whatever. 

Note: The driver will **not **be listed in Hardware Drivers if you installed it using other non-recommended methods.

---

### Post by jestonb on 2009-07-23
Thanks all, 
 
It still freezes running the live CD.  Got the envyng core to download and start, now I'm uninstalling the ATI driver with Envy, we'll see what happens.

---

### Post by Mark Phelps on 2009-07-23
According to Google, your laptop is running an ATI Mobility Radeon chip from 2004 -- which is no longer supported by AMD/ATI with restricted drivers.  If you force an install through EnvyNG or by running a driver installation from AMD, you most likely won't get any working video.  You're stuck using the open source drivers -- which are installed by default.

---

### Post by jestonb on 2009-07-23
Sure enough the everything froze when I ran Envyng.  Mark you are correct that is the card that I'm running.  I've tried just running the default drivers and everything still freezes.  Is there something else that I should be checking?

---

### Post by LewRockwell on 2009-07-23
you might want to take a look at...and bookmark this page

[http://esupport.sony.com/perl/swu-list.pl?mdl=PCGK17](http://esupport.sony.com/perl/swu-list.pl?mdl=PCGK17)

.

---

### Post by jestonb on 2009-07-23
> **LewRockwell said:**
> you might want to take a look at...and bookmark this page

[http://esupport.sony.com/perl/swu-list.pl?mdl=PCGK17](http://esupport.sony.com/perl/swu-list.pl?mdl=PCGK17)

.

Am I missing something this only has window XP info.  Are there other reasons than the ATI driver that would make ubuntu freeze all the time?

Thanks

---

