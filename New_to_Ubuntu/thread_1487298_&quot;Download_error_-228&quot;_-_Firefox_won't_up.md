---
title: "&quot;Download error -228&quot; - Firefox won't update add-ons"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by anothernewuser on 2010-05-18
Ummm ... been fighting with 10.04 for a few days trying to work out DVD playback issues (Did i win?  Not really) ... finally got back to fighting with it about other stuff ... aaaaaaaandddd

When I started up firefox it told me that NoScript needed an update so I clicked on Install ... update seemed to start then hung and eventually I got this message:



Firefox could not install the file at 

[http://releases.mozilla.org/pub/mozilla.org/addons/722/noscript-1.9.9.77-fx+sm+fn.xpi](http://releases.mozilla.org/pub/mozilla.org/addons/722/noscript-1.9.9.77-fx+sm+fn.xpi)

because: Download error
-228


Ummm ... ???


I have tried switching to another account and it can't download updates to add-ons either.... not NoScript.

This is Firefox 3.6.3 and it seems to do everything else ok .. just not downloading updates to add-ons.

Is this a simple thing to fix? Anyone know?

I've prowled the forums a bit it seems people always recommend removing your profile and starting over with Firefox issues - ummmm ... I don't know if thats the answer or not ... and, to be honest, I'm not entirely sure what to do ...???

I followed this link before ([http://www.ubuntuforums.org/showthread.php?t=201488](http://www.ubuntuforums.org/showthread.php?t=201488)) - at least I think thats it - from Psychocats when firefox was misbehaving 'but it seems to have gone dead or perhaps that's yet another issue in my system?  I believe it renamed my Mozilla profile and let firefox establish a new one ... ummm ... maybe? was a long time ago... I don't believe I use anything else that would have info there soo not a problem to do this I suppose if it would work and if I knew how.

Any help or advice would be appreciated muchly.

---

### Post by ubunterooster on 2010-05-18
type ```
about:config
``` into browser "go to" bar. go to the line in screenshot  [network.dns.disableipv6] and double click it so it says "true"

---

### Post by anothernewuser on 2010-05-18
Thanks for coming to my rescue:


Did that - no difference though.



Hmmm ... some 2 hours later tried again aaaaaaaaannnnd .. for some reason .. I am able to update and install extensions.

*shrug*
 
[Solved] I guess ;)



Perhaps this was never an issue with my system then??

I'm soo confuzzled :)

---

### Post by lovinglinux on 2010-05-18
Mozilla AMO is under heavy changes recently. They are partially migrating several content pages from the old codebase to the new zamboni codebase. As you can see on the site, some installation buttons have already changed on some pages, but not on all of them. It will will take a couple of weeks before the entire site is completely moved to the new codebase. Until then, you will probably experience some weird issues. For instance, a couple of days ago it let me install an extension that wasn't available for Linux.

I have experienced this error 228 a couple of times, but usually if you try again a couple of minutes later it will install.

---

### Post by anothernewuser on 2010-05-18
Oohh ... okie dokie then.

I had no idea about that .. guess I won't worry too much about such things for the next little while then.


Thanks for the info.

---

### Post by MoreCowBell on 2010-08-01
> **ubunterooster said:**
> type ```
about:config
``` into browser "go to" bar. go to the line in screenshot  [network.dns.disableipv6] and double click it so it says "true"
I want to thank you, ubunturooster, for the solution to the problem that I was having downloading Add-ons to Firefox. I am running version 3.6.8 right now, but I had the same problem with the previous three or four versions. I kept getting Download Error code -228. But, thanks to your tip, on entering, "about:config" (I have never done that before), I have avoided a complete reinstall of Ubuntu. Thank you so much! That tip is on the money!

---

### Post by lovinglinux on 2010-08-01
> **MoreCowBell said:**
> I want to thank you, ubunturooster, for the solution to the problem that I was having downloading Add-ons to Firefox. I am running version 3.6.8 right now, but I had the same problem with the previous three or four versions. I kept getting Download Error code -228. But, thanks to your tip, on entering, "about:config" (I have never done that before), I have avoided a complete reinstall of Ubuntu. Thank you so much! That tip is on the money!

See more about:config tips to boost Firefox performance on my blog: [http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html](http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html)

---

### Post by siretfel on 2010-10-24
> **MoreCowBell said:**
> I want to thank you, ubunturooster, for the solution to the problem that I was having downloading Add-ons to Firefox. I am running version 3.6.8 right now, but I had the same problem with the previous three or four versions. I kept getting Download Error code -228. But, thanks to your tip, on entering, "about:config" (I have never done that before), I have avoided a complete reinstall of Ubuntu. Thank you so much! That tip is on the money!

yeap that saved my day too. thank you  very very very very much.

---

