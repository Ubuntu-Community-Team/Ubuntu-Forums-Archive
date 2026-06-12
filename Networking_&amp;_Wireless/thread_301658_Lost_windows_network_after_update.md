---
title: "Lost windows network after update"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by somersetsimon on 2006-11-17
After a hard disk failure, I rebuilt my system and installed Dapper . Once I got my wireless network going, I connected to some share on my windows network simply by clicking on connect to server. My windows network was there and I could see everything and make connections. The last thing I did then was to install the updates that were now available.

When I rebooted I couldn't connect to the links I had made earlier. When I went to 'connect to server', nothing appears under 'Windows Network'.

Any clues?

Thanks

Simon

---

### Post by somersetsimon on 2006-11-17
> **somersetsimon said:**
> After a hard disk failure, I rebuilt my system and installed Dapper . Once I got my wireless network going, I connected to some share on my windows network simply by clicking on connect to server. My windows network was there and I could see everything and make connections. The last thing I did then was to install the updates that were now available.

When I rebooted I couldn't connect to the links I had made earlier. When I went to 'connect to server', nothing appears under 'Windows Network'.

Any clues?

Thanks

Simon

I was being a bit slow tonight :-| 

I hadn't done ndiswrapper -m, so my wireless network didn't start up automatically when I booted up. It appears that, for samba to work properly, the network has to be available as soon as you boot up. All sorted now :)

---

