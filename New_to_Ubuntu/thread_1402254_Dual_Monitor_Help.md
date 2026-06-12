---
title: "Dual Monitor Help"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by runvs00 on 2010-02-08
Hello all! I am a newbie to this but I knew well enough to search for resolved issues of this nature... Every time I come across one it does not help me.. So here is my dilemma...
 
I have an Acer 1200X with an Nvidia 8200 graphics GPU integrated on the motherboard. I have an HDMI and VGA output. I have downloaded the Nvidia graphics driver using envyNG and the old fashioned way. I have tried configuring the monitors 15 ways from Sunday in the configuration and I cannot for the life of me get dual monitors to work.
 
When I go into configuration with the Nvidia wizzard it blanks like its going to work then just stays black with the mouse cursor. Then reverts to the old setting most of the time. I also cannot save as I get a "parsing" error. I am using Ubuntu 9.10 and have even tried using envyNG to get the monitors to work on twinview... NOTHING :sad: Hope someone can help! I also have tried 9.04 AND 9.10...
 
My dad who is a Linux nut came over to help and he left 3 hours later because were tempted to chuck the computer out the window... :shock:
 
I need to figure this out as this is going to be my work computer and I need dual screens.
 
HELP!

---

### Post by switch10 on 2010-02-08
Do you have compiz installed?  My dual monitors will not work (side by side anyway) with compiz running.  

I always wondered if you would be able to run dual monitors with one VGA, and the other DVI (or HDMI).  I don't see why you wouldn't be able to.  

Keep us updated if you get this working...

Dave

---

### Post by chewearn on 2010-02-08
A while back, I did a detailed set-up of nvidia in Ubuntu 8.10.  I think the situation has not changed much in recent Ubuntu 9.04 and 9.10, so my how-to should still work (but I can't confirm, since I have not upgraded from 8.10).

The post is quite long, so read carefully.  Hope it is helpful.

This one first:
[http://blog.chewearn.com/2008/10/08/nvidia-twinview-in-intrepid-ibex-beta/](http://blog.chewearn.com/2008/10/08/nvidia-twinview-in-intrepid-ibex-beta/)

Followed by this one:
[http://blog.chewearn.com/2008/10/09/nvidia-separate-x-screen-in-intrepid-ibex-beta/](http://blog.chewearn.com/2008/10/09/nvidia-separate-x-screen-in-intrepid-ibex-beta/)

---

### Post by runvs00 on 2010-02-09
> **switch10 said:**
> Do you have compiz installed?  My dual monitors will not work (side by side anyway) with compiz running.  

I always wondered if you would be able to run dual monitors with one VGA, and the other DVI (or HDMI).  I don't see why you wouldn't be able to.  

Keep us updated if you get this working...

Dave

I can turn off compiz how?? hahaha... Noooob here..

Does anyone know whether the problem could be that it is integrated graphics GPU motherboard or should that not matter?

---

### Post by runvs00 on 2010-02-09
> **chewearn said:**
> A while back, I did a detailed set-up of nvidia in Ubuntu 8.10.  I think the situation has not changed much in recent Ubuntu 9.04 and 9.10, so my how-to should still work (but I can't confirm, since I have not upgraded from 8.10).

The post is quite long, so read carefully.  Hope it is helpful.

This one first:
[http://blog.chewearn.com/2008/10/08/nvidia-twinview-in-intrepid-ibex-beta/](http://blog.chewearn.com/2008/10/08/nvidia-twinview-in-intrepid-ibex-beta/)

Followed by this one:
[http://blog.chewearn.com/2008/10/09/nvidia-separate-x-screen-in-intrepid-ibex-beta/](http://blog.chewearn.com/2008/10/09/nvidia-separate-x-screen-in-intrepid-ibex-beta/)


I will check on this as soon as I get home.. Thanks!

---

### Post by chewearn on 2010-02-09
> **runvs00 said:**
> Does anyone know whether the problem could be that it is integrated graphics GPU motherboard or should that not matter?

I have integrated graphics (nvidia GeForce 6150).  Have been running dual screens [noparse](1680x1050 + 1280x768)[/noparse] for a long time without problem.

---

### Post by runvs00 on 2010-02-09
Okay the error I get when going through the blog entry is "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.


Help..... :)

---

### Post by chewearn on 2010-02-09
> **runvs00 said:**
> Okay the error I get when going through the blog entry is "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.


Help..... :)

Please be more specific, which step resulted in this error.

---

### Post by runvs00 on 2010-02-09
Okay so I have HDMI and VGA will this code need to be any different??

Option "TwinViewXineramaInfoOrder" "DFP-0, CRT-0"
Option "UseDisplayDevice" "DFP-0, CRT-0"
Option "TwinViewOrientation" "DFP-0 LeftOf CRT-0"

---

### Post by chewearn on 2010-02-09
> **runvs00 said:**
> Okay so I have HDMI and VGA will this code need to be any different??

Option "TwinViewXineramaInfoOrder" "DFP-0, CRT-0"
Option "UseDisplayDevice" "DFP-0, CRT-0"
Option "TwinViewOrientation" "DFP-0 LeftOf CRT-0"

No, it doesn't need to be different.  What is important is consistency.

"DFP-0" is used to represent digital channel (basically, DVI or HDMI), and "CRT-0" represent analog channel (VGA).  Then, you should consistently use the same for the entire "xorg.conf".

---

### Post by runvs00 on 2010-02-09
Okay so try and FAIL.. My xorg.conf looks diff than yours in your blog AND I even tried just adding the sections you had and completely copy pasting your conf file. To no avail.. My next step is downloading 8.10 and trying it with that..

Any other options would be greatly appreciated as I need this working by Tuesday.. :o

---

### Post by runvs00 on 2010-02-12
Okay so updates....

I have installed 8.10 and update, setup the graphics card then the computer jams on a regular basis when I open new windows such as firefox etc.. All the steps I have done 3 times before with all the newer Ubuntu versions with NO success in getting dual monitors to work on this computer... I am at my whits end with it and need dual monitors BY Tuesday..

I even tried to go to the dark side and install Windows XP onto the computer but it gives me a hard drive error on a blue screen when the setup begins and wont let me continue..

So I tried to do a fresh install of Ubuntu and partitions sector 1 of the hard drive as FAT32 with a windows root and the 2nd half as EXT4 for linux... No go on that either the partitioner does not like the setup and I am back to square #1..

I now know after reading this forum that I should have installed windows first and then linux but crap happens and I did not so now I am stuck trying to figure out what the heck to do!

?? #1  Is there anything I can try that I have not tried on Linux to get dual monitors to work.

?? #2 How the heck do I wipe the hard drive COMPLETELY clean so I can install XP first then Linux?

Linux truly is a abor of love which pay big dividends once everything is set up properly, but man getting there is a CHORE!! :o

---

### Post by chewearn on 2010-02-12
> **runvs00 said:**
> ?? #1  Is there anything I can try that I have not tried on Linux to get dual monitors to work.

I am sorry the instructions did not work for you.  However, I am unsure how to help you further, as you did not elaborate on what (specifically) didn't work.

> ?? #2 How the heck do I wipe the hard drive COMPLETELY clean so I can install XP first then Linux?

On GParted > Menu > Device > Create Partition Table.

---

