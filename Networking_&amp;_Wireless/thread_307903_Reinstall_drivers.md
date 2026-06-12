---
title: "Reinstall drivers"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by luken8r on 2006-11-27
Ive been having some networking issues with my onboard Intel 82547EI ethernet connection and I would like to reinstall (or update) the drivers

1) How do you see what version of the drivers you are currently running

and 

2) How do I reinstall them?

---

### Post by az on 2006-11-27
> **luken8r said:**
> Ive been having some networking issues with my onboard Intel 82547EI ethernet connection and I would like to reinstall (or update) the drivers

I guess you did not try to recompile the drivers from source, correct?


> **luken8r said:**
> 
1) How do you see what version of the drivers you are currently running?

All those drivers are kernel modules and are part of the standard kernel.  You can probably see what version they are by looking in the logs.  You can check /var/log/messages or just type

dmesg

at the command line and scroll up - that is the log from the time you turned on your computer.

I am not sure, but perhaps the device manager will show you the module's version.


> **luken8r said:**
> 

2) How do I reinstall them?

Unless you removed or changed them, reinstalling them will do nothing - they are just files and since they have not been changed, there is no point.

If you did try to recompile something and borked up some modules, you can reinstall them by reinstalling that kernel

sudo apt-get install --reinstall linux-image-2.6.xx-xxx-xxxxx

where the Xs are the exact version number of your running kernel

use

uname -r 

to get that version.


So... exactly what is the problem with your ethernet card?

---

### Post by luken8r on 2006-11-27
> **azz said:**
> 
So... exactly what is the problem with your ethernet card?

Thanks for the suggestions. Ill give that a try

I posted my issue a few weeks back without any help, so here it goes again 

I lost power a few weeks ago and ever since, my network connectivity has been hit or miss. 
I try to go to a website or ssh or anything else using my eth connection and the first attmpt times out on me, but if i refresh, it goes through

For instatance, if I try to go to my home page in FF (or most any other site)  the first attempt at the site says it can not be reached, but if I refresh or go to the page again, immediately after, it goes through without an issue. Same thing with SSH; the first attempt at connection gives me a "resource unavailable" error then I just "up arrow" and execute the command again, it goes through
Its maddening I tells ya
And its only been occurring since I lost power.  Well, I didnt exactly lose power, I accidentally unplugged the box (grabbed wrong cord..whoops :rolleyes: )

So I thought doing the ol windows trick of reinstalling the drivers would help, me coming from the M$ world and beeing quite the n00b to this Linux thing

---

### Post by az on 2006-11-27
Where do you live?  PCI ethernet cards are usually dirt cheap.

---

### Post by luken8r on 2006-11-27
Youre suggesting my card is toast?

---

### Post by az on 2006-11-27
> **luken8r said:**
> Youre suggesting my card is toast?

Based on your description of the problem, I would say that's likely.  

Maybe it would be worth looking into you bios setting to see if your CMOS (bios settings saved onto a small chip) is corrupt.  You may need to reset your BIOS settings to factory defaults.  Maybe that would help - but otherwise, I would say it is fried.

---

