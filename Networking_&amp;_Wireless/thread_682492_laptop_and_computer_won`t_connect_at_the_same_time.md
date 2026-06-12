---
title: "laptop and computer won`t connect at the same time"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by nothingspecial on 2008-01-30
Everything was going smoothly on my ubuntu computer but then it died.  My friend said he would fix it if he could but not for a couple of weeks. In the meantime I bought a Sony laptop with windows on it, everything worked fine. He fixed the computer (it was the graphics card). 
 When I plug the ubuntu computer into the internet (it`s a BT home hub) the laptop can`t connect (it`s wireless). If I unplug the ubuntu computer from the home hub the laptop will connect.
 Anyone know what I should do?
 Is it a conflict between ubuntu and windows, the computer and the laptop or do I need to do something to the home hub.
 Thankyou in advance for any help. I am a complete novice by the way.

---

### Post by jeffus_il on 2008-01-30
Check the IP addresses of both machines using ifconfig in a terminal. You may have conflicting addresses.

---

### Post by shad0w_walker on 2008-01-30
Seems as I read to the complete novice bit of your post I will expand on the suggestion from the post above. On your windows machine to find your IP address do this (If its off I apologise, It's rare I use windows and I'm running from memory)

Right click on network places (On your desktop or where ever it may be hiding) and select properties
In the window that opens up after you click, double click on the icon for your network (It should stand out fairly easily)
In the new window it should list the details of your connection including IP.


In Ubuntu. Involves the command line but it's really simple and works regardless of what version you use.

Goto Applications > Accessories > Terminal  to open a terminal.
In the terminal type this command

```
ifconfig | grep "inet addr:"
```

If in doubt of the command just copy and paste it into the command line and if in doubt about which is your IP then just copy the output into a message and post it in the thread and we can help you out.

Good luck. :)

---

### Post by nothingspecial on 2008-01-30
Are they supposed to be the same?

---

### Post by shad0w_walker on 2008-01-30
No. They should have different IPs otherwise they will conflict and the router won't know which system to send data to.

---

### Post by nothingspecial on 2008-01-30
Ok. Thanks. I,ll try it when I get home and then come back here.

---

### Post by shad0w_walker on 2008-01-30
Ok, if they have the same IP just need to change it (only the digits after the final .) and it should work fine. If you need any help just ask. 

Good luck. :)

---

### Post by nothingspecial on 2008-01-30
Thanks for your help !

---

