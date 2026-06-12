---
title: "FIXED: Dell wireless 1390 with ndiswrapper after upgrade to feisty"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by superchris on 2007-06-06
I had a real pain with this so I thought I would share my pain in hopes someone else can avoid the same thing.  I upgraded to edgy and then feisty from dapper.  Had my Dell Inspiron 9400 with built in Dell 1390 wireless card working fine on Dapper by using ndiswrapper.  Then when I upgraded it didn't work.  I tried and tried and eventually got it "kind of" working.  I tried the fwcutter approach and it would work, but only until the next time I rebooted.  Each time I rebooted I would have to run the fwcutter script, put my laptop to sleep, and wake it up again.  Stumped me for a week, and very annoying.  Finally I figured it out... when I upgraded to Feisty it added the bcm43xx module which was conficting (evidently) with my previous succesful ndiswrapper install.  When I blacklisted bcm43xx (add a line to /etc/modprobe.d/blacklist) and rebooted all was well.  So bcm43xx and fwcutter might work fine.  Ndiswrapper also works very well.  But using them both and the same time is bad, bad, bad!

Don't be like me ;)

---

