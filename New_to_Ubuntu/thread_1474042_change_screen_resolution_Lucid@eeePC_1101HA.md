---
title: "change screen resolution Lucid@eeePC 1101HA"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by belochkka on 2010-05-05
I installed Ubuntu Desktop Lucid Lynx on my eeePC 1101 HA. Aside from issues I'm not ready to tackle yet (power management, since the battery seems to work somewhat less; camera configuration; brightness keyboard controls not working), I'm most perplexed by the fact that 
[LIST]
[*]the "monitor type" is not detected automatically
[*]I'm only offered two options for screen resolution (800*600 and 1024*768, the latter is enabled by default, and both look absolutely hideous)
[/LIST]
I've scoured the www in hopes of finding a solution, but most appear to suggest modifying the xorg.conf file in the /etc/X11 folder. I have little idea of what I'm doing here (heck, I "discovered" Ubuntu a week ago!), but it appears that I do not have such a file on my PC.

How do I change the screen resolution to something acceptable???
Thanks in advance!

---

### Post by tonsil on 2010-05-05
you probably do. open a terminal (CTRL+ALT+T) and type:
sudo gedit /etc/X11/xorg.conf
it will ask for your password, type it, and you'll see your xorg.conf file.
Check it out and perhaps paste the xorg file here, so we have an idea what may be wrong?
remember, the terminal is case sensitive.

---

### Post by belochkka on 2010-05-05
It does indeed ask me for my password, BUT the gedit plain text file is blank!
And there is no /etc folder in my home folder, even when I check the "View hidden files and folders tab"

---

### Post by belochkka on 2010-05-06
> you probably do. open a terminal (CTRL+ALT+T) and type:
sudo gedit /etc/X11/xorg.conf
it will ask for your password, type it, and you'll see your xorg.conf file.
Check it out and perhaps paste the xorg file here, so we have an idea what may be wrong?
remember, the terminal is case sensitive.
Okay, so from reading a bunch of stuff on the web, I'm assuming that my problem lies in the fact that I do not have a graphics controller :confused::confused:(i.e. a driver for my graphics card) installed (the eeePC 1101 HA sports an Intel 950 GMA, and for the life of me I can't seem to find a driver for it on their site or elsewhere)
Poulsbo is, unfortunately, listed as not working on Lucid Lynx, which is what I'm trying to install. ](*,)](*,)](*,)

Any remote ideas on how to configure the bloody thing? I really don't want to revert back to XP, but the distorted screen is a major pain!
Including the fact that I use my netbook for school, I spend around 6+ hours looking at it, and OOwriter looks atrocious!:cry::cry::cry:

Please HELP!!!

---

### Post by bredman on 2010-05-06
There is a special version of Ubuntu available for the eeePC and similar, it is known as Ubuntu Netbook Remix. It would probably have been a better choice than the Ubuntu Desktop Edition.

If all is lost, I would recommend trying out the Netbook Remix before moving back to XP.

But, it is still worth trying to get the Desktop Edition to work. I suggest you search for forums supporting the Netbook Remix or the eeePC. Explain that you have used the Desktop Edition and you have graphics problems, and somebody may be able to help. The Netbook Remix is just a reconfig of the standard Desktop Edition, so maybe somebody with experience on the Netbook Remix can still help you with the Desktop Edition.

Best of luck, sorry I can't help any better.

---

### Post by Splarz on 2010-05-06
unfortunately the problem is due to a lack of support of the graphic card, the Intel GMA500. lucazade, jbernardo and others are trying to get the driver working on lucid lynx; you can follow [this discussion](http://ubuntuforums.org/showthread.php?t=1229345&page=9&highlight=1101ha) and... keep your fingers cross :)

---

### Post by belochkka on 2010-05-06
> unfortunately the problem is due to a lack of support of the graphic card, the Intel GMA500. lucazade, jbernardo and others are trying to get the driver working on lucid lynx; you can follow this discussion and... keep your fingers cross 
Thank you! Yes, I realized this was going on, and was hoping that someone could direct me to such a thread!!!:KS:KS:KS

---

### Post by scicode on 2010-05-15
[http://code.google.com/p/gma500/wiki/InstallScript](http://code.google.com/p/gma500/wiki/InstallScript)

works like a charm (if you have all the latest updates)

what about multi touch?

---

