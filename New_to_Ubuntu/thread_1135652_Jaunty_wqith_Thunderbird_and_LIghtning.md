---
title: "Jaunty wqith Thunderbird and LIghtning"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Oscar_Islix on 2009-04-24
HI!  I've just upgraded to Jaunty and all seems fine (minor problems with Firefoc but all OK now).  But I have a major problem with Thunderbird.  It seems to have totally lost my Lightning extension.  Says it is still there but I can't add a new event or task and it's lost all my existing calendars.  Can anyone help me please?  I'm pretty much a novice with Ubuntu so please keep the suggestions as easy as possible.

Many thanks

---

### Post by empty_spaces on 2009-04-24
Just to be sure, you upgraded from 8.10 using the upgrade command and not a fresh install, right? 
Was Lightning the only extension that you had? If you had others, are they working correctly?
The one thing that I can think of that might prevent Thunderbird from accessing your Lightning extension is if somehow the folder permissions may have got messed up. You can check that by going to **home/your-username/.mozilla-thunderbird** and check the properties on the extensions folder to see if you are the owner

---

### Post by Oscar_Islix on 2009-04-24
Thanks - just checked permissions and I seem to be the owner of the folder.  All the other extensions work fine.  I have even tried uninstalling Lightning and reinstalling it but still nothing.  Really weird because it looks as though its fine but just nothing there.  If that makes any sense.

---

### Post by Oscar_Islix on 2009-04-25
Just discovered Bug#278853 - known problem.  

libstdc++5 solves the problem on 9.04 and after reinstall lightning

Thanks everyone

---

### Post by rusyear04 on 2009-04-27
[COLOR="Red"]question anwered :)[/COLOR]

i did install libstdc++6 parallel to 5 and now lightning seems to work. will try the synch-install as well.
if i experience problems i will report them :)

=====================
> libstdc++5 solves the problem on 9.04 and after reinstall lightning

do you have to install libstdc++5 in parallel to libstdc++6 or instead of 6??

thanx!

---

