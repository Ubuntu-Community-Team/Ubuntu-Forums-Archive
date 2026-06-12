---
title: "ipw2200 driver packet injection"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by rentacop on 2006-10-30
Hi, i just installed Drapper Drake and i wanted to play around with my wireless network and one of the things i wanted to learn was wireless auditing for security reasons. 

I have aircrack installed and everything works great accept i don't think that i can inject any packets. I did a lot of research for the past few days and i didn't really find anything that helped me at all. I read that i needed to patch my IPW2200 driver but me being new to linux i don't know how to go about doing it.

SPECS: 
Card : Intel Pro Wireless 2200B/G
Driver : IPW2200 ( auto installed when i installed Ubuntu )

 
If anyone could help me, I would be happy!

Thanks - Dave.

---

### Post by ceargle on 2006-10-30
You're going to have trouble injecting packets with that card.  I've got the Intel 2200BG in my Thinkpad, and it's quite a pain.  Injection is possible when you patch the driver, but you will only be able to inject when you are authenticated, so no promiscuous mode injection.  

I have a D-Link DWL-G650 PCMCIA card that I use for all my packet injecting, and it works absolutely awesome with the madwifi drivers.  Might save you some trouble and hair-pulling to the go the route of getting another card.

Hope this helps!!

Bryan

EDIT: Just found this link [http://tinyshell.be/aircrackng/forum/index.php?topic=400.0](http://tinyshell.be/aircrackng/forum/index.php?topic=400.0) from the post here: [http://ubuntuforums.org/showthread.php?t=242556](http://ubuntuforums.org/showthread.php?t=242556)

Also [http://forums.remote-exploit.org](http://forums.remote-exploit.org) usually has some good info and a helpful community when it comes to security and auditing.

---

