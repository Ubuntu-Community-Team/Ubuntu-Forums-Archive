---
title: "Laptop loses power when trying Ubuntu trial"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by DizzyDaze on 2011-02-05
Hi, Ubuntu newbie here, never installed it or Linux before but interested in getting into Ubuntu.

I made a Live USB for Ubuntu Desktop 10.10 and changed the boot order on my laptop to USB hard drive, and Ubuntu loaded up. I chose 'Try Ubuntu' and everything seemed to be fine - desktop loaded, sound played, could connect to wifi, Firefox worked. 

 However, about 5-10 mins into clicking on menus and enjoying the trial, the laptop lost power completely, as if it'd been working off the mains with no battery and the electricity had gone (this wasn't the actual situation but the end result was the same).

I actually tried the Ubuntu Netbook Remix first and didn't even manage to get to the desktop, clicking on Try Ubuntu made it try and load but the blackout happened again. The desktop version gave me a bit more time but the same happened...

I've no idea what could be causing this - I'm not entirely computer illiterate but I'm not a boffin either so help would be muchly appreciated. The computer is running Vista fine, however, and I'm worried the same loss of power problem could happen if I chose to install Ubuntu.

_System specs:_

[I]HP Pavilion DV2500 laptop
Microsoft Windows Vista Home Premium 32bit SP2
nVidia GeForce 8400M GS
Intel Core2 Duo CPU T5250 1.5 GHz
2GB RAM

