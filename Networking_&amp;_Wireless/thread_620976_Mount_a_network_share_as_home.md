---
title: "Mount a network share as /home"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by quinnten83 on 2007-11-23
Hi, 
I actually posted to [this thread]("http://http://ubuntuforums.org/showthread.php?t=232100"), but I believe it is in the wrong subforum, so I will ask the question here again.
In a windows office users have the use of a roaming profile. Their settings follow them, no matter which windows computer you log in.
The user settings are stored on a network folder
 I was wondering if it is possible to mimic this behaviour by mounting a network share as /home.
I would need to have a script that runs at startup, probably as root that will check which user is loggin in and then automount their network share as home with all their settings.
Also, for laptop users it would be necesarry to have a script that will check if the network share is connected and if it is not, use the local /home/$user folder. Also it needs to check if the user is on a computer different than his laptop. because in that case a synchronisation of the network /home is not desirable. 
I think that the scripting could be overcome with the help of an expert (which by no means I am not), but is the mounting possible?

---

