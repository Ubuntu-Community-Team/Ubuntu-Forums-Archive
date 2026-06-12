---
title: "ATI Radeon 1200"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by loyaleagle on 2009-04-23
Everything works great in 9.04 (64) except for the screen flickers and seems to lag when moving windows or refreshing / drawing new page in the browser. Looks like it is using a generic driver and not the one ffrom ATI

HELP...

---

### Post by loyaleagle on 2009-04-24
tried to install fglrx from ATI and got a total crash. Black screen with green lines. Short of a re-install,  anybody have any ideas?

---

### Post by TransitMan on 2009-04-24
ATI Radeon 1200 is not officially supported by ATI in Jaunty. 
Remove/uninstall fglrx and install the open source radeon drivers from the repos. This should take care of your problem.

---

### Post by JoshuaRL on 2009-04-24
... partially.  You won't have 3D from the open source ones.

---

### Post by SerafeimG on 2009-04-29
EXACTLY the SAME problem here!!!
I have ubuntu 9.04 on my laptop fujitsu-siemens apilo pa2510 with amb64 processor.

I was also forced to reinstall ubuntu after installing the drivers from ati.
If you want to use the 3d effects, the open drivers have problems with ati radeon xpress X1200.

Any secure ideas?? (by telling secure I mean to not force me in a new reinstallation of ubuntu)

Thanks a lot!! (and sorry for my English level :P)

---

### Post by loyaleagle on 2009-04-29
So let me see if I understand.

ATI drivers are no longer supported for my card and are now legacy.

My options are:

1: run 9.04 with a flickering screen and white lines.
2: Install non ATI drivers that do not run 3D.
3: Go back to Ubuntu 8.10 where all was fine to start with.

This seems unacceptable to me. My first major problem with an Ubuntu upgrade. My laptop is only 1 1/2 old.

What should I do. I am out of ideas.

Thanks....

---

### Post by Mortus Pryde on 2009-04-29
I had the same problem with my laptop though somewhat older. The graphics system is too new to be fully supported by open source, too old to be supported by ATI and thus left in the dead zone by Jaunty. I went back to 8.10 to wait for support to catch up. I think the decision to update xorg to 1.6 was rather untimely. Though I think we can fairly blame ATI for the support gap as I understand they did not release the specs for the cards they were dropping till shortly before dropping them and leaving not enough time for os developers to fill the gap.

---

### Post by garythegoth on 2009-04-29
Same with my laptop. I shall certainly never buy an ATi based product again.

---

### Post by alphacrucis2 on 2009-04-29
> **loyaleagle said:**
> So let me see if I understand.

ATI drivers are no longer supported for my card and are now legacy.

My options are:

1: run 9.04 with a flickering screen and white lines.
2: Install non ATI drivers that do not run 3D.
3: Go back to Ubuntu 8.10 where all was fine to start with.

This seems unacceptable to me. My first major problem with an Ubuntu upgrade. My laptop is only 1 1/2 old.

What should I do. I am out of ideas.

Thanks....

Not much you can do. At least ATI have released the full documentation of the legacy cards and the OSS devs intend to implement the 3D support but it will take a few months I suspect.

---

### Post by kansasnoob on 2009-04-29
You can't blame Ubuntu or Linux in general.

AMD/ATI really dropped the ball!

They've become the Lexmark of graphics cards!

---

### Post by Duskao on 2009-04-29
Actually, you can't really blame either. the exact same thing could have happened with Nvidia. It just happened all at the same time. Give it a bit of time and I'm sure that there can be some sort of patch put out by ubuntu so that you will be able to use 9.3 drivers with the legacy cards. 
Just to sum up, this is a very normal occurance, and not just with video cards or just by Ati. Every company has to drop support for older hardware/software or whatever it may be, due to the fact that it takes too many resources to keep the old stuff going. Its the same with the old versions of Ubuntu. That is why old versions like 4.4 are no longer supported, or with windows where 95/98/2000/ME and eventually even XP will be dropped, in fact MS keeps saying they will drop XP by next year, but it keeps being postponed because there are so many XP users and Vista and Win 7 suck. (reason I am now a VERY HAPPY linux user :D). Also keep in mind that the X1000 series is 4 years old now (and for computer age, thats a lifetime)

