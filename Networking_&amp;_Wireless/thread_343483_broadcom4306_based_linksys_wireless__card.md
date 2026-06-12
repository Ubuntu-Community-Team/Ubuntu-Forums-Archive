---
title: "broadcom4306 based linksys wireless  card"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by newb2linux on 2007-01-21
hello group,

i am new to linux  and need some help regarding setting up wireless card which is broadcom4306
chipset based by linksys. I am running ubuntu6.1 and have spent considerqable amount of time 
reading posts and how tos. So far no luck.  Ihave tried ndiswrapper and can't get anywhere.
Any help will be appriciated.
Thanks](*,) ](*,)

---

### Post by Metaljaz on 2007-01-21
try this one. If you have a problem post back.

[http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902)

---

### Post by taosaur on 2007-01-21
After days of trying to get my linksys bcm4318 card working, this thread, [http://ubuntuforums.org/showthread.php?t=185174]("http://ubuntuforums.org/showthread.php?t=185174") just got me up and running with the bcm43xx driver.  I'd tried other methods for fw-cutter, but this one worked, and should work for most 43xx cards.  He recommends re-installing ubuntu if you've been messing with ndiswrapper, but I just did a Complete Removal of ndiswrapper-utils at System>Administration>Synaptic Package Manager.  Also, I wasn't able to access my wireless with Network Manager (the program he recommended), so I removed it and installed Wifi Radar, and voila, here I am ):P

---

### Post by Metaljaz on 2007-01-21
good job. glad to hear that.

---

