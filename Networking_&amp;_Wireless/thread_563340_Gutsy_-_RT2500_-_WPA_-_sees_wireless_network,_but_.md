---
title: "Gutsy - RT2500 - WPA - sees wireless network, but freezes PC"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by JakeSpeare on 2007-09-29
I just installed Gutsy Beta on my Averatec 4100.  I had trouble getting wireless working with Feisty so was real pleased to see that Network Manager spotted my wireless network and its strength.  When I try to connect, however, it freezes my PC after a few seconds.  I cannot get out of this freeze and have to do a hard reboot.  I tried to uninstall Network Manager and tried WICD - it does the same.  

I am running a wireless network with WPA.

If anyone has any suggestions on how to get this working, I would be really grateful.

:)

---

### Post by java_java_and_more_java on 2007-09-30
I have a similar problem.

I've upgraded to Gutsy Beta from Feisty. For some unknown reason the system randomly freezes at random times. I'm using a Fujitsu Siemens Amilo L7300 laptop. I suspect it has something to do with the wireless connection which by the way seems to be working better than in Feisty and maybe even better than in Windows XP.

Unfortunately the upgrade failed at the installation step with a message saying my system may no longer be in a usable state, or something similar to that effect. Fortunately I was able to boot into Gutsy and it seems the failed upgrade wasn't fatal after all. It's using the latest version of Gnome and I notice I don't have so many problems connecting wirelessly (at the moment this is my only means of internet connectivity).

-Alex

---

### Post by grovulent on 2007-09-30
yep - same problem here...  

this seems to be a consistent bug - has anyone logged it?

---

### Post by wieman01 on 2007-09-30
I have installed Gutsy BETA two days ago and I had to ditch the rt2500 driver and replace it using "ndiswrapper" (see signature for a tutorial on how to do that). I was hoping that Ralink drivers would now work out of the box but apparently they don't do so yet. 

"ndiswrapper" saved my day.

---

