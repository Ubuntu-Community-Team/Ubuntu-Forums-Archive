---
title: "Hardy hung on install at 90%"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by isee on 2009-04-30
Gateway MX6441 laptop

Well that didn't go too well.  I had to push the power button.

This is pretty new to me, my first attempt at a partition and now my Windows C:\ is only half as big as it was.

I had it working with Wubi, even updated and got the Broadcom wireless going (that part Hardy mainly did by prompting me).
It crashed once under Wubi after showing me the proprietary drivers screen.  I can't recall exactly what happened but it rebooted and then hung on a text screen (you know, the ones that usually flash by before the splash screen shows up) which just kept repeating a Broadcom error.  I can say more about that if anyone wants to know.  Soooo....  I had to push the power button there too.  But that went well 'cause the error message contained the www of the site to retrieve the firmware and reboot allowed me to get online and access the goods which then Hardy used that fwcutter thingy to get my Broadcom working.  Was good!

So I decided to try Intrepid with Wubi.  Worked to install, but no Broadcom prop. drivers using the Hardware Devices (is that right?  I don't have Ubuntu at all right now so no reference).
So no wireless support like I got in Hardy so decided to go back.

Second install of Hardy with Wubi hung after main install while installing the 96(?) updates, hung while installing a Gnome one.  Had to push the power button there too.  A reboot into Ubuntu loaded the screen fine, mouse worked, but nothing clicked i guess you might say.  No menus worked.

So I decided to do what I'd set out to do and partition my drive and install a Linux OS and I chose Hardy.  The missing half of my drive I have seen, because I went so far as to start a reinstall, but it wanted to partition the other half of my drive that had Ubuntu on it already, and I just canceled it.

I hoping the answer is I'm gonna have to try a manual partition and overwrite the partition where the last install attempt occurred.

This all started with an online Wubi Jaunty install which ended all 3 times Ive tried Jaunty with this error -
X An error occurred Permission denied For more info see log file c:\docume~1\owner\locals~1\temp\wubi-9.04-rev128.log
- I can post log if anyone wants.

I hope this makes sense.
PS I have a folder at C:\ubuntu-backup in my Windows now.
Cheers

---

### Post by Zeedok on 2009-04-30
Doesn't sound like you're having much fun.  I haven't had much experience with wubi (I've never tried it), but I thought you could uninstall it like any other "windows" program.

As for your partitions . . . the best way to sort these kind of problems is with the Live CD - I even used the GParted live CD a few weeks ago, it's great for "rescue" operations.  Delete all the failed linux installations (not your windows one!!) and start all over again, I would suggest either 8.10 (Intrepid) or persisting with 9.04 (Jaunty).  I would not use Hardy - it will not be supported for much longer.

Good luck.

---

### Post by isee on 2009-04-30
Thats very reassuring Zeedok.  Doesn't sound too bad then, and will investigate the GParted liveCD.

Yes every Wubi install was followed by an uninstall, but that was never my intention to run it like that.  Didn't even know such a thing existed 'till I ran into it on the web page.

I think I will go with Intrepid, you know it's a very appealing name.  Then maybe upgrade later because I've read you can go from 8.10 to 9.04

---

### Post by Zeedok on 2009-04-30
Back-up your data first, just in case.  Every time I have mucked something up I've learned more about linux and computers in general, so look at it that way.

---

### Post by isee on 2009-04-30
Thanks again.  No worry's on a data backup as there is none to back up.  My D:\ recovery drive was wiped out accidentally a couple of years ago, and I have done a clean Windows install from XPSP1 to SP3 (many hours of downloading and rebooting, installing drivers and programs).

I have 2 questions.  Why can't I see the Ubuntu partition like I could my D:\ drive when in Windows?  Shows my entire HD as being only 36GB from in Windows.  Thats the half I gave it while partitioning with Hardy.

Related to that, when I boot from the Hardy liveCD and chose install now, when the partitioner comes up I can only see the 36GB I gave to Ubuntu from the earlier install attempt.

Should this be a new post?

---

