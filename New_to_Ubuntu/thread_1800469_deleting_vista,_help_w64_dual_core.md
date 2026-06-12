---
title: "deleting vista, help w/64 dual core"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by YellowBronco on 2011-07-09
iv had enough, going full tilt ubuntu, any sugestions before i click the final button, i have a full backup, not that i will go back, if anything i might load xp, not sure, i do have a problem with the linux_frequency_driver, aparently microsoft made a bo bo and put a general fix on my amd athlon 64 x2 dual core processor and made it a single core in the updates, i cant find an easy fix for it, i did the amd bio update and i dont think it fixed it. I cant figure out what powersaved 0.8.19 , cpuspeed 1.20.1 and cpufreq 1.20 do to help me fix it, or how to decipher the way its supposed to be done, please help,   dan

---

### Post by OldBoy44 on 2011-07-09
Before going to Unity - run following in a terminal to check your computer is compatible -

usr/lib/nux/unity_support_test -p     :)

It probably will be O.K.

---

### Post by Wim Sturkenboom on 2011-07-09
Are you saying that even in Ubuntu your processor is currently identified as a single core?

---

### Post by YellowBronco on 2011-07-09
what is unity and how do i run it,?
im not sure how to check it in ubuntu, everytime i start i start ubuntu i have to start it from nothing, like i was never on it before????   
im waiting for 2 backups to finish deleting off my external drive,
 one says 55g deleting and it has been at 5 seconds for an hour,

---

### Post by YellowBronco on 2011-07-09
o yea, ubunu said it will del all drives, is that the documents folder also?

---

### Post by OldBoy44 on 2011-07-09
To be honest YellowBronco, I am not sure what it is that you are doing. A wiser head than mine hopefully will be able to help you! 
I would suggest that you open another thread called something like "Help Wanted To Download Ubuntu". There is plenty of documentation that I think you should read. Others have ready access to these guides - I do not.
The most stable version of Ubuntu at present is 10.04 which is supported to April, 2013. This may be the best version for you. Sorry I can't be of greater assistance - If you feel inclined, post here to let me know if you have followed my suggestions. In the new thread include all details of your computer specs and mention the problems you have been having. My reference to Unity was because of my mistaken belief that you would be wanting to download the latest version of Ubuntu, 11.04 Natty Unity. I don't believe now that this would be the best choice for you. I trust my suggestions will be helpful to you.

All the best,  :)

---

### Post by YellowBronco on 2011-07-09
[http://ubuntuforums.org/showthread.php?t=594827](http://ubuntuforums.org/showthread.php?t=594827)
sorry this is the reference, but i cant find the one that described how to build the powersaver 0.8.19, cpuspeed-1.20.1 and cpufreq-1.20 ver 2.6.10, they are listed in the download at the amd site, but it is a broken link, and i found that someone on here built one out of code , but i cant find it now,,,,,

---

### Post by OldBoy44 on 2011-07-09
Hi YellowBronco,

See my comments in post 6 - I think I have led you astray, please accept my apology!

aussiebean  :p

---

### Post by YellowBronco on 2011-07-09
u aussy guys are great, always awake when i am in the mid of the night,, im going to load the newest 64 bit linux version , my drives are cleaned of all but microsoft vista,, yuk,yuk, took a while with 2t , then i had to take the motherboard out to get to the s/n on the BACK side of it,,, im putting it together now and i can log back into msi and get the new bios that are keeping the ssd drive from running, , the question still is 
do i have to apply some type of other bios for the amd 64 x2 prossesor, and why do i have to keep installing ubunto, ?

specs:


os vista ultimate ver 6.0.6002sp2
ubuntu on and off
amd athlon 64x2 dual core pro 5000+ 2.59 gh
bios american megatrends v1.6
smbios 2.5
power thermaltake tr2-500pp psf450s
6 g ram crucial
nvidia gforce 7900 gt/gto grapics w/ dual 22 monitors
memorex 16x double layer 5395 cd-r/rw drive
sony optiarc dvd rw ad-7190s ata 1.02
a dr zid citizen tuv
hd c crucial ssd 64g
hd e western digital 1600aajs 160g
hd f western digital 2500jb 250g
hd g seagate st340810a 40g 
external hd western digital 10000hiu-00 1T
external hd western digital 3200aajb 320g

---

### Post by grahammechanical on 2011-07-09
Hi YellowBronco

I think that something is being lost in translation. I do not clearly understand what the problem is. I did find this link

[http://powersave.sourceforge.net/powersave/index.html](http://powersave.sourceforge.net/powersave/index.html)

Not that I understand what it is saying either. How did you install  Ubuntu? Was it through Windows using Wubi? Perhaps you are running a  Live session from a Live CD. This allows you to see if Ubuntu will work  on your machine and also to allow you to become familiar with the OS.

If you are running a Live session open system monitor and look at the  System tab and then the Resources tab. This will tell you if Ubuntu is  seeing your machine as having two CPUs. This would be a good start.

The Windows operating system that you have might not be able to use two  CPUs. So it runs it as one CPU. Programs have to be coded to take  advantage of having more than one CPU core. On my machine the processes  are continually being switched from one CPU to the other and back again.

Unity is the new user interface for Ubuntu. You can see what it looks  like from the Ubuntu home page. It makes use of the 3D capabilities of  video cards that have 3D capabilities. The standard video drivers that  come with Ubuntu do not have at present the ability to make full use of  some video cards. We need to install a proprietary driver. For this  reason a Live session will not necessarily show you the Unity interface.

During the install to hard disk you will be told that you do not have  the hardware to support Unity. That may or may not be true. After  installation open Additional Drivers and activate the recommended video  driver. You will see a message that the driver is activated but not in  use. Do not believe this message. It is in use. Reboot and at the log in  screen click on your user name and look at the bottom panel. On the  right will be a menu list that should say Ubuntu. This is Unity. Click  on it and see if you like the look.

If you do not like the look you can select Ubuntu Classic from the same menu at log in time.

I hope that this helps you in some way.

Regards

---

### Post by YellowBronco on 2011-07-09
wow, lots of info , thank u , i was just going to get the s/n off the back of the motherboard , but i got to cleaning and dusting and making some mods,, well ill get to the install, from what ive been reading the 2x core amd that i have is a version that they made to coserve power for the eviormentaly consious, but now they have taken the support away , downloads , for it and it only runs in slow speed, i thought that it was my low gig ram, but i just updated it and now found this power to the cpu problem, .
the system becomes sluggish or non responsive durring quick file grabbing, locks, and i have to reset, and startup takes 5 min ore more, otherthen that it works great for my first build,,, thanks for the help, dan

---

### Post by YellowBronco on 2011-07-22
well, its been almost 2 wks and im finaly to where i can reinstall   11.04, it was my own stupidity, i put a version 6 on top of 11.04. i   thought it was just info from the library , not a whole new install.   like i said^ i like ubuntu, ive been too enamored in the bill gates   world to fully get it all of ubuntu yet, i guess if u are starting out   fresh with it it is easier then having to relearn things 
alot of my problem is i think i know how it works, well it only works that way in windows,, lol
there is probably alot of ways to do this but i nuked the disks all hds ,   re-installed a new os , xp not the vista stuff, had to re-find all   drivers this way and reinstall from bios, in order to do that i had to   take the motherboard out and find the codes on the back side of it
please dont anyone else do what i did
dan

---

