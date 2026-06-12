---
title: "Splash Screen Screwed - HELP"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by TheHitman2010 on 2010-05-02
It's a small thing - but important.

I'm not sure what caused this - installed application or something I'm sure - but my splash screen is now in "DOS" format after I installed all of my apps.  It says Ubuntu in the old fashioned lettering, not the nice display the version came with - and then gives a description underneath of what is loading.  Once at the desktop everything is fine - but why has the splash changed??  This never happened in 9.10 - any suggestions?  Furthermore, when the login screen appears, some silly background with a tree opens up.  Everything goes to normal once logged in, but this screen reappears every bootup even if I delete the background.  It has to be caused by an install of some kind - I'm thinking the educational suite I put on for my kids.  This is completely weird. Can someone please help??

---

### Post by madjr on 2010-05-02
video card?

plymouth doesnt work too well with some drivers

[http://www.phoronix.com/scan.php?page=news_item&px=NzgwMA](http://www.phoronix.com/scan.php?page=news_item&px=NzgwMA)

i know they're working on it but still has issues

[http://ubuntuforums.org/showthread.php?t=1343120](http://ubuntuforums.org/showthread.php?t=1343120)

[https://wiki.ubuntu.com/FoundationsTeam/LucidBootExperience](https://wiki.ubuntu.com/FoundationsTeam/LucidBootExperience)

---

### Post by TheHitman2010 on 2010-05-02
NVIDIA GeForce 9500GT - didn't have a problem on 9.10 at all.  Is Plymouth a new thing?  I updated my drivers via Hardware Drivers to the [recommended] setting but it didn't fix anything.  This is driving me nuts. I know it's a small thing - but it's important to me. :P

---

### Post by sunk8 on 2010-05-02
The easiest solution...
Install startup-manager.
Uncheck the 'show text during boot'...

---

### Post by Claus7 on 2010-05-02
Hello,

yes it is new (plymouth). The easiest thing I would recommend is reinstalling from synaptic plymouth and plymouth theme, restart and see what is going on. With updates plymouth might messed up.

Regards!

---

### Post by TheHitman2010 on 2010-05-02
Thanks. I'll try it.  Do you know how to install the latest NVIDIA drivers? I have it downloaded, I just can't figure it out. I'll let you guys know if it's fixed.

---

### Post by TheHitman2010 on 2010-05-02
Neither of that worked...and I still had that stupid tree background. I'm going to try and reinstall everything.

---

### Post by TheHitman2010 on 2010-05-02
This is definitely a video driver issue.  I just did a complete reinstall of Ubuntu, and it did the usual error on bootup, then I booted in safe mode with graphics scaled back, installed the updated NVIDIA driver from the Hardware screen, and the resolution on the splash spreen got big again.  It's this Plymouth application that doesn't like the NVIDIA drivers, and judging by the forums today, any video card.

---

### Post by Claus7 on 2010-05-04
Hello,

I was tampering with xsplash screen resolution and I messed ubuntu logo, right now having a blurred two sided logo instead of a solid one.

Yet, there are many solutions in the net, which describe how one can change xsplash. Since everything else is working ok, then I think that you should try this.

Regards!

---

### Post by ankspo71 on 2010-05-04
This is a sticky post in the General Help section of this forum.
"Known Lucid Lynx issues/bugs with workarounds"
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)
In the middle of the post it says there is a fix for Plymouth.
I haven't tried it yet though. I might try it today.
Good luck.

---

### Post by xumuk37 on 2010-05-04
after all night trying to make it "nice", finaly I've got it...

[[COLOR="Red"][CENTER][IMG]http://www.freewebs.com/perpendicularproductions/images/youtube%20banner.jpg[/IMG][/CENTER][/COLOR]]("http://www.youtube.com/watch?v=F48GXVvTL6I")

If I can help something, ask xD

---

### Post by TheHitman2010 on 2010-05-05
Thank you for the link, awesome!

---

