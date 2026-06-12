---
title: "[SOLVED] reinstalled networking manager - no wireless in list"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by jonathanmotes on 2007-10-12
A few days ago I installed Wicd, but I was having an [issue with it]("http://ubuntuforums.org/showthread.php?t=572671"). I decided to try to reinstall network-manager, but now I can't see my wireless networks from the icon in the notification area. I have to go to "Network Settings" and create a manual connection to connect to my wireless. I had the exact same problems after reinstalling network-manager on another laptop a few months ago, so I don't think it is something with my computer. Please help!

---

### Post by kevdog on 2007-10-12
Did you select enable roaming??

---

### Post by jonathanmotes on 2007-10-12
Roaming was enabled after installing. But, I just changed it back to roaming and now it shows them! Thanks! The only problem now is, I'm not connected to the wireless even though the network manager shows that I am!

---

### Post by jonathanmotes on 2007-10-12
Never mind, I got it to work by uncommenting some things in the networking interfaces file and restarting the network!

---

### Post by kevdog on 2007-10-12
See the link in my signature to confirm you can connect manually idependent of network manager.  If you can, then its obviously a network manager issue.

---

### Post by jonathanmotes on 2007-10-12
> See the link in my signature to confirm you can connect manually idependent of network manager. If you can, then its obviously a network manager issue.

OK. I am still having problems connecting to a secure network (unlike before with network-manager), so I will use your method.

Thanks

---

