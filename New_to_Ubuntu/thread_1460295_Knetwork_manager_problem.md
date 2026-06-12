---
title: "Knetwork manager problem"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by vivek40 on 2010-04-22
Hi I have this problem with my KNetworkmanager..I have a wired internet connection and the system automatically detects the connection and connects it (AUto eth0)..but whenever i click on it  in order to manage connections nothing is shown .. there are no wired connections shown....can someone please help.. the snapshots are given here......

[http://twitpic.com/1hkmj9](http://twitpic.com/1hkmj9)
[http://twitpic.com/1hkmpn](http://twitpic.com/1hkmpn)

(Am using Karmic 9.10)

---

### Post by Old *ix Geek on 2010-04-22
> **vivek40 said:**
> Hi I have this problem with my KNetworkmanager..I have a wired internet connection and the system automatically detects the connection and connects it (AUto eth0)..but whenever i click on it  in order to manage connections nothing is shown .. there are no wired connections shown....can someone please help.. the snapshots are given here......

(Am using Karmic 9.10)I'm too lazy to get up and try this, but I'm REASONABLY sure that when I've used a wired connection on my laptop nothing showed up for me either.  But, really, why do you need it?  I mean, what's there to manage? :confused:

---

### Post by SimpleSimonUK on 2011-03-12
Hi,
This problem haunted me for ages, please try the following after you have added a "wired" connection in network manager.

open the file /etc/NetworkManager/nm-system-settings.conf and put the folowing line after "[Main]"

no-auto-default=**:**:**:**:**:**,

you must put the correct mac for your interface where the *'s are (perform command ifconfig and look for HWaddr .......... 

restart and now you don't have de "auto eth0" 

Hope this helps.

---

