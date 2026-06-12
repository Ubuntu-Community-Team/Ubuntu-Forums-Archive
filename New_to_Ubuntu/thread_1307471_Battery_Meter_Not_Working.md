---
title: "Battery Meter Not Working"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by jandalchick on 2009-10-31
I've just installed Ubuntu 9.10 on two laptops; a 64bit version on a new vaio and a 32 bit version on an older HP laptop.  The battery meter appears to work fine for the vaio but doesn't work at all on my HP.  I also had this problem with 9.04 on the HP, however although it was inconvenient not being able to see the battery status, it didn't impact on use of the computer.  

The battery status reads unknown, 0.0% (it picks up if it is on AC or battery but always 0.0%).  My problem with 9.10 is that if I unplug the laptop power cable, after 10s or so it seems to put the computer to sleep so I can only use it when it is on AC power.  Sure the battery is pretty old and useless, but it can normally at least run the computer for half an hour or so without being plugged in.  Has anyone else had this problem, and is there a way to fix it or get around it?

Cheers!

---

### Post by HotShotDJ on 2009-10-31
Power management is now handled by DeviceKit in Karmic rather than HAL and it is apparently causing issues with a lot of laptops.  In my case, it shows percentage, but cannot figure out time remaining or time until full charge.  See [Bug #444881]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/444881").

---

### Post by humphreybc on 2009-10-31
I've noticed in Karmic power preferences, the option to "do nothing" for when the power gets low and lid closed actions etc has disappeared.

Anyone know how to set this back? Gconf value perhaps?

---

### Post by Sortini on 2009-11-01
Hi,
Fortunately, if I move mouse cursor to the battery icon then a notification shows me how much time remaining I have. But I want battery time remaining to be displayed constantly in the system tray. In Ubuntu 9.04 I had installed some application which was doing this but after upgrade to Ubuntu 9.10 this application disappeared and I can't remember it's name. Thank You for help.

---

### Post by rewyllys on 2009-11-03
> **Sortini said:**
> Hi,
Fortunately, if I move mouse cursor to the battery icon then a notification shows me how much time remaining I have. . . . In Ubuntu 9.04 I had installed some application which was doing this but after upgrade to Ubuntu 9.10 this application disappeared and I can't remember it's name. Thank You for help.

Sortini, I'm experiencing the same problem of the former battery level indicator having disappeared, in 9.10, from the top panel.  I hope an answer to how to restore this indicator will be posted here by someone.
But I also am curious about the battery icon to which you refer.  What is this icon? and how did you get it to be installed?  
Thanks.

---

### Post by Sortini on 2009-11-04
That was neither gnome-power-manager nor kpowersave. That was little battery placed horizontally with green filling. Moreover that was icon indicating AC/battery using. And first of all the time remaining (to discharged if using battery and to charged if using AC) was being displayed. I even can't remember how it was installed. My fault I didn't bookmark site it had been downloaded from.

Battery level indicator can be added to the top panel in the following way: go to System->Preferences-> Power management-> Tab General->Notification area->Always display an icon. Hope this will help.

---

### Post by sethtriggs on 2009-12-07
> **rewyllys said:**
> Sortini, I'm experiencing the same problem of the former battery level indicator having disappeared, in 9.10, from the top panel.  I hope an answer to how to restore this indicator will be posted here by someone.
But I also am curious about the battery icon to which you refer.  What is this icon? and how did you get it to be installed?  
Thanks.

I, too, would like to see this indicator return to always be present in the tray. The small black notification bubbles are too unobtrusive for me to notice till it's too late.

-Seth

---

### Post by Muskegman on 2009-12-19
Thanks for the information, its great having my battery indicator back on my laptop     :P

---

### Post by Sortini on 2009-12-27
I still have not solved problem of permanently displaying remaining time, but I've noticed that: - I don't spend time on looking how much battery I have; - I see blue colour, then it's okay, I don't calculate how much I can do in this time etc.; - one thing less to disturb while working; - I have no more (unnecessary) situations like that: there is 75% battery, you burn CD or process an image and at such power consumption you have only 30 minutes remaining time, and you start thinking about it, but after 5 minutes this tasks are done and now you have hour and a half again.
I think the less precise information is the more stable one, and that might be relevant for such an information. I'd only like to know whether this is intended for the sake of an average user.

---

### Post by sethtriggs on 2009-12-28
> **Sortini said:**
> I still have not solved problem of permanently displaying remaining time, but I've noticed that: - I don't spend time on looking how much battery I have; - I see blue colour, then it's okay, I don't calculate how much I can do in this time etc.; - one thing less to disturb while working; - I have no more (unnecessary) situations like that: there is 75% battery, you burn CD or process an image and at such power consumption you have only 30 minutes remaining time, and you start thinking about it, but after 5 minutes this tasks are done and now you have hour and a half again.
I think the less precise information is the more stable one, and that might be relevant for such an information. I'd only like to know whether this is intended for the sake of an average user.

However, this is a significant issue for me, as the battery charge warning is not easy to see (the change in color/design is too subtle). In addition, I think the timer is necessary to activate features such as the automatic hibernate when battery is low.

The older battery charge monitor, with the different colors (green, yellow and red) was much larger and easier to see, plus the time allows you the ability to plan your power-saving options much more easily. Right now I have to break my work to mouse over to the battery indicator. On occasion I've been too late to save my work as I was not able to see the flashing critical battery indication on my laptop until it was too late.

-Seth

---

### Post by irielion on 2010-01-14
There is a commandline tool called IBAM. It has a better indication of the battery and it shows the time remaining. I wrote an applet for ibam to totally mimic gnome-power-manager applet. It even integrates with it's translations. Upon startup it will try to hide the gnome-power-manager applet, but you'll need my special patch one. Packages can be found in my ppa:
ppa:mark-baas123/ibam-applet

Greetings,

Mark

---

