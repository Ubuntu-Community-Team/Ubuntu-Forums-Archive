---
title: "Sharing Firefox / Thunderbird profiles - a working method?"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by Applegeek on 2009-09-22
OK, here's what I really need to do:  Share bookmarks, passwords, cookies and emails between Firefox and Thunderbird on a dual-boot machine, with a method that actually works.  Our company security policy prevents storing any sort of password info on an outside server, so xmarks is out.  Rather not use a "backup" program, I'm looking for a way to truly share the data between Xp and Ubu X64 - seamlessly.  When I boot into either OS I need the shared data to be in place, without extra steps.

What I did was use the ProfileManager on both Firefox and Thunderbird to have their profiles setup on a neutral NTFS partition.  At first glance that sorta works...BUT the extensions are screwed up.

Whenever any add on is added while in the XP side, say for instance you add the Lightning calandar to Thunderbird, and go to the Ubu side, the lightning data is all scrambled. Or if you add AdBlock plus to Firefox on the Ubu side, then when you start Firefox in Windows the AdBlock data will be hosed also.  Obviously the extensions won't share properly between Xp (32) and Ubu (X64).  We have X64 installed for some scientific apps we have to run.

SO:  How do you share JUST the emails / bookmarks / cookies and passwords between the two OS's WITHOUT getting the extensions fouled up - but keeping the data the extensions need intact?

---

### Post by LewRockwell on 2009-09-22
you may/might hack something together where it works "sometimes"

we don't recommend it and subsequently don't support or warrantee it

.

---

### Post by Applegeek on 2009-09-22
So, no way to do this?  I guess what I'm looking for is the functionality of xmarks - but without the external website, so the data is always local to the my machine...or at least to the in-house network.

---

### Post by philinux on 2009-09-22
[http://www.google.co.uk/search?q=Sharing+Firefox+%2F+Thunderbird+profiles&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.uk/search?q=Sharing+Firefox+%2F+Thunderbird+profiles&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

First hit looks good but old.
[http://ubuntuforums.org/showthread.php?t=203524](http://ubuntuforums.org/showthread.php?t=203524)

Maybe you need to do more searching but I'm sure a solution is out there.

---

### Post by oldfred on 2009-09-22
I have Firefox and Thunderbird shared between Ubuntu 32 bit and Windows XP. I have had no issues, but have heard that Lightning calendar does not work. I do not use the calendar functions. I do have Adblock, autopager and a few other extensions and the only error I get is in Shiretoko missing Ubuntu add ins, since it is not offical yet.
When I travel I copy the entire profiles for both Tbird & FF to my Windows portable and then copy it back when home without any issues.
I have also upgraded from ver 2 to ver3 and now 3.5 for Firefox and whatever Thunderbird upgrades over the last 3 years on both Windows & Ubuntu without any issues. Three years ago I was primarily Windows and now only Quicken prevents me from being 100% Ubuntu so I do not use the Windows side very much any more.
Info on sharing:
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

---

