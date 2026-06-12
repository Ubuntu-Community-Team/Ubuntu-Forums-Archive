---
title: "b43 in stead of bcm43xx or ndiswrapper"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by s0ullight on 2008-02-17
hello i got a bcm4311 wireless card
i tryed to use the bcm43xx driver but only was able to retrieve signals from networks 
i couldn't connect
then i used ndiswrapper wich worked perfectly
i would like to thank everybody who figured this out and helped people with this issue
but it doesn't provide things i need like monitor mode
i am interested in b43 and b43 legacy
it should do everything i want the driver to do
only thing is i don't have a clue how to make it work on ubuntu 
i would like to open this post so people can suggest or explain how it would work or works
plz help me...

i know it is much asked after being able to connect etc. XD

btw this is the site of b43
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by spd106 on 2008-02-18
If you want to use b43 then I recommend that you try a Hardy Heron alpha release.

If you feel confident you could perhaps try patching/building your own kernel with b43 support. This isn't very easy unless you know what you are doing. There are some helpful guides in this forum that might help you, but I can't point to any one off hand.

It might also be worth mentioning that Fedora 7 has b43. It didn't work for me a few months ago, but there may have been some improvements since then.

---

### Post by rustybronco on 2008-02-18
or you could try the hardy kernel 
[http://ubuntuforums.org/showthread.php?p=3993033#post3993033](http://ubuntuforums.org/showthread.php?p=3993033#post3993033)
> bcm4311 rev 2 / bcm4312 (needs patches for 2.6.24) hardy kernel

***note*** I upgraded 7.04 to the hardy kernel, but still some things might break.

---

### Post by s0ullight on 2008-02-20
tnx for the link i'm going to try it out right now :D

---

