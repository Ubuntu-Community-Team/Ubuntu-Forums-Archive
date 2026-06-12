---
title: "Wine problem"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Hsueh Lin Chen on 2009-11-05
I tried to install ragnarok online through wine and i got to the step of patching it... an deficiency or program error problem came out,[IMG]http:///home/daniel/Desktop[/IMG] _[IMG]http:///home/daniel/Desktop[/IMG] _i was not able to log into the game w/o patching it... 
Is there anyway to solve this issue? thx for your time.

---

### Post by Mark Phelps on 2009-11-05
The link below points to the Wine Application Compatibility page.  enter ragnarok in the name area and click the update filter button:

[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true")

If you're talking about version 2, and you patched it to be the version shown in the table, you ended up with an app rated Garbage, meaning, it is NOT going to work.

---

### Post by Hsueh Lin Chen on 2009-11-05
I tried the method and found the wine that is suppose to be compatible (wine 1.1.20) [http://appdb.winehq.org/objectManager.php?sClass=version&iId=8370](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8370) but it is not available i think for dl and it is for jaunty while i have karmic. When i followed the instructions on  [http://wiki.winehq.org/Ubuntu](http://wiki.winehq.org/Ubuntu) i think i can only get the newest ones, which showed the error. The ragnarok server im looking for is private if that makes a difference (apparently it does for the site.)

Thank you for your time, and it would be awesome if you can give me some more specific instructions. ^^

---

### Post by SunnyRabbiera on 2009-11-05
Actually you can install the jaunty build of Wine in Karmic if you really need it, Karmic is newer so not everythimng has been ported yet.
Jaunty packages should work though, but Wine itself is not percfe3ct so your desired software might not work.

---

### Post by Hsueh Lin Chen on 2009-11-06
> **SunnyRabbiera said:**
> Actually you can install the jaunty build of Wine in Karmic if you really need it, Karmic is newer so not everythimng has been ported yet.
Jaunty packages should work though, but Wine itself is not percfe3ct so your desired software might not work.

does the newer versions of wine works like the older ones (wine 1.1.32 vs wine 1.1.20) generally or do i have to get the wine 1.1.20 which is the one that is said to work.

---

### Post by SunnyRabbiera on 2009-11-06
> **Hsueh Lin Chen said:**
> does the newer versions of wine works like the older ones (wine 1.1.32 vs wine 1.1.20) generally or do i have to get the wine 1.1.20 which is the one that is said to work.

Well if i were you i would use the suggested version for your desired software.
Sometimes newer doesnt mean better, give it a shot in later versions though never know.
Wine is kinda fuddy duddy sometimes, its not meant to be a full drop in replacement for windows.

---

### Post by Hsueh Lin Chen on 2009-11-10
are there any other windows emulator that may be effective? before i go to jaunty

---

### Post by Mark Phelps on 2009-11-10
> **Hsueh Lin Chen said:**
> are there any other windows emulator that may be effective? before i go to jaunty

Yes, but not free ones.  Google on Cedega and Crossover.  Both of these are commercial products, requiring subscriptions to use.  Crossover is the commercial version of Wine, so what doesn't work in Wine is also most likely to NOT work in Crossover, either.

Your other alternative is to use VirtualBox to install a VM in your machine and install an MS Windows OS inside that -- but then you need a working license and the full space for an MS Windows installation.

---