EDIT: Had the laptop since 2007, use it pretty much daily. Sometimes video heavy stuff (iPlayer, Skype, 4oD etc, some gaming (but we're talking games from 1998-2004 at lowest reqs). The video card's blown a couple of times from the video heavy usage - completely failed first time round, and second time round on the replacement motherboard, started giving me BSODs after playing two 30 min episodes of a show.[/I] [I]

A new motherboard to replace that was put in literally days before I started trialling Ubuntu. Had no trouble so far on Vista.[/I] 

Thanks!

---

### Post by Hedgehog1 on 2011-02-05
> **DizzyDaze said:**
> 
...
 However, about 5-10 mins into clicking on menus and enjoying the trial, the laptop lost power completely, as if it'd been working off the mains with no battery and the electricity had gone (this wasn't the actual situation but the end result was the same).
...


When you were running off the USB stick doing your 'Test Drive' of Ubuntu, you were running off just the laptop's battery, correct?

**If you were running on battery** what you have described is what happens when the battery runs out and the OS you are using does not have the battery level monitoring software installed for that particular laptop.

If you removed the battery level monitoring software from your vista install, it would do the same thing.

If you do a true install of Ubuntu on your laptop, the battery level monitoring software will also be installed and this shuold not happen again.

:KS

---

### Post by NightwishFan on 2011-02-05
It might be overheating. Was it hot? Also the battery monitor should work from the live cd trial.

---

### Post by Hedgehog1 on 2011-02-05
The laptop overheating would also induce this behavior.

If DizzyDaze was plugged when this happened, then an overheating event seems like a very possible cause.

DizzyDaze: If you were running from your AC adapter, then this is more likely what happened.

If you were running from battery, would you reboot from the Live USB, and look for the battery monitor in the notification area?  If it appears, does it seem to be telling you correct info about your battery?

:p

---

### Post by sammiev on 2011-02-05
Laptop overheating maybe the cause. Get a few of the sensors going to check and is your fan running at all?

---

### Post by Lt. Surge on 2011-02-06
The real problem is Vista. jk

No, I believe either your battery is having issues or your laptop internal cooling ventilation isn't working properly. When did you get it and how often was it used? Did you ever dust it? Please include the answers in your OP along with your specifications.

If you have the tools and/or you haven't done it lately, you should open up your laptop and check for dust. Get a compressed air can and blow into the vents, see if any dust comes out. Then do a complete dusting of the rest of the laptop.

EDIT: If you've not done this before also consider removing the battery before going into your laptop. This is standard procedure whenever doing so.

---

### Post by DizzyDaze on 2011-02-06
Thanks for your prompt replies! 

> **Hedgehog1 said:**
> When you were running off the USB stick doing your 'Test Drive' of Ubuntu, you were running off just the laptop's battery, correct?


Nope, was running off AC mains, battery was in as well.

> **sammiev said:**
> Laptop overheating maybe the cause. Get a few of the sensors going to check and is your fan running at all?

I did notice the fan start to run about 3 mins or so into getting to the Ubuntu desktop, and it always goes on prior to the power loss. The laptop doesn't feel warm at all though, it's been warmer/hotter when playing videos in Vista with no trouble.

How would I check with the sensors?

> **Lt. Surge said:**
> No, I believe either your battery is having issues or your laptop internal cooling ventilation isn't working properly. When did you get it and how often was it used? Did you ever dust it? Please include the answers in your OP along with your specifications.

If you have the tools and/or you haven't done it lately, you should open  up your laptop and check for dust. Get a compressed air can and blow  into the vents, see if any dust comes out. Then do a complete dusting of  the rest of the laptop.

EDIT: If you've not done this before also consider removing the battery  before going into your laptop. This is standard procedure whenever doing  so.

I've never had trouble with the battery but in the past I have managed to blow the graphics card a few times from overheating, resulting in getting new motherboards - a new motherboard was replaced before trying out Ubuntu, however. It's a laptop from 2007 and I did use it quite often for some video heavy stuff, but with a new motherboard (I hope it's not a defective one that was put in though) the first thing I did since the replacement, apart from checking files, was to trial Ubuntu. Will add the info to the OP.

Never actually taken a laptop apart, heh, it may be beyond my skill (my limit is basically sticking more RAM into an old desktop). I may just get myself a new laptop and try again as I noticed that since getting my motherboard replaced, my touchpanel volume/mute buttons aren't working. Sort of sick of the trouble I've had with this laptop, heh! It's a shame because I think apart from the overheating issue (I think that's the problem), Ubuntu looks like it'd run okay!

---

### Post by Hedgehog1 on 2011-02-07
The good news is: You found an excuse for a new laptop.

:lolflag:

At least this cloud has a sliver lining...

Of course, a new laptop will cost you some silver, too. :KS

---

### Post by DizzyDaze on 2011-02-08
> **Hedgehog1 said:**
> The good news is: You found an excuse for a new laptop.

:lolflag:

At least this cloud has a sliver lining...

Of course, a new laptop will cost you some silver, too. :KS

True! Hopefully I'll get a laptop that won't overheat/melt motherboards quite so much. I guess I can change this thread title to solved - it's not really an Ubuntu problem after all. Unless there's a setting in Ubuntu I can change to prevent it from overheating?

---

### Post by migs73 on 2011-02-08
> **DizzyDaze said:**
> Unless there's a setting in Ubuntu I can change to prevent it from overheating?

It's called the power switch :lol:

---

### Post by NightwishFan on 2011-02-08
To be honest, I would think there is not much you can do other than to add the cpufreq applet to the panel, and set it to powersave mode when you need it to be cool.

---

### Post by DizzyDaze on 2011-02-08
> **migs73 said:**
> It's called the power switch :lol:

I'm guessing that's a joke otherwise it's a reference that's gone over my head :confused:

> **NightwishFan said:**
> To be honest, I would think there is not  much you can do other than to add the cpufreq applet to the panel, and  set it to powersave mode when you need it to be cool.

Hmmm, okay. My laptop seems to have further issues that need fixing, so I guess my Ubuntu fix will have to wait until I get a new laptop, heh.

Thanks all for the help!

---

### Post by migs73 on 2011-02-08
I just meant if you have an issue with overheating, switching it off is the only thing going to stop it frying itself!!!

---

### Post by DizzyDaze on 2011-02-08
> **NightwishFan said:**
> To be honest, I would think there is not much you can do other than to add the cpufreq applet to the panel, and set it to powersave mode when you need it to be cool.

> **migs73 said:**
> I just meant if you have an issue with overheating, switching it off is the only thing going to stop it frying itself!!!

Heh, okay :)

---

### Post by Tyggna on 2011-02-08
on laptops, in the terminal (applications->accessories->terminal), you can type in:
```
acpi
```
That'll tell you whether its working off main power, charging, or discharging the battery.

If that turns up well, then go out and get those $5 compressed air cans, find the "air intake" on your laptop and use the can on it--works wonders for mine.

You can find your air intake by looking around your laptop for a fan behind some plastic grating.

---

