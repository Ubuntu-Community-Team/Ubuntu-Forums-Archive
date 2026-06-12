---
title: "Lost cupsys Whereditgo ?"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by Septuagenarian on 2009-09-23
After many months of satisfactory use ( since jaunty install ) my cupsys has disappeared , I've tried all the restart procedures but all I get is  " exiting child status 1 " whatever that means .  My printer works perfectly in Windows via the same cable so it's not that. I seem to recall a recent update to cupsys in update manager and it's not worked since , is there any way to roll back the update ?  I thought of trying HPLIP to configure the printer , but when I type hplip-gui , which is installed , nothing happens . I've also checked all the dependancies , and cupsys update , still nothing . Any suggestions please ?

---

### Post by Septuagenarian on 2009-09-23
Further to the above I have now discovered that a ppd file is missing and I can no longer connect to localhost 631 . I have looked on the installation disc CD but of course only the Windows files show up .
After much messing I have now got HPLIP to work and it has located my printer correctly but still asks for the ppd file , but wont browse the CD even though it is mounted and shows up on my desktop .
Hope this helps.

---

### Post by cariboo on 2009-09-23
Check System-->Administration-->Synaptic Package Manager to see if cups is installed, just type cups in the search box, and you should see it in the list.

---

### Post by Septuagenarian on 2009-09-24
Yep , its there , and also its enabled in my startup services list . I temporarily fitted an old hard drive with Hardy and Intrepid dual boot , strangely enough the printer works with Hardy but not with Intrepid . Weird or what ? Must be different versions of cupsys.  As a matter of interest , is it better to have the printer switched on at startup , or wait till everything is running then switch on ? I think I'll go on the HP site to see if I can find this ppd file .

---

