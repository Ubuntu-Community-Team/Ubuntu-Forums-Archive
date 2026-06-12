---
title: "Login Screen on 2nd monitor after 9.10 upgrade - Boot time slower"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by Razmear on 2009-10-30
I finally finished the upgrade to 9.10, only took about 3 hours not including backup time before installing. 
Everything seems to be fine other than some oddities with the new FireFox with 2 exceptions. 
Firstly on boot the white ubuntu logo shows for about 10 seconds before the Nvidea splash screen comes up. This slows boot time as it's apparently happening before the system even starts its boot process. If that were removed then the boot time would be on par with 9.04. Any quick hints before I start hunting up the solution? 

Secondly, and more importantly, the login screen is now appearing on my secondary monitor, which is my TV out. The Nvidia control panel has my CRT as the primary and I run in Twinview mode. The TV is the right monitor and the CRT is the left. Is there a way to get the login screen back to the CRT so I don't have to switch the TV to its SVHS Input when I log into the system? 

And Thirdly, when I upgraded to 9.04 I had to do a tweak to get update manager to act like it did in 8.10. Will I have to do that tweak again or will that setting stick? (just thought of that question while typing this). 

Overall the upgrade was pretty painless. One trick I learned from the last upgrade is to go into update manager and select the best software source before running the upgrade, that way you'll get a server that isn't being hammered. The files only took about 55 minutes to download. 

Well, back to seeing what else is different in this version instead of getting some much needed sleep before work tomorrow. 

eb

---

### Post by Spectre5 on 2009-11-11
> **Razmear said:**
> Secondly, and more importantly, the login screen is now appearing on my secondary monitor, which is my TV out. The Nvidia control panel has my CRT as the primary and I run in Twinview mode. The TV is the right monitor and the CRT is the left. Is there a way to get the login screen back to the CRT so I don't have to switch the TV to its SVHS Input when I log into the system?

Did you find a solution to this?  It is happening to me and it is very annoying.

Thanks,
Scott

---

### Post by malleeblue on 2009-11-11
I too am having the same problem. It seems to be happening because of the position of the mouse. In previous versions of Ubuntu the mouse would always appear in the center of my main screen, and thus the login window would appear on that screen too. In this version (9.10) the mouse, upon bootup, is exactly in the middle of the combined window span. So as a result the login window is appearing on the second monitor; which in my case is on the right side of my main monitor.

I have found that moving the mouse to the left just as the default brown Ubuntu splash screen appears (this is during the bootup sequence) causes the login window to appear on the main monitor (just like in previous versions).

I'd say it's a bug and all that is needed is for the mouse to be told to position itself in the middle of the main monitor, rather than in the middle of the combined monitor span/width.

Hope this helps slightly.

---

### Post by Spectre5 on 2009-11-11
> **malleeblue said:**
> I too am having the same problem. It seems to be happening because of the position of the mouse. In previous versions of Ubuntu the mouse would always appear in the center of my main screen, and thus the login window would appear on that screen too. In this version (9.10) the mouse, upon bootup, is exactly in the middle of the combined window span. So as a result the login window is appearing on the second monitor; which in my case is on the right side of my main monitor.

I have found that moving the mouse to the left just as the default brown Ubuntu splash screen appears (this is during the bootup sequence) causes the login window to appear on the main monitor (just like in previous versions).

I'd say it's a bug and all that is needed is for the mouse to be told to position itself in the middle of the main monitor, rather than in the middle of the combined monitor span/width.

Hope this helps slightly.

Interesting...I'll have to try moving the mouse as you've said to see if that works.  I'm sure this has to do with gdm switching to xsplash.  I heard that you could use nvidia-settings to solve this by selecting your main monitor under "X Server Display Configuration" and then selecting "Make this the primary display for the X screen."  This didn't work for me (I noticed that it did add the following line in the xorg.conf file:
```
Option         "TwinViewXineramaInfoOrder" "DFP-0"
```

EDIT: Interesting, moving the mouse tot he main monitor worked for me to - then it appears as I'd like it to...

---

### Post by Spectre5 on 2009-11-11
Someone has created a patch - hopefully it will make it into an ubuntu update soon
[https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/458027]("https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/458027")

---

