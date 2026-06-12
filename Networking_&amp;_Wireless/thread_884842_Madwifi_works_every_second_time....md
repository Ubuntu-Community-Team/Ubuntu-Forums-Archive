---
title: "Madwifi works every second time...?"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by theirishfozz on 2008-08-09
Hi

I had a lot of trouble getting wireless to work. I had to disable ACPI in order to get any kind of cooling working and possibly because ofthis I cant turn my wireless card on or off in linux. gah. Then I tried for ages to get ndiswrapper or madwifi working and eventually got madwifi working after ndiswrapper froze when modprobing. ugh. 

So madwifi works! Fantastic..the only problem is that it only works every second time I boot up. I'll boot up and I have the module automatically load..and it connects to my wireless network no problem. Then I restart and the module has been loaded but no wireless interfaces are created. Then I'll restart again and it work perfectly. I tried unloading the ath modules before restarting when it worked to see if perhaps it wasnt shutting down properly but that didnt work. Im not an uber linux user so Im out of ideas. Does anyone know what the problem might be?

I have a similar problem on windows...sometimes when I boot up it detects my wireless card but cant use it for some reason but thats less frequent (maybe 1 in 20 boot ups, not 1 in 2).

Im using Hardy and my wireless card is a Atheros 5007.

thanks

EDIT: Just did a quick test, its def based on boot up. I removed the module and re-loaded it a few times and it worked fine. Next time I restart I'll do the same and it wont work at all.

---

