---
title: "network quit after restart"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by frenchsquared on 2008-11-19
So, I am a little confused. 
I have a ltsp server that has two network cards
when I run ifconfig both cards have the correct ip address.
The drones can connect to the server but none of the computers have internet connectivity. The all had internet connectivity a few hours ago.

On the server in the top corner of the creen there is normally a green ball(icon) that you can click on to change network setting. It is missing. I am guessing that the missing icon has something to do with the problem.

Any ideas?

---

### Post by frenchsquared on 2008-11-21
This sucks, apparently my questions are getting harder.
So it turns out the problem was caused by an upgrade to ubuntu's new network manager. I removed network manager and installed wicd and everthing works great.

Network Manager didnt know how to use both of my nics. So it just played dumb. Normaly I could right click on the conection I didnt want Network Manager to use, but after the update I lost the power to edit the networks. I might have been able to uninstal Netwrok Manager and reinstal, but I didnt care once I got wicd working. 

Hope this helps someone else.

---

