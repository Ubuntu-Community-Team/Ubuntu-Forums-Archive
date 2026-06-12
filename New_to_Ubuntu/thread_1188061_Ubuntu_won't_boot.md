---
title: "Ubuntu won't boot"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by sciencegirl on 2009-06-15
Hi! 

I have Ubuntu and Windows Vista Business installed on my Dell Prcision T7400. Both were booting fine until last week. Now Ubuntu only boots maybe once in every ten attempts. When Ubuntu won't boot I get the following error message:

ubuntu\winboot\wubildr.mbr corrupt or missing
status: 0xc000000e

Windows always boots fine. 

Can anyone help me get Ubuntu up and running again? I miss it. :(

Thanks!!!
Abby

---

### Post by salvachn on 2009-06-15
You use WUBI, right? If you either suspend or hibernate Vista, or if Vista shuts down improperly(it does most of the times!) then the drives containing Hibernation and Paging files cannot be accessed by Ubuntu or any other distro at startup. So take care not to try booting Ubuntu after hibernating Vista or an improper shutdown.

Otherwise [http://www.maximumpc.com/forums/viewtopic.php?p=799547&sid=26c47dc36e879e98ac7910de9d758303](http://www.maximumpc.com/forums/viewtopic.php?p=799547&sid=26c47dc36e879e98ac7910de9d758303) has some help.

---

### Post by sciencegirl on 2009-06-16
I always try to boot into Ubuntu from a restart - never a hibernation or bad shutdown. 

I tried the bootrec.exe/fixmbr - it said it was successful but Ubuntu still won't boot and I still get the same error message as above.

Anything else I can try?

---

### Post by sciencegirl on 2009-06-16
I asked this question in the General Help but the answer I got didn't work so I thought I would try here.

I have Ubuntu and Windows Vista Business installed on my Dell Prcision T7400. Both were booting fine until last week. Now Ubuntu only boots maybe once in every ten attempts. When Ubuntu won't boot I get the following error message:

ubuntu\winboot\wubildr.mbr corrupt or missing
status: 0xc000000e

Windows always boots fine. 

I tried using the System Recovery Disc and Bootrec.exe/FixMbr  - it said it fixed it but Ubuntu still won't boot and I get the same error message.

Can anyone help me get Ubuntu up and running again? I miss it. :(

Thanks!!!
Abby

---

### Post by pixel :-) on 2009-06-16
try on this forum

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

I'm not familiar with wubi, but ask some one to post his "wubildr.mbr"

backup yours, and replace it, maybe it will work

---

### Post by sciencegirl on 2009-06-17
I asked this question in the General Help but the answer I got didn't work so I thought I would try here.

I have Ubuntu and Windows Vista Business installed on my Dell Prcision T7400. Both were booting fine until last week. Now Ubuntu only boots maybe once in every ten attempts. When Ubuntu won't boot I get the following error message:

ubuntu\winboot\wubildr.mbr corrupt or missing
status: 0xc000000e

Windows always boots fine. 

I tried using the System Recovery Disc and Bootrec.exe/FixMbr - it said it fixed it but Ubuntu still won't boot and I get the same error message.

Can anyone help me get Ubuntu up and running again? I miss it. :sad:

Thanks!!!
Abby

---

### Post by sciencegirl on 2009-06-17
Thank you - I will try!

---

### Post by overdrank on 2009-06-17
Please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by metalf8801 on 2009-06-17
I've had problems like this after a my computer was turn off improperly (because Visa crashed).  What seems to fix the problem is using check disk in vista.  Its something to try even if your computer wasn't turn off improperly.  
here's a how to: [http://maximumpcguides.com/windows-vista/how-to-use-check-disk-in-windows-vista/](http://maximumpcguides.com/windows-vista/how-to-use-check-disk-in-windows-vista/) 

I hope this helps 
Dan

---

### Post by sciencegirl on 2009-06-18
Hooray! Ubuntu is alive and well again. The checkdisk worked! 

Thank you sooooo much!

---

### Post by metalf8801 on 2009-06-18
> **sciencegirl said:**
> Hooray! Ubuntu is alive and well again. The checkdisk worked! 

Thank you sooooo much!

Thats great I'm happy I could help

---

### Post by sciencegirl on 2009-07-09
I'm back... Same thing happened. Ubuntu crashed and now won't boot. I get the same error message: 

\ubuntu\winboot\wubildr.mbr
0xc000000e

I've run the startup repair from the installation disc for windows (10 times!) and I've run the windows checkdisk 5 times (it takes 4 hours each time... :( ). I've also copied the wubildr.mbr onto every drive. No luck!

Please please help! I have an analysis due next week and I need Ubuntu to run it! 

Many Thanks,
Abby

---

### Post by LewRockwell on 2009-07-09
> **sciencegirl said:**
> I'm back... Same thing happened. Ubuntu crashed and now won't boot. I get the same error message: 

\ubuntu\winboot\wubildr.mbr
0xc000000e

I've run the startup repair from the installation disc for windows (10 times!) and I've run the windows checkdisk 5 times (it takes 4 hours each time... :( ). I've also copied the wubildr.mbr onto every drive. No luck!

Please please help! I have an analysis due next week and I need Ubuntu to run it! 

Many Thanks,
Abby

those unclean dismounts are hell

after you got it up and running last time did you get a good back-up done?

I'd imagine running the fixmbr would get you back to booting windows at least...

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

.

---

### Post by sciencegirl on 2009-07-10
Thanks for the advice! Windows boots up just fine. It's Ubuntu that won't boot! :(

---

