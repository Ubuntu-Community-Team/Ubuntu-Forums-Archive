---
title: "Karmic Koala Live CD works fine but installed version does not boot."
date: 2009-12-02
forum: New to Ubuntu
---

### Post by marvin_littlewood on 2009-12-02
Hi!
 
Apologies in advance if the solution here is really simple but...
 
Started the Ubuntu 9.10 (Karmic Koala) live CD (Gnome version) with nolapic and it worked like a charm! All my Sony VAIO Laptop PCG-GRT896SP hardware was correctly recognised and handled.:D
 
Therefore installed Ubuntu with the default options and on restarting, the system drops out into a command line window asking me for my user name and password.:(
 
FWIW: I typed my username and password and then: startx. The bars and menus at the top and bottom of the screen appear, as does the cursor but then X stops with the message: open /dev/fb0: no such file or directory. Dunno if this is relevant because I am not sure of the best way to start the graphical system.
 
Can anyone help me to understand what is going on here? Should I try a re-install? Or is this correct behaviour and I need to type something else to get Gnome started?
 
Many thanks
 
Marv

---

### Post by jbrown96 on 2009-12-02
That's not proper behavior. Do you know your graphics card? You can check after you login with ```
lspci | grep VGA
``` It's probably some sort of graphics problem. 

Generally, with something like this, there may be an easy solution, but if we can't solve it very quickly, it makes more sense to reinstall. Reinstallation takes about 20 minutes. Waiting for an answer on the forums can sometimes take hours, so I'd just reinstall.


Do you have a reason for using the noapic option? You may want to try leaving that out; it may cause some hardware detection to fail. 

I have never seen a device called fb0; that's really strange. Searching around it seems to be a frame-buffer, which is a type of video mode. There was probably an issue with the hardware detection of your graphics card. It may or may not have been caused by noapic.

---

### Post by marvin_littlewood on 2009-12-02
Hi jbrown96
 
Thanks for your help.
 
Without the "nolapic" command, the Ubuntu LiveCD hangs on booting up (as does Fedora). I'll reboot the system with the liveCD tomorrow (in about 6h) and tell you where. I'll also try re-installing and see where that gets me.
 
The graphics card is a Nvidia GeForce FX Go5600 and is correctly detected both during the liveCD session and during the installed system session, according to Xorg.0.log. Looking at the /var/Xorg.0.log of the installed system, the problem seems to be during or after loading the GLX module. In the LiveCD session, the log continues but not in the installed session.
 
It would be a great help to know what settings were used for the LiveCD video configuration. If I could emulate them for booting the installed image, the recommendation from the LiveCD is to install the NVidia supplied driver 173.14.22.
 
I'll attach the log of both installed and liveCD Xorg sessions tomorrow, if that would help. Apart from the results of "lspci" is there anything else that might be of value?
 
Thanks
 
marv

---

### Post by marvin_littlewood on 2009-12-03
Hi!
 
Back up again!
 
Using the LiveCD, without "nolapic" Ubuntu stops at: 
 
"USB Mass Storage support registered"
 
Using LiveCD, out of curiosity, I tried safe graphics mode, just to see what would happen: stopped even more quickly (3.0 instead of 7.4) at another USB device:
 
"ata2.00: ATAPI: Pioneer DVD-RW DVR-K12D, 1.00, max UDMA/33"
 
I'd say that "nolapic" actually facilitates USB device recognition rather than hinders it. 
Using LiveCD Booted with "nolapic" in safe graphics mode, and boot stopped at the same place as with the installed version but this time with a flashing screen and patchy keyboard suppport.
 
I'd say that "nolapic" is fairly essential. Wont have time to do more for a while, but I hope the update is useful.
 
Mark

---

### Post by marvin_littlewood on 2009-12-04
Hi
 
A re-install solved the problem! Everything now works! 
Fantastic and many thanks to Ubuntu and the forum.
 
Marv

---

