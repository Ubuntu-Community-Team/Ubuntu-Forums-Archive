---
title: "Grub back to default"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by nml on 2009-04-12
Please forgive my ignorance, but I better ask **before** I mess up the system again....

Current setup is on 80gig hd:

dev/sda1  =  Ubuntu
dev/sda2  =  XPpro
dev/sda3  =  did have OpenSuse, had to dump it, but would like to have it back
dev/sda4  =  extended format for swap

When I went through the OpenSuse 11.1 install, I got it to install on sda3....unfortunately, I couldn't get it configured to let me use my original Grub bootloader......matter of fact, I couldn't get back to Ubuntu I even had a hard time booting back to OpenSuse, so I reformatted the sda3 partition with Gparted, then used Ubuntu live cd to setup my original grub again as described:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

anyway, everything is back like I had it, but I want to try to put OpenSuse back on my dev/sda3.....**IF and ONLY IF** I can use my original Grub to decide what OS to use.......

This time, I want to figure out how to make my initial choice the Ubuntu Grub and then Chainload the OpenSuse along with the XP install (if that's possible)...

If I've explained this poorly or you need more information, please let me know

Mick
(yeah and I do need most of the explanations to be in NOOB terms.....)

---

### Post by kk0sse54 on 2009-04-12
You can 1) either choose not to install grub during your OpenSUSE installation and directly boot it off your Ubuntu grub however this would require you to continually update your menu.lst for each kernel update in OpenSUSE.

Much easier would be to chainload, check out this tutorial [http://ubuntuforums.org/showthread.php?t=724817&highlight=chainload](http://ubuntuforums.org/showthread.php?t=724817&highlight=chainload).

---

### Post by nml on 2009-04-12
Hey C!oud...thanks for the link..

I've been through that link a couple of times before I messed up this last attempt...there are just many variables for us Noobs....

anyway, as I reread it, I certainly see some possibilties.....one of which may be summed up in the reply that bodhi.zazen gave to a response a couple of posts after his tutorial....

> LOL Multibooting is moderately complex. If you do not understand what you are doing that is an indication to stop and do some additional reading.

so, probably the best thing for me to do is read more, then give it another whirl.......it seems that the 2nd OS installed is the one that has the control......if that's really the case, then it will make my planning process different the next time I start with a total reformat....

anyway, maybe I can figure out how to leave sda1 as Ubuntu, sda2 as XP, put OpenSuse on sda3 and leave the swap as it is....

thanks again,

Mick

---

