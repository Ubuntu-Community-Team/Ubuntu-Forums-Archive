---
title: "still monitor problem ... how if..?"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by sarium on 2007-05-10
Hi 

I am not an expert on linux /ubuntu and this is my problem:

I want to keep my wireless card ( BCM43 broadcom) in Monitor mode, I am able to set it that way but the card goes back after a little (1-2minutes) to managed mode.

since no one so far  knows  out to solve that I though to write a little routine that run every 60sec or so the instruction

sudo iwconfig eth1 mode monitor  

like if there was someone typing it in the terminal...

is it possible and how could I do that...? ...

thank you


Raf

---

### Post by tturrisi on 2007-05-10
Apparantly you are using the bcm43xx driver and not using ndiswrapper, because ndiswrapper utilizes windows drivers which are incapable of monitor mode to begin with.  That being said, realize that the bcm linux driver is very buggy and monitor mode is unstable in it.  Best to get a card that uses a drive that supports monitor mode well, such as ateros chipsets.  To get an idea of what chipsets best support monitor mode see the Kismet docs here:
[http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)
and see:
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#Broadcom](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#Broadcom)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

---

### Post by jwm0z on 2007-06-06
I am having this problem as well, i'm using the bcm43xx drivers, monitor mode works ok for a few mins and I can pick up beacons in airodump-ng but then the beacons stop coming and monitor mode has reverted to managed.

Anyone any ideas on this?

---

