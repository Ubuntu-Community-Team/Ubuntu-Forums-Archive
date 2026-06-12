---
title: "Hardy Heron Hoses Wireless"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by Kawa800 on 2008-06-06
In Gutsy, I had used the unrestricted driver manager to enable my wireless card and followed KevDogs instructions to set up wireless manually.  When I upgraded to Hardy the wireless was hosed. :( The card no longer showed up in hardware manager.  I tried Ndiswrapper, but could not get it to work.  I spent a few weeks working on this off and on.  And from reading the posts I know I am not alone.  It wasn't easy getting wireless to work in Gutsy to begin with, but it worked.  I have finally resorted to going back to Gutsy.  Completely wiped the laptop and started over.  In less than 2 hours I had Gutsy on there, fully updated and the wireless working.  I am a recent convert to Linux and am tempted to go back to Windows, just because of how difficult it is to use wireless in Linux.  I am still hanging in there though.  I just won't be upgrading to Hardy any time soon.  (I have a desktop and the laptop both running Gutsy on wireless.)

I have looked at a lot of posts of people having trouble with wireless.  I understand it has something to do with the makers of the chips and cards not allowing open access to their code.  I am just curious if there is a reason that it would seem that things got worse instead of better from Gutsy to Hardy?

---

### Post by Peter K Nicol on 2008-06-06
It would be great if someone could tell us what is wrong. I found the wireless connection in Fiesty better than Gutsy. So far no more than very partial success with Hardy (after 4 weeks trying).

---

### Post by Ayuthia on 2008-06-06
Well, the big thing with Hardy is that it brought in the new kernel (2.6.24).  In this kernel, they (wireless developers not Ubuntu) introduced some new drivers.  The ones doing work for the Intel cards brought in the iwl* drivers and the developers for doing the Broadcom cards brought in the b43 drivers.  This changed the way the wireless cards worked.  Because of this new introduction, a lot of work is being done to make the new drivers work.  When they do work, they are usually better than the old drivers.  However, there are a lot of work being done to make the new changes work also.

I heard that there is a fix for the Broadcom drivers that will make a couple more cards work (4311 rev 02 and 4312 rev 02), but they do not come out until 2.6.24-18.

For NDISwrapper and Broadcom cards, there is also a conflict with the ssb driver.  The b43 (wireless) and b44 (wired) drivers use the ssb driver.  The ssb driver will immediately grab the Broadcom card and will not share with the NDISwrapper driver so the ssb driver needs to be removed and added after NDISwrapper.  Because of this, an additional script needs to be added so that the ssb driver is loaded after NDISwrapper if ssb is needed.

Another change is that with the newer kernel, the compiler changed also.  Because of this, the code for some of the wireless drivers have to be modified so that they will compile for the new kernel.  

Since Ubuntu has a six month cycle, the group had to choose between using 2.6.23 or 2.6.24.  The newer kernel does have new features that have helped some people, but of course, it also has made some people struggle more.  

I am thinking that the next release (I think that there is going to be another one soon--before the October one) that will help fix some of the issues.  The community has also done a lot in trying to communicate the fixes/workarounds to help make it work.

Having a six month release cycle brings in a lot of the latest and greatest changes, but will also bring in a lot of changes in a short time period that will need some extra time to fix.

The best places to look for help is usually here in the forums and also to take a look at [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/).  The community also provides some documentation that will help.  There is a lot of information in there though.

---

