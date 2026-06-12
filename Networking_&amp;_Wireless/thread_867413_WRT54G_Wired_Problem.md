---
title: "WRT54G Wired Problem"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by ren4 on 2008-07-22
Hi,

I've been running ubuntu (on a desktop and a laptop) for 5-6 months now.  Earlier tonight, we had a thunderstorm and lost power for a few hours.  After the power came back on, I had to reconfigure the router to connect to the net.  

Now everything is back up and running, except I can no longer connect to the internet with Ubuntu through the WRT54G router.  

I can connect directly through the DSL modem with Ubuntu.  I can connect through the router with Windows (and so I'm back on XP for the first time in months).  So it would seem that a hardware issue is out.  I can also connect to other wireless networks, but not my own with the laptop?  

Does anyone have an idea of how I can fix this?  Thanks for your help in advance!

---

### Post by dmizer on 2008-07-22
just because it works in windows, doesn't mean your router isn't toast.  and, it really looks like that's the case here.

have you tried different ethernet ports?  one may be fried while another is ok.

your router is deeply suspect because you had to reconfigure it after the storm.  that means the router's firmware was effected by the storm somehow.  this could cause any number of strange problems with your connection.

---

### Post by ren4 on 2008-07-23
Thanks for the response.  I did try switching the ports.  And your conclusion makes sense.  

I also tried installing dd-wrt micro (apparently that's all the WRT54G ver 6 can handle).  

It's a similar problem.  In Windows I can configure the settings, but I still can't get the Ubuntu box to even see the thing.  (I didn't bother with the actual DSL info yet.)  

Either way, I need the internet on my laptop, so I'll pick up a new router.  

Does anyone have any firmware recommendations or fun projects for an almost bricked wrt54g ver 6 router?

---

### Post by sputnikkk on 2008-07-23
If the router works under windows but not ubuntu - how is it suspect and possibly toast?

Hardware either works or it does not - its not OS discriminatory!

Networking in Ubuntu Hardy 8.04 is whats suspect - especially through the built in NetworkManager GUI. 

How is your desktop configured to manage wireless connections?

What ver of ubuntu are you on?

I suspect a minor user setting vs a toast router.

---

### Post by DrOlaf on 2008-07-23
> **ren4 said:**
> Thanks for the response.  I did try switching the ports.  And your conclusion makes sense.  

I also tried installing dd-wrt micro (apparently that's all the WRT54G ver 6 can handle).  

It's a similar problem.  In Windows I can configure the settings, but I still can't get the Ubuntu box to even see the thing.  (I didn't bother with the actual DSL info yet.)  

Either way, I need the internet on my laptop, so I'll pick up a new router.  

Does anyone have any firmware recommendations or fun projects for an almost bricked wrt54g ver 6 router?

If you are going to get yourself a new router, and want some ways to play around with the old Linksys, you could always flash the firmware with an alternative version that unlocks a load of new features. There used to be a free version called Satori, that I've been running on my WRT54G for years (I originally put it on there to enable the use of my Airport Express as a range extender). 

I think the free version has now been replaced with a subscription-based one (get it from [http://www.sveasoft.com/]("http://www.sveasoft.com/")) but the freeware one may still be available. 

I've used Satori for so long now that I can't even remember what the original firmware looks like :)

---

### Post by dmizer on 2008-07-23
> **sputnikkk said:**
> If the router works under windows but not ubuntu - how is it suspect and possibly toast?

Hardware either works or it does not - its not OS discriminatory!
actually, that's not true.

happens more frequently than you would suspect: [http://ubuntuforums.org/showpost.php?p=5188719&postcount=39](http://ubuntuforums.org/showpost.php?p=5188719&postcount=39)

i've seen it happen often enough that i know it's a very real possibility in this case.

---

### Post by ren4 on 2008-07-23
> **sputnikkk said:**
> If the router works under windows but not ubuntu - how is it suspect and possibly toast?

Hardware either works or it does not - its not OS discriminatory!

Networking in Ubuntu Hardy 8.04 is whats suspect - especially through the built in NetworkManager GUI. 

How is your desktop configured to manage wireless connections?

What ver of ubuntu are you on?

I suspect a minor user setting vs a toast router.

On the desktop, I'm using 8.04, but that's a wired connection.  On the laptop I'm still using 7.10 (with ndiswrapper on a broadcom chip).  I checked the wired connection with a live disk too (probably 8.04 but I can't remember for sure).  Everything worked yesterday with no fuss before the storm.  

Neither the laptop or the desktop will connect to the router, although the laptop can see the wireless signal and connects just fine to my neighbors conveniently unencrypted wireless.  

I have the same connection problem with the dd-wrt installed.  Which makes me think it's an odd hardware issue in the router and not the firmware.  

Thanks again for all the help!

---

