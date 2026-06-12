---
title: "Searched 2 days for answers to my resolution problem NVIDIA GeForce 6150"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by darkchest on 2009-11-05
Hello all,

Please could someone help me fix my screens resolution problem. I have searched for a solution and no one seems to work. I started having this problem after doing a clean install of ubuntu 9.10. My resolution stops at 640 x 480 50hz. Everything is soo big.

I have been searching for solutions to add resolution to my display settings. I can not. I have installed all the NVIDIA cards offered by Ubuntu Software Center - still no help. I even got the flickering command prompt tty1 trying to fix my problem and I had to fix that.

Im just trying to get a solution if there is any. Tell me what to do and i will do it

---

### Post by darkchest on 2009-11-05
I just found out that my professor asked me to come to school, so I will be gone from the computer for about 3 hours. Please you can leave your messages.

PS: i tried xrandr, editing xorg, nvidia installations, envyNG, ftp: download.nvidia.com. None of this helped

---

### Post by Marlonsm on 2009-11-05
Something like that is usually a driver issue.

You have alreaded instlled the drivers in the software center, but how about in the driver installer?
Open System > Administration > Hardware drivers, and enable the latest one.

---

### Post by timjohn7 on 2009-11-05
What monitor do you have?  I have a nVidia 6100 Graphics card and just enabled the nVidia driver recommended under Hardware Drivers as specified in the previous post (version 185).
What was interesting in my situation was that I had an extension VGA cable between my Samsung monitor and VGA port.  I also only had low resolution until I connected the monitor directly to the box (removing the extension cable).  Once connected directly, Karmic immediately recognized the card/monitor combination and I had full resolution range selectable.

---

### Post by cariboo on 2009-11-05
Open an Applications-->Accessories-->Terminal and type:

```
sudo nvidia-xconfig
```

then restart, that should solve your resolution problems.

---

### Post by darkchest on 2009-11-06
I tried all that you have asked. i activated the nvidia driver 185, i did the "sudo nvidia-xconfig" and restarted. I still see dont see higher screen resolutions.

PS: I have a View Sonic, ViewPanel VG150.

---

### Post by darkchest on 2009-11-06
Is there a way out, or am I forced to downgrade the OS

---

### Post by darkchest on 2009-11-08
Something funny happened. I was on the ubuntu IRC, someone was helping me go decipher what was wrong. I mistakenly deleted the contents of xorg.conf and restarted. Then i got the different resolutions needed.

I tried all resolutions but anything higher than 800x600 either looked funny or the monitor said it was out of range.

Is that the monitors fault or is it ubuntu's fault bcos my Windows XP has its display resolution on 1024 by 768.

---

### Post by drewchapman on 2009-11-08
It's been a while for me, but I used to have that same video card and to get up to my native resolution I had to add it into a specific file before it was selectable.

Alas, I have no idea what file that was now. But if that sounds like the right answer to someone who knows what they are talking about, they might know which file it was that I am talking about.

---

