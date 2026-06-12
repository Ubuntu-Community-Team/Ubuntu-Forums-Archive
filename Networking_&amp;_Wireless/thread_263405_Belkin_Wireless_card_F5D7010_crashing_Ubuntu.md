---
title: "Belkin Wireless card F5D7010 crashing Ubuntu?"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by FireFusion on 2006-09-23
I recently got a Belkin Wireless G Notebook Network Card (F5D7010). I was very pleased to find Ubuntu found it straight away and I was on the net in seconds (connected via ra0). However once I restarted my laptop and tried to boot in to Ubuntu it crashed. 

I took out the card and it booted fine. I then plugged in the card before logging in and it crashed. I restarted, logged in then plugged in the card and it would no longer let me get to the networking options. 

Has this happened to anyone else? How did you fix it?

Thanks.

---

### Post by profaner on 2006-10-29
I'm having the same problem with this card (F5D7010 v6000). The weird thing is that I once made it to work with the driver "rt61.inf" that comes in the CD. I checked it with "ndiswrapper -l" and it said "rt61 driver present, hardware present". Then I saw that the signal strength was 100%, but when I tried to load any webpage in Mozilla nothing happened. I configured the wireless connection, inserted the WEP key and all that stuff, and still nothing. Then I rebooted my laptop and in the loading process "Identifying Network Interface" Ubuntu crashed.

Now I'm trying with different drivers, but the same thing happens when I plug my card in while in Ubuntu; Ubuntu crashes and when I remove it Ubuntu comes to life again, but the terminal stops working and I can't open another one because it won't start, so I have to reboot.

---

