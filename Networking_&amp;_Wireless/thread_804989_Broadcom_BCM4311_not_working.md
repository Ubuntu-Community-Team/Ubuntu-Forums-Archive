---
title: "Broadcom BCM4311 not working"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by -Morgoth- on 2008-05-23
I have a Acer Laptop with a freshly-intalled Ubuntu 8.04. My wireless card is "Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)" 
Problem is that i cant get this card to work. I've tried ndiswrapper but im not sure if i got it right. When i click on "Windows Wireless Drivers"  in the menu, it says this under "currently installed windows drivers:" bcmwl5 - hardware present: yes
When using Wifi Radar my network is found and i can connect to it, but its not properly  connected as i cant online. Nothing about wireless LAN appears in the notification area. Only the wired connection shows up there.
So apparently the computer knows the card is there... but it wont connect me to the internet. Any help on this?


btw, i've had this card working in feisty but i cant remember how i got it working... :/

---

### Post by Ayuthia on 2008-05-23
What you can try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
```
If that works, then you will need to add the following:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS' | sudo tee -a /etc/modprobe.d/ndiswrapper
```
This comes from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-6a90c0182f807f29d1a2f55e8654ac07689542bb](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-6a90c0182f807f29d1a2f55e8654ac07689542bb)

Hope that helps.

By the way, this is a new step.  The native Linux Broadcom drivers changed so this step had to be added.

---

### Post by Steve413z on 2008-05-23
if you don't want to use ndiswrapper try this:
[http://ubuntuforums.org/showthread.php?t=803986](http://ubuntuforums.org/showthread.php?t=803986)

---

### Post by Ayuthia on 2008-05-23
> **Steve413z said:**
> if you don't want to use ndiswrapper try this:
[http://ubuntuforums.org/showthread.php?t=803986](http://ubuntuforums.org/showthread.php?t=803986)

Just to add some comments to Steve413z, this card (4311 rev 01) does not work as well with the bcm43xx driver.  The b43 driver works better.  As for the difference in ndiswrapper and b43, there is not too much.  Some days ndiswrapper works a little better and some days it is b43.

---

### Post by Steve413z on 2008-05-23
> **Ayuthia said:**
> Just to add some comments to Steve413z, this card (4311 rev 01) does not work as well with the bcm43xx driver.  The b43 driver works better.  As for the difference in ndiswrapper and b43, there is not too much.  Some days ndiswrapper works a little better and some days it is b43.


broadcom is annoying,  I almost recommend buying a new wireless card for $30 and install it, it's not hard on most laptops, usually there is a panel you take off the bottom, it's almost as easy as adding more ram.

---

### Post by meborc on 2008-05-24
there is a good chance this will work - [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

;)

---

### Post by -Morgoth- on 2008-05-25
I went through that guide but it didn't work :(
Its just like it was before i did all that stuff in the walkthrough

---

### Post by -Morgoth- on 2008-05-25
It's up and running now :) Thanks for the help

---

### Post by TommyIndep on 2008-08-03
> **-Morgoth- said:**
> It's up and running now :) Thanks for the help

Can you please tell us what guide you used? :)

I'm on my Acer TravelMate 5520 and I have the same problem as you, everything worked in Gutsy after following a guide, but not in Hardy, so I'm on Gutsy now and I'd like to get back on Hardy!

---

