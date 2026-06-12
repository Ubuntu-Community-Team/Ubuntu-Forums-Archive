---
title: "X Post: Need some help with my Wi-Fi connection"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by kona0197 on 2006-09-07
From the Kubuntu Forum:

Hi guys. I love Kubuntu so please keep up the good work. However I do have a problem with my Wi-Fi card. Yes Kubuntu detects it and can use it but every once in awhile it seems Kubuntu will stop detecting or stop using the Wi-Fi card and tell me via the Wireless Assistant app that the card is not turned on when I know it is so I end up losing my connection and have to boot into Windows to talk to people in the forums I visit.

Now I have no idea how to fix this. My Wi-Fi card is an Atheros AR5005G card. I am running Drapper with an 1.6 Ghz Celly and 512 megs of DDR2 RAM. Thanks guys.

---

### Post by kona0197 on 2006-09-08
Bump - if anyone can help thank you.

---

### Post by dannyboy79 on 2006-09-08
this happened to me as well, i have a netgear which has the ar5212 chipset I believe which is suppose to work out of the box with dapper drake, ubuntu. I posted a thread asking for help and someone suggested that I should go to a terminal and type in 
sudo ifdown eth0
and then
sudo ifup eth0  
Now make sure that you enter whatever interface yours is, for example mine is ath0, not eth0, so if yours is like mine, go to a terminal and type in 
sudo ifdown ath0
then
sudo ifup ath0
That should enable your internet access again.
This is the website that explains it.
[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430) 
Now that still left the question, why is my internet connection being dropped? I couldn't figure it out for the life of me. Then after a few days, maybe a sudo aptitude dist-upgrade or 2 I noticed that my internet connection wasn't being dropped anymore and my network card has it's 2 little flashing lights going non-stop. So I am not sure what eventually caused the fix of my network card not working every so often but I am happy it's fixed is all I can say! Let me know if that helped you. If not check this site out, [https://launchpad.net/distros/ubuntu/+source/udev/+bug/46048](https://launchpad.net/distros/ubuntu/+source/udev/+bug/46048) 
I didn't have to do this but it looks like a solution if your problem doesn't automatically fix itself like mine did. Oh, I am running Xubuntu, maybe that's a difference than what you are running. Good luck and don't forget to let me know if any of this has helped.

---

