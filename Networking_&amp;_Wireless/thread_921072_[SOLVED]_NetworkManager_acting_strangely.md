---
title: "[SOLVED] NetworkManager acting strangely"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by tachikomatic on 2008-09-15
I have been running Xubuntu on a Dell D630 for a few months now, and the forum has been invaluable in getting everything setup as I needed. I have come to a dead end, though, because my NetworkManager is acting strangely. It all started when I reset my router to factory defaults, and then changed them back to my normal settings, which include a cloaked network. Ever since I did this, NetworkManager keeps showing "linksys" as my available network connection, which is what I used to connect to the router when I reset it, even though I changed my network name to something else and set it to not broadcast its SSID. Network manager will allow me to manually connect to my access point by manually entering in my network name under "Connect to other wireless network", but about 2 seconds after it gets a successful connection, it drops it. 

I had success with having a connection for the last 3 hours by making the router broadcast its SSID by accessing it through another computer, and then connecting using that SSID through NetworkManager, and then setting the router back to not broadcasting the SSID. It is still a functioning link, but when I mouse over the network manager applet, it says "Wireless network connection to '(unkown)'(61%)". It seems to me that the applet doesnt remember the ssid of my router unless it already has an established connection to work off of, which results in it treating it like it doesn't exist and disconnecting. 

Should I purge and reinstall NetworkManager, and start back from square 1 in terms of what networks it knows? It works fine with other routers, since I used it today for several hours on my university campus with no problem at all. Any help is appreciated!

Update:

Turns out that NetworkManager had the mac for my router in it under both linkys and my custom network name, and that was causing a conflict. Deleted the linksys entry, rebooted and all was happy.

---

