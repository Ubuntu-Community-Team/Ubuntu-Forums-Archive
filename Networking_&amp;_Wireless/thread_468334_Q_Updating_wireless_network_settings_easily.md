---
title: "Q: Updating wireless network settings easily?"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by derekwp on 2007-06-08
First post :)

After many, many, many days of reading through threads, HOWTOS, wikis, drivers, repos and FAQs I finally managed to conquer wmp54g.  It really was a nightmare to me, most likely because I am a  newbie.  Anyway...

It was necessary for me to change the essid on the router.  After doing so I obviously had to change the essid "hereiam" line in a few files.  Or did I?  I am assuming the line in /etc/network/interfaces needed to be changed which I did.  How about the line in  /etc/Wireless/RT61STA/rt61sta.dat ?

I ask this because once I changed the essid only in both of these files, the network did not start.  Rather I had to 
```
sudo route add default gw 192.168.0.1
```
as it changed as well.  And it now works.

So finally, what would be the appropriate way to successfully update network information for next time?  Thanks for the help.
Derek

---

### Post by crazy_vyper on 2007-06-13
have you isntalled "wifi-radar"? you can use that to "show" ndiswrapper different wireless systems if it can't detect them itself.

should you change the details again, using wifi-radar you can change the connection already present and then ndiswrapper should allow you to just connect like normal, of course asking for the new WEP/WPA etc.. key

---

