---
title: "Network Manager"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by Andy06 on 2009-05-29
Hi is there anything better than network manager to manage connectivity and networks? I know every part of ubuntu is so modular, there are probably loads but which one is good?

I find Network Manager too basic and I'd love to have a Vista style notification when you are connected to a local network but not the internet (the globe in vista disappears to signify a problem with an internet connection or router/IP/DNS settings). 

In ubuntu it doesn't notify you in a simple way when your router has lost its internet connection (but you are still connected to LAN)

Thanks a lot

---

### Post by nothingspecial on 2009-06-01
Try wicd. Don`t know how it compares to the vista one but it works well for me.

---

### Post by imdano on 2009-06-01
You're welcome to try wicd, but it doesn't have the "limited connectivity" notification you miss from Vista.

---

### Post by Andy06 on 2009-06-01
Is there any way then to find out? How do you guys figure tghe problem out when ubuntu tells you that you are connected but you find 404s everytime you access anything. I don't quite remember how I did this in XP either.

The problem is in places that I frequently access the internet from, the routers frequently have DNS issues, DHCP issues or at times simply require a restart, in each instance, vista notifies that there is some problem but ubuntu says everything is perfect, so if there is some way to remedy that, I'd be very very grateful.

---

### Post by arubislander on 2009-06-01
Wouldn't the fact that the connection to the router is fine but there is no internet connectivity be a clear enough clue?

---

### Post by steeleyuk on 2009-06-01
I think UPnP is used to detect whether the internet connection is up. I vaguely remember reading that some work was being done on the Epiphany Web Browser to show the internet connection status.

---

### Post by Andy06 on 2009-06-02
> Wouldn't the fact that the connection to the router is fine but there is no internet connectivity be a clear enough clue? 

Yes bit it helps to know the issue too. I might draw some flak here but I find Vista's repair tool quite efficient. In my setup, it detects when the issue needs to be repaired by resetting the LAN adapter, refreshing DNS cache or is related to DHCP. The Ubuntu network manager does not advise me on these things.

Besides, sites can show as not found even when the server is down, loaded or sometimes just randomly. A quick look at the icon in vista tells me if the connection in fine but in Ubuntu, I will have to open another tab and check if other sites are up.

Now it gets even more complicated with wireless. Vista shows you a nice map to see where you have conked out with both the statuses for your computer to router and router to internet connection, Ubuntu doesn't. So its a bit of guesswork if you've lost internet connectivity or the signal to the router itself especially if you are on a direct LAN backbone or WAN.

I'm no expert at the new connection technologies, so I find it quite helpful. Anything with more features would do to be honest.

---

### Post by bodhi.zazen on 2009-06-02
> **Andy06 said:**
> Yes bit it helps to know the issue too. I might draw some flak here but I find Vista's repair tool quite efficient. In my setup, it detects when the issue needs to be repaired by resetting the LAN adapter, refreshing DNS cache or is related to DHCP. The Ubuntu network manager does not advise me on these things.

Besides, sites can show as not found even when the server is down, loaded or sometimes just randomly. A quick look at the icon in vista tells me if the connection in fine but in Ubuntu, I will have to open another tab and check if other sites are up.

Now it gets even more complicated with wireless. Vista shows you a nice map to see where you have conked out with both the statuses for your computer to router and router to internet connection, Ubuntu doesn't. So its a bit of guesswork if you've lost internet connectivity or the signal to the router itself especially if you are on a direct LAN backbone or WAN.

I'm no expert at the new connection technologies, so I find it quite helpful. Anything with more features would do to be honest.

In linux networks do not need to be "repaired", just configured.

Network manager or wicd, both are nice tools.

---

### Post by Andy06 on 2009-06-03
Well unfortunately for me, the network does break down in many places every now and then. Does so for everyone around me as well. It is configured properly. So what do I do then? When I was in vista and for the people still on it, its not that great a problem (couple of clicks soln), but it is for me since I have to start all the troubleshooting steps one by one and check every step of the connection.

---

