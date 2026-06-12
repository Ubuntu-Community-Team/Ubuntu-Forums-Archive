---
title: "intel 3945 recognized but not working"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by isiahil on 2007-06-13
I have the intel pro/wireless 3945 wireless network card. I have been searching through the forums for old threads about my wireless card and I have read basically all of them. I been having this problem for a while. First off I noticed since I installed the linux restricted drivers for my wireless card the led light for it has stopped blinking all together. So today I disabled it(linux restricted drivers) and rebooted so that the system is not using it. I then did a lsmod and noticed that the ipw3945 is loaded but when in the "used by column" it has a 0. I then put in my Ubuntu live cd to compare results and when using the live cd when i do a lsmod the ipw3945 module is loaded and it says 1 in the "used by" column and runnig iwconfig allows me to set up the card. And i have ran alot of commands from all the old threads I read and I know that the wireless card is recognized by Ubuntu and its NOT disabled or the kill switch is not activated. And iwconfig doesnt have a eth with wireless extensions. ifconfig is only showing me my wired connection and my loopback connection. 

SUMMARY: Its like my drivers are loaded and my card is recognized but Ubuntu is not using my drivers to control the card. Is there anyway to do this manually?

---

### Post by isiahil on 2007-06-13
OK nevermind, I went the ndiswrapper route a got it done.

---

### Post by Glennjamin on 2007-06-13
i have a simular problem with the same card-

it recognises the network and card but shows no signal strenght and the status is disconnected- any ideas?

---

