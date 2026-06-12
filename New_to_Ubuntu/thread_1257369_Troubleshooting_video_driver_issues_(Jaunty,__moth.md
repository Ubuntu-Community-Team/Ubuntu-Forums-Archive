---
title: "Troubleshooting video driver issues (Jaunty,  motherboard ATI HD4200)"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by remymarathe on 2009-09-03
**In short:**
1)  How can I see which video driver is *currently loaded* and *being used by* gnome?  Near as I can tell, settings in xorg.conf no longer seem to matter.

2)  Which video driver is the default used by Jaunty?  Or, if upon basic install it chooses one based on your hardware, what would it have used for an onboard 785g/Radeon HD 4200?

3)  How can I revert the video drivers back to their basic installation state?

**At length:**

I've got the m4a785TD-V EVO motherboard, which has 785g northbridge= Radeon HD 4200.  Fresh install of stable Jaunty 64-bit, no hardware changes, just not so fresh that I'm willing to do a complete reinstall. 

In the process of trying to get 3D accelerated gfx drivers kicking, I made the mistake of trying too many different methods without being sure what I was doing.  I ran the binary installer from AMD/ATI's website.  I used the Ubuntu restricted-driver management applet.  I may or may not have used the sofware add/remove system.  I disabled the driver listed in the restricted-driver management box, and later tried to reenable it.  All without understanding the differences between what exactly they would install.

This  culminated in me getting a frozen black screen with some ugly artifacts on reboot the other night, and unfortunately because I tried so many different methods I can't be sure which one caused the trouble.  A slash-and-burn command line removal of fglrx was required for me to return to a normal-looking state I can work with.

Now I want to do one thing at a time, hoping that if it doesn't work I can at least identify exactly which video driver using which method causes the freeze-up.  I've got plenty of links available for the various methods but I'd like to better understand what I'm doing.

First I need to verify that I'm at square one.  The other night I noticed that fglrx was getting loaded regardless of whether xorg.conf called for it, which leads me to believe that video driver settings are taken from somewhere else now.  Where can I find out what video driver I'm *currently* using?

Terminology is also confusing me; there's Catalyst, fglrx, "Proprietary ATI driver binaries" from their website, "Open source drivers".  Is catalyst just ATI's video control software?  Is it able to affect graphics settings using either the proprietary or the open source drivers?  Is fglrx the proprietary driver from ATI?  What are the open source drivers for ATI called?

---

### Post by xir_ on 2009-09-04
Catalyst, fglrx, "Proprietary ATI driver binaries", pain in the **** = the same thing

The default driver that comes with ubuntu is the open source readon drivers, these are ok, (and are getting better).

But those who want 'better' performance have the option of the ati binaries, these generally are faster but less stable (ie more breakage) and to be honest are not well looked after by ati (nvidia seems far more on the ball).

Could you please post your xorg.conf, you should be able to do what you want from there.


The safest way i have found to get binary drivers working is to use envyng, these are slightly below bleeding edge, but you are not as likely to get breakage.

```
sudo apt-get install envyng*
```

This program lets you install and remove both ati and nvidia binaries.

---

### Post by remymarathe on 2009-09-04
Thanks for the response, and I may yet check out the open source drivers.  Hopefully that's not what was automatically installed at first, or yeah I require better performance :).  

I eventually gave up on finding out exactly which driver was in use (xorg.conf was *empty* of entries, just the basic template), so given that my window movements were choppy like after the default install I went ahead and assumed I was at square one.

I then tried using the "restricted drivers" menu under gnome.  It supposedly downloaded, installed, and exited.  There was a notification under the ATI device listed that said it required a reboot.

I reboot, it freezes on a black screen w/ ugly artifacts during the initialization of X, same as the original problem.

From the console I reset the driver again by copying a backup of the empty xorg.conf into place and removing xorg-drivers-fglrx.   Reboot; I'm back to a working desktop sans fglrx.

Next I tried, step by step, the method described under "Installing the Drivers Manually" (maybe this is the procedure that EnvyNG automates?) :
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Alternatives](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Alternatives) 

Don't anyone follow my code below verbatim, there are steps I didn't need to do and caveats that didn't apply to me described in the howto above.  

 Essentially took the .run file downloaded from ATI's website, turned it into a deb package and installed:
```

sudo bash
sh ati-driver-installer-9-7-x86.x86_64.run --buildpkg Ubuntu/jaunty 
dpkg -i xorg-driver-fglrx_*.deb fglrx-kernel-source_*.deb fglrx-amdcccle_*.deb 

```added to xorg.conf```
Driver        "fglrx"
``````
aticonfig --initial -f 
aticonfig --input=/etc/X11/xorg.conf --tls=1 
```I reboot, X loads with no problems.  

I still don't know the difference between fglrx as installed via the restricted drivers menu and fglrx as I installed manually.  This line from the installation guide linked above sticks out suspiciously though:[I]
"Some people find that changes to xorg.conf don't get used by the driver. To force the ati driver to adopt changes made to xorg.conf, type the following command: [/I]aticonfig --input=/etc/X11/xorg.conf --tls=1*"*

See when my machine was hanging after the restricted hw driver installation, changing xorg.conf back to the default/empty state had absolutely no effect.  Still hung.  Not until I actually removed the fglrx driver altogether could I get X to load.  Maybe after using the restricted driver installer, there are configuration actions you need to take before rebooting to prevent the system freeze.

I'm going to go ahead and mark this thread as "solved" since I've got SOME kind of 3d acceleration working.  Not seamlessly but wine and World of Warcraft are a whole separate can of worms.

---

