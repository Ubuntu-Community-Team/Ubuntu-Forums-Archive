---
title: "update or upgrade?"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by wiab4355 on 2009-05-25
I've been using my first Linux system, Ubuntu JJ, for about 2 months and enjoying it (he says guardedly).

When the next version comes out, apparently in October, does it overwrite everything or will it leave my programs and documents in touched?

This will be (obviously!) my first update/grade and I don't want to mess it up by not backing up stuff that's obvious to other users but not me!

Ian

AFC Wimbledon, Conference South Champions

---

### Post by _Purple_ on 2009-05-25
It will not overwrite your documents. :) You can either do an upgrade using network or using an alternate CD. You can check this page for more details:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by candtalan on 2009-05-25
> **wiab4355 said:**
> I've been using my first Linux system, Ubuntu JJ, for about 2 months and enjoying it (he says guardedly)

Welcome!

> 
When the next version comes out, apparently in October, does it overwrite everything or will it leave my programs and documents in touched?


New versions are released every 6 months, so yes the next version will be 9.10 and will be released in October.
(LTS versions such as 8.04 are released every 2 years and are supported for 3 years)

However note that the security updates will continue to be available for 9.04 (JJ) for 18 months - until October 2010, so you have no pressing need to upgrade to the new version in October 2009.

If your setting in
System>Administration>software sources 
[Updates][Release upgrade]
is 
Show new distribution releases
then you will be invited to upgrade to the new version as soon as it becomes available. There are other settings as you will see.

If at any time, you decide to accept the invitation to version upgrade, then in theory it will retain all of your files and settings - if possible. However, it would be most unwise to procceed with the process unless you had a trusted backup, just in case things screwed up.

is

---

### Post by lindsay7 on 2009-05-25
I used the upgrade on line system to upgrade 3 computers with no problems.  I used to upgrade from 8.10 to 9.04 . All you do when the time comes and you are ready to upgrade is hit alt + F2 and type update-manager -d on the line provided and that is it.

Right now for example you can get the early version of 9.10. As time goes on it gets updated and eventually it will be the full install. Remember that you can not jump versions with in online upgrade system so, when 9.10 is ready you need to be using 9.04.

---

### Post by Bill Sheppard on 2009-05-25
I've been using 8.10 for a little over 3 months now, and am 100% happy with it. Dumped MS/Windows and will never look back. Yeehaw:P. But after some nightmarish experiences with "upgrades" in MS/Windows, I'm leery of trying any upgrades now.. per the old adage "if it ain't broke don't **** with it." What are the hazards/pitfalls of trying the 9.04 upgrade? What are the hazards/pitfalls of *not* upgrading and just staying with the 8.10? thanks
Bill

---

### Post by XCan on 2009-05-25
Take a look at the known issues in [http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904) . It seems like, most issues I've run across on this forum seem to deal with graphics drivers, and in particular Intel's and AMD/ATI's. 

As for hazards on staying with 8.10, I really don't see any big hazards as long as it gets security updates.

---

### Post by raymondh on 2009-05-25
Hello Ian,

If you haven't yet, how about separating your /home to a different partition?  That is another way to preserve your settings, files, etc should you decide to do a fresh install instead of a network upgrade.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Happy Ubuntu-ing.

---

### Post by wiab4355 on 2009-05-28
Thanks to all

I think I'll do a backup right now!

Ian

---

### Post by glotz on 2009-05-28
Always a good idea.

---

### Post by fballem on 2009-05-28
> **Bill Sheppard said:**
> I've been using 8.10 for a little over 3 months now, and am 100% happy with it. Dumped MS/Windows and will never look back. Yeehaw:P. But after some nightmarish experiences with "upgrades" in MS/Windows, I'm leery of trying any upgrades now.. per the old adage "if it ain't broke don't **** with it." What are the hazards/pitfalls of trying the 9.04 upgrade? What are the hazards/pitfalls of *not* upgrading and just staying with the 8.10? thanks
Bill

My own experience with doing upgrades in ubuntu have been less than perfect. For example, in ubuntu 8.10, OpenOffice is still version 2.4 (by default), but in 9.04, it's OpenOffice 3.0. The configuration files are different.

How I approach the problem is that I will save my documents, pictures, music, and video files to an external drive. I use Evolution, so I will also run their backup utility and save that file to the external drive. I will also backup my FireFox favourites and save that file to the external drive.

I will then unplug the external drive and do a fresh install of ubuntu 9.04. When that's done, I'll then restore the documents, pictures, music, and video files. I'll run Evolution and select the option to restore from a backup (the backup that I made earlier). I'll restore my FireFox favourites from the backup.

I have, personally, found this approach to be the safest, particularly with the major changes to program versions between 8.10 and 9.04. Since everything that I need is in the repositories, the whole process takes about 3-1/2 hours _plus_ the time needed for the backup/restore operations.

Just some thoughts,

---

