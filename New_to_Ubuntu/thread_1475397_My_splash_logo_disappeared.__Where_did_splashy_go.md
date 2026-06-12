---
title: "My splash logo disappeared.  Where did splashy go?"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by outleradam on 2010-05-06
My splash screen disappeared a couple of weeks aog.  I cannot seem to get it back.  What do I have to do to get rid of the unsettling tty view and replace it with the stock Ubuntu 10.04 splash screen?

---

### Post by cap10Ibraim on 2010-05-06
I have the same issue the first boot it was there then it was gone

---

### Post by -humanaut- on 2010-05-06
Are you using A nvidia card with proprietary drivers? Because Plymouth seems to really hate it. I enabled the proposed-updates today an update there seems to sort of bring it back to life. atleast its not 16 colors or nothing with it.

---

### Post by flyfishingphil on 2010-05-06
I don't know much about all of this but I went into System > Preferences> Appearances and played with Themes, etc, inported a bunch of photos from my files and now have the initial Ubuntu screen when it's starting up and then goes to one of my photos for  the background.

Maybe go in there and select something different, come back out and see if it works, then go back in and grab the oen you had, if that's what you want.

---

### Post by -humanaut- on 2010-05-07
> **flyfishingphil said:**
> I don't know much about all of this but I went into System > Preferences> Appearances and played with Themes, etc, inported a bunch of photos from my files and now have the initial Ubuntu screen when it's starting up and then goes to one of my photos for  the background.

Maybe go in there and select something different, come back out and see if it works, then go back in and grab the oen you had, if that's what you want.

Hey man I love the sig!

---

### Post by WinterRain on 2010-05-07
Mine disappeared too, but I'm using the nvidia drivers. No biggie.

---

### Post by outleradam on 2010-05-07
^^ Dude, are you friggin' serious?   No biggie?  I've searched and this bug is 1 year old!  A WHOLE YEAR!  That's a long time to have any sort of bug.  

What would happen to Windows if their OS did this, or Mac?  People would say that it's unreliable.   I'm starting to think the same thing.   It is unsettling to see how many non-communicating SATA ports I have and it really is un-needed information when I'm starting my computer.  

When I shut down my computer it freezes and gives me a messed up video feed.  What would happen to Windows or Mac if that happened every time?

This is redonculous.  This OS is supposed to accelerate at speed and reliability.  Canonical is reducing the speed with every fluffy add-on and the reliability is going to hell as well.   GTK just crashed on me 10 minutes ago.

---

### Post by JerichoKru on 2010-05-08
Does this work for anyone?  


[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/17/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/17/)

---

### Post by -humanaut- on 2010-05-08
Turn on proposed updates. Theres a new Nvidia driver and a fix to this problem simple.

---

### Post by -humanaut- on 2010-05-09
Apparently the new updates worked for all of one day! I'm back to the TTY console this is getting pathetic. Maybe the developers shouldn't have relied so heavily on Nouveau I'm blacklisting it to see if that helps.

---

### Post by outleradam on 2010-05-11
It's working for me.  I downloaded the latest drivers from nVidia directly, killed my xorg and then installed as root.  It worked well.   Also, I found out that I was running 32bit ubuntu on a 64 bit machine.  It may be that I forced architecture on a 32 bit package though.   I thought for sure that I was running 64 bit, but a DIY somewhere told me to force archetecture.  Anyways, I was not able to install the 64 bit drivers.  So...
 
Backed up home drive
downloaded ubuntu 10.04 LTS
installed fresh
enabled proposed updates
updated through update manager
restored home drive (except for certain hidden folders)
installed newest nVidia Drivers
Rebooted
problem solved.
 
Everything works great.  No graphic artifacts on shutdown, no TTY on bootup, and everything seems faster.
 
The only thing that's missing is the option to switch kernels.  I have not figured out how to access grub options from 10.04.  I had a grub menu before on my 10.04 beta 1 upgraded to LTS, but now my grub menu is missing.   I'm trying to add the profile option to the end of linux line.

---

### Post by QIII on 2010-05-11
Outleradam -- 

Do a "find" for "delay" here.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

That'll help you get your grub delay back.

If you are quick on the draw, you can also hit the Shift key.  But you have to be quick.

I'm not sure a 0 delay is such a good default ...

---

