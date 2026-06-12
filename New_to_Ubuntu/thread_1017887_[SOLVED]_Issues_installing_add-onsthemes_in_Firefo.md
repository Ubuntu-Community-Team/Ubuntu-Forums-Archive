---
title: "[SOLVED] Issues installing add-ons/themes in Firefox"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by daarkstaar on 2008-12-21
Hi-
I'm having issues installing any add-ons in Firefox.  When I go to the Firefox add-ons page at Mozilla.org and click on the "add to Firefox" button nothing happens.  If I right-click and try to open in new tab, the tab just loads forever and nothing comes up.  If I go through Tools -> Add-ons in Firefox and I click on "add to Firefox" I get the loading icon and it shows "connecting..."  Nothing happens for about 5-10 minutes.  Then the download icon appears.  If I click that I get the loading icon and it says downloading.  It stays this way for a long time.  I waited last night for 30 minutes while "downloading" foxmarks, but gave up and went to bed.  When I got up today it had finally installed.
Does anyone know what's going on here?  At this rate it will take me until New Years to get my extensions installed!!
I have a new install of 8.10 with no extra packages installed yet.  I removed Firefox via synaptic, and reinstalled, but no luck.
Please help!

---

### Post by eagle416 on 2008-12-21
Please post your system specs here. Were you running any other programs at the time?

---

### Post by jimmy the saint on 2008-12-21
Have you tried going to the extensions website and installing from there?

---

### Post by daarkstaar on 2008-12-21
@eagle416

 There were no other programs running besides FF.

Intel e6750 2.66
4GB ddr2
Gigabyte GA-P35-DS3R
Corsair 620 Watt PSU
XFX 8800 GTS

@jimmy the saint

Do you mean Mozilla's extensions page?  I did try it from there...


UPDATE - I just got adblock plus to install - it hung for 45 minutes and then finished... this is wierd


BTW - I had no problems with FF in 8.04

---

### Post by daarkstaar on 2008-12-21
I've gotten a couple other add-ons installed, but it takes on average 45 minutes for the process to complete.
Has anyone seen anything like this before?

---

### Post by daarkstaar on 2008-12-21
I found some info on this issue here from some Gutsy users [http://ubuntuforums.org/showthread.php?t=587533&page=2](http://ubuntuforums.org/showthread.php?t=587533&page=2).  Apparently it has something to do with ipv6 dns lookup.

Still not sure why it's happening, but editing about:config in firefox and setting networkdns.disable.ipv6 to true has solved my problem.

---

