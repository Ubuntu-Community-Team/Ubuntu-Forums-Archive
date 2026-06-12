---
title: "p4_clockmod and wireless problems"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by digitalbenji on 2007-05-30
Hi,
   I have a Pentium M Celeron 410 1.46GHz .  By using insmod p4_clockmod I have been able to get cpu frequency scaling working.  However, I notice that sometimes the network connection goes down (and won't come back up).  This has only started happening since I started using p4_clockmod.  Does anyone know anything about this?
   My thoughts are that if the CPU scales down really low, then the network keepalive processes don't have time  to do what they need to stay active.  By default, the scaling will go as low as ~183mhz, which is really slow.  When I had it set to dip down this low, the network drop seemed to be happening much more frequently.  I had changed the minimum to be ~700mhz, but I just had the network drop at that speed for the first time.  Now I have it set to scale between 1.1 and 1.4 ghz.  Does anyone know anything about this?  Is there maybe a setting I'm missing?
   I also have both powernowd and cpufreq-utils installed.  Is it mistake to be using both of these?  cpufreq-utils is more configurable I think, but powernowd seems to be needed so that my laptop can hibernate and suspend properly.
   Also, the reason I'm using scaling is because I have a laptop and I'm interested in saving any power I can. 

Thoughts, comments, ideas appreciated.

Thanks

---

### Post by digitalbenji on 2007-05-31
bump in the night

---

### Post by digitalbenji on 2007-06-01
bump

---

### Post by digitalbenji on 2007-06-01
bump

---

### Post by inportb on 2007-06-19
Well, I can report the same problem. It's been this way for a while, and I've disabled scaling, resulting in a red-hot laptop. I tried it again today, and, as expected, the network died after a while. It's both wired and wireless for me.

my post -- [http://ubuntuforums.org/showthread.php?p=2497135](http://ubuntuforums.org/showthread.php?p=2497135)

---

