---
title: "Enable Intel Graphics Driver for Ubuntu 10.10:"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by Terry Maker on 2011-04-15
Hi All,

I've been trying to do the following upgrade to my Novatech laptop mod: 259ii1

************************************************************

Step-by-step to Enable Intel Graphics Driver for Ubuntu 10.10:
Install the updated Intel graphics driver by:

[B]sudo add-apt-repository ppa:glasen/intel-driver
sudo apt-get update && sudo apt-get upgrade[/B]

To enable the Intel driver you need to create a file called /var/log/xorg.conf containing the following:

Section "Device"
Identifier "Configured Video Device"
Driver "intel"
EndSection
Section "Monitor"
Identifier "Configured Monitor"
EndSection
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"

X freezes (GPU lockups) are still being experienced on i830, i845, and i855 chips. There is a kernel patch for the Intel 855 series chips that appears to fix the system freezes. After re-enabling the Intel driver as above, i855 users can set by this:

[B]sudo add-apt-repository ppa:glasen/855gm-fix
sudo apt-get update && sudo apt-get install dkms 855gm-fix-dkms[/B]

This will provide an updated version of xserver-xorg-video-intel that may provide better results than what you currently have. After you add the the repository run:

**sudo apt-get update and sudo apt-get upgrade**

If you don't receive updates to the xserver-xorg-video-intel then run:

**sudo apt-get install xserver-xorg-video-intel **

*****************************************************************

Now this is the bit where I get to look an absolute idiot! When I get to the part:

***To enable the Intel driver you need to create a file called /var/log/xorg.conf containing the following:***

Section "Device"
Identifier "Configured Video Device"
Driver "intel"
EndSection
Section "Monitor"
Identifier "Configured Monitor"
EndSection
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"

And try to save it, it comes back at me that I don't have root permissions and I'm not the owner, which I am!

Can anyone guide me as to what I'm doing wrong, I can create the file with text editor OK, but I can't save it to the required location! All of the other stages went fine, I just can't enable it!

Newbie with a big dent in his forehead from beating his head against a brick wall!

Any ideas anyone? I'm probably too close to the problem to see what I'm doing wrong!

Terry M

---

### Post by spiky001 on 2011-04-15
You need to be root when doing this. Just as a note where did you get link for the driver

---

### Post by Rubi1200 on 2011-04-15
Which specific series Intel card do you have?

I was able to use the Glasen PPA without creating a xorg.conf file.

@ spiky001:

here are the links for 10.04 and 10.10:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

---

### Post by spiky001 on 2011-04-15
lspci shows ```
VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)         Subsystem: Toshiba America Info Systems Device 0002
```  But it is more involved than that

---

### Post by Terry Maker on 2011-04-16
OK, thanks for the replies, the "Card" isn't as separate, it's integral to the laptop. 

the link was via this forum, to several other sites and finally here:

[http://www.neowin.net/forum/topic/980676-ubuntu-1010-screen-resolution/](http://www.neowin.net/forum/topic/980676-ubuntu-1010-screen-resolution/)

I'm not so bothered about the resolution, I wanted to try this aspect of the drivers:

*"X freezes (GPU lockups) are still being experienced on i830, i845, and i855 chips. There is a kernel patch for the Intel 855 series chips that appears to fix the system freezes. After re-enabling the Intel driver as above, i855 users can set by this:"*

So should I be doing this via terminal- sudo - and Touch?

TM

PS (on Edit)the system is currently using the VESA driver so Compiz tells me.

---

### Post by Terry Maker on 2011-04-18
After much testing sadly these drivers do NOT work on the Novatech 259iil laptop, causing a complete graphics lock up

---

### Post by GNU-Cody on 2013-04-01
At the time of this post, the last comment on this thread was two years ago. So, I'm just bumping this thread to let everyone know that the procedure in comment #1 worked perfectly today for my Ubuntu 10.04 LTS installation on my old Toshiba Satellite A15-S157. 

My prior workaround was just using the "vesa" driver setting in xorg.conf, which resulted in being able to view the desktop just fine, but anything more than basic windowing and it got choppy quick, and you could forget about playing a DVD. However since following the procedure in comment #1 it runs great! ...or at least as great as you can expect the Intel 855GM chip-set to run. Thanks again for posting, albeit very late!

---

### Post by wildmanne39 on 2013-04-01
Thread closed. Please do not post in old threads.

---