Options...
Jaunty 9.04 with very little 3d 
or
Intrepid or older with 3d 
or 
get new video card

---

### Post by JoshuaRL on 2009-04-29
From someone I talked to, it seems like the newest OS drivers are accelerated to some degree.  Stellarium apparently works just fine, and with FPS close to what they used to be.

Here's to hoping that all proprietary driver writers realize that its easier and a whole lot cheaper to release the specs and let the community write your driver for you.

---

### Post by mal1958 on 2009-04-30
I am a noob at Linux, and at Ubuntu, though I have worked with computers since 1979.  I have always steered clear of ATI cards since I have never had much luck with them in the past.  Slow response from their support staff, and information that never seemed to get any good results.  Others have had better luck with them.  If it is an option, I would reccomend that you look into the possibility of a new and different card for your system.

Mal

---

### Post by lucacimarius on 2009-05-08
Same problem dudes... on acer travelmate 5520, everything goes right until i install the new verios of ubuntu last week, after that the hell started. I have instaled for a few times until i understand was the graphic card...now I have again 8.10 verios and I tried to update to 9.04 again and the system announce me that the driver from ATI is not supported for my sistem. :( Hope to manage this if not...I have to change the laptop...

---

### Post by malleus74 on 2009-08-31
I want to preface this post by saying I'm a huge fan of Ubuntu. I like it better than any distro I've ever used. I'm currently running a modified version of UbuntuStudio "Jaunty".

I have a year-old Toshiba laptop, so updating the hardware is not a possibility. Thankfully I'm able to do most of what I want with the opensource driver. However, I would like to run WoW, and in the future, Entropia Universe on this laptop. I would also like to run Mame, LXDREAM, etc., so in the long-run I'm crippled on Jaunty.

Am I really going to have to reinstall 8.04/8.10 to use my laptop?

---

### Post by malleus74 on 2009-08-31
Has anyone attempted this:

[http://www.kdedevelopers.org/node/3942?destination=node%2F3942](http://www.kdedevelopers.org/node/3942?destination=node%2F3942)

I'm going to try this tonight. If this works without breaking my system, and it allows me to use the proprietary drivers, then I'll post about it.

---

### Post by Mark Phelps on 2009-09-01
> **malleus74 said:**
>  However, I would like to run WoW, and in the future, Entropia Universe on this laptop. 

If you're running MS Windows on the laptop, my suggestion then is to stay with that.  Unless there is a linux port of Entropia Universe, you won't be able to run it at all because the Wine rating for it is "garbage".

You're not going to have to reinstall anything to "use your laptop"; you'll have to go back to a prior release to get restricted drivers to play some games.

---

### Post by malleus74 on 2009-09-01
> **Mark Phelps said:**
> If you're running MS Windows on the laptop, my suggestion then is to stay with that.  Unless there is a linux port of Entropia Universe, you won't be able to run it at all because the Wine rating for it is "garbage".

You're not going to have to reinstall anything to "use your laptop"; you'll have to go back to a prior release to get restricted drivers to play some games.

I'm running UbuntuStudio Jaunty, modified to fit my needs. 

Wine worked well enough with Entropia to sign in so my account isn't terminated. I didn't have any problem with WoW or any of the other programs I ran with it, once the dll's were installed.

**Why does it matter what I want to do?** I want fully functioning video.

To go back to Intrepid, I'll have to repartition, set up LUKS, install the os, and then add back all the modifications that makes this distro useful to me. 

This is going to take quite a bit of time. I don't think this is reasonable, so I added my .2 cents to the thread for **helpful** responses. I intentionally made positive comments about Ubuntu, and I'll stand by them. I even posted a possible fix that I found on net. Can you please explain to me why exactly wanting to use an earlier version of xorg so I can use hardware drivers is so wrong?

---

### Post by Ric_NYC on 2009-09-01
I have the same video card.
Same situation here.

---

