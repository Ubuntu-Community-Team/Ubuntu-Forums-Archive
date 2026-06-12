---
title: "LAN Card does not start on booting, the lights are off."
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by linux32_user on 2008-11-16
After doing a lot of googling, I am having trouble on connecting to the wired internet, the main problem is that my LAN card does not start (or does not power on) (I cannot see the lights at the back of my CPU cabinet and also from router). But in XP, it starts, so please help
I am using ubuntu 8.1. Please help

Edit

My network card's manufacturer is ADMtek AN983 PCI 10/100 Mbps

---

### Post by linux32_user on 2008-11-16
common, reply please and help me out with this bug or problem.

---

### Post by 081105jk on 2008-11-16
Nihilum, [**wow gold**](http://www.oofay.com/)famed Horde guild on Magtheridon EU, will be running a second live, cheap [**wow gold**](http://www.oofay.com/)streaming raid on the Sunwell Plateau this month. Partnering with Xfire, Nihilum is set to provide the entire raid in real-time, cheap [**wow gold**](http://www.oofay.com/)through your browser with the Dyyno plug-in. Choose your favorite class and watch the raid through the eyes and screens of a Warrior, Druid, cheap [**wow gold**](http://www.oofay.com/)or Warlock from the guild. [**world of warcraft gold**](http://www.oofay.com/)(Choose wisely because you can't switch later.)

---

### Post by linux32_user on 2008-11-16
That doesn' help, please reply linuxers

---

### Post by linux32_user on 2008-11-16
ADMtek AN983 PCI 10/100 Mbps

---

### Post by dino99 on 2008-11-16
hi,
i have the same problem or very close to it (see bug report 272247 on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247) )

can you boot ?
look at /var/log 
try dmesg to see if you can identify some reasons about that

good luck

---

### Post by linux32_user on 2008-11-16
According to that bug report, it is about freezing of the system on boot, but my system boots up successfully, but my lan card's power is off, ubuntu cannot start my lan card. So any suggestions?

---

### Post by VanDu on 2008-11-16
See my post here... [[COLOR="Red"]LINK[/COLOR]]("http://ubuntuforums.org/showthread.php?t=983292")
In short, what I did was to go to Win device manager and uninstall the card from device manager and then let it install itself with default win drivers. Be sure that installed drivers are dating year 2001. Boot ubuntu then and see what happens.

---

