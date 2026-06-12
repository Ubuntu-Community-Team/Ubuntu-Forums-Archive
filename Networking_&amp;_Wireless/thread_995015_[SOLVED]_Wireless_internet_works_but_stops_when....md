---
title: "[SOLVED] Wireless internet works but stops when..."
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by magical_graam on 2008-11-27
...I either try to install updates with apt-get, or just after a couple of hours of use. I only noticed this problem a while after [[COLOR="Blue"]this problem[/COLOR]]("http://ubuntuforums.org/showthread.php?t=986398"), where my wireless network sometimes fails to connect and asks for the password again, but it shows hex in the password box. I'm still having that problem (btw thanks for all the help :p), but this one is more important. 

What happens is once I (eventually) connect, if I try to download the updates, through synaptic, the icon on the panel or even apt-get in the command line, it downloads for about 2 secs then stops. Completely. Try to use firefox, but no webpages load. Network manager says I'm  still connected though. I have to restart the network (well, right click the panel icon, disable networking then enable it again).

I am using a BCM4312 wireless card and an ndiswrapper driver. However, I don't think anything is wrong with them, since they worked fine in 8.04.

Help please!

---

### Post by magical_graam on 2008-11-27
Right, I've got wicd to work, so I'm alright. However, I did find a lot of people who had the same problems as me, so I think that the network manager might have gained a few unwanted 'features' from its recent upgrade to intrepid.

---

