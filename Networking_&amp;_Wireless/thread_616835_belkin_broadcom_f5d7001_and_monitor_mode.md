---
title: "belkin broadcom f5d7001 and monitor mode"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by CrinkElite on 2007-11-18
I've got a belkin wireless desktop card and i am unable to put it into monitor mode

magnum@magnum-desktop:~$ iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Operation not permitted.
magnum@magnum-desktop:~$ 

i used the solution in the sticky in this forum that automatically sets up ndiswrapper with the correct windows driver (excellent solution for broadcom card users by the way)

I can't seem to get the card into monitor mode and i think this is because of the ndiswrapper/windows driver (please correct me if I'm wrong about this)
I have also read that that there is a bcm43XX driver that works with the card also, would this driver allow me to access monitor mode. or is there any way to force it into monitor mode. i'm new to ubuntu so thanks for any info you can pass on.

---

### Post by CrinkElite on 2007-11-19
sorry I've got it the wrong way round I'm using the bcm43XX driver but I'm pretty sure ndiswrapper doesn't work with RFMON. If anyone has managed to get this card into monitor mode I'd really like to hear about it. I can't afford a new card unless It's absolutely necessary

---

