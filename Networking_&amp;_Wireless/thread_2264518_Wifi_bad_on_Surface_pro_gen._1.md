---
title: "Wifi bad on Surface pro gen. 1"
date: 2015-02-08
forum: Networking &amp; Wireless
---

### Post by Askel on 2015-02-08
Hi 

I installed Ubuntu 14.04 on my  Surface Pro and most of the things work great on it. Not the Wifi though. It connects without problem, but it stops working even though it says it's connected. I have to reconnect it every 2-3 minutes. It doesn't loose connection, it just stops reciving data. 
I've read that this was an issue when the Surface was new, but that the issue had been resolved with newer versions of Ubuntu. I havn't figured out how to solve this though.
The suspend doesn't work either. It starts suspending, shuts down, and then wakes up again right away.

Anyones got any solution to these problems?

//Askel

---

### Post by Askel on 2015-02-09
now the Wired connection stopped working to. It doesn't connect to it at all, even though the connection shows when I press the network icon.

The wireless has gone from bad to worse to. Now it can't even hold the connection but keeps dropping it and keeps reconnecting.

What could I do to fix this?

---

### Post by Knightwise on 2015-02-18
I have found that disabling the power management on the Wifi card increases the stability and the speed of the wifi connection : [http://ubuntuguide.net/speed-up-wireless-ubuntu-1404](http://ubuntuguide.net/speed-up-wireless-ubuntu-1404)
On the other hand : One of the problems you might be having is the fact that your Surface Wifi doesnt play nice with the chipset of your wireless router. I"ve had this issue before where my wifi connection kept dropping after I installed Ubuntu on my Macbook air. Turns out the Wifi chipset in my router caused dropped packages in combination with my Macbook air (running ubuntu) when the wifi router was set to B/G/N instead of B/G . To get around this (I still wanted N wifi) I got a second wifi access point with a different chipset and put that in B/G mode. Evertything worked fine after that.

---

