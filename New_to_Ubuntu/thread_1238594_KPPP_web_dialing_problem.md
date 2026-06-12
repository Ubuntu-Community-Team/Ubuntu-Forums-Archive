---
title: "KPPP web dialing problem"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by parvati on 2009-08-12
Having trouble getting KPPP, Kubuntu web dialing tool, to work and getting Konqueror to open webpages. In the process of getting internet connectivity through KPPP.... it now only returns error message 19. At one point, thought it was configured properly bc no more error messages, it was in the toolbar as though launched, and the connection clock was running. After adding my username to various groups, including root, it will now only give error message 19. Network Copnnections indicates a New Wireless Connection but under Last Used says Never. I never did get Konqueror to open webpages, tried maybe 5 times.
 
XP/Kubuntu dual boot
Ubuntu 9.04 Jaunty kernel 2.6.28-14 generic
Internet: Tethering Verizon LG cellphone to laptop
Using Kubuntu since 8-10-09
 
Getting this readout and others like it:
 
Aug11 14.47.15 ubuntu pppd [1431]: pppd 2.4.5 started by root, uid 0
Aug11 14.47.15 ubuntu pppd [1431]: Using interface ppp0
Aug11 14.47.15 ubuntu pppd [1431]: Connect: ppp0 <-> /dev/ttyUSB0
Aug11 14.47.18 ubuntu pppd [1431]: PAP authentication failed
Aug11 14.47.18 ubuntu pppd [1431]: Connection terminated.
Aug11 14.47.18 ubuntu pppd [1431]: Exit.
 
 
The KPPP log gave me this, which could be the problem: 
/root/.kde/share/apps/kppp/kppp/pid
When attempted to move it, was told: No such file or directory.
 
Also tried "noauth" under arguments and that didn't work but maybe I did something wrong.

---

