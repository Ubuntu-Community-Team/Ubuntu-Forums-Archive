---
title: "Intel® PRO/Wireless 3965ABG Network Connection"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by gazzard41 on 2006-09-20
Intel® PRO/Wireless 3965ABG Network Connection on ubuntu 6.06 on dell xps m1710

Ethernet fine no wireless

please help

---

### Post by hurl380 on 2006-09-20
What do you mean. Is your wireless card being detected or you can't connect to a wireless device?

---

### Post by gazzard41 on 2006-09-20
i am a complete beginner whenusing xp my wifi light as static when using ubuntu it flashes like made and i am unable to connect to the internet using wireless

---

### Post by knottyboy on 2006-09-21
I have the same problem, but initially it was working becuase of my wireless connection not being encrypted. Now that I've encrypted it...like you say...my wifi light on the laptop blinks and flutters on and off like mad. I've tried deactivating my wireless card which IS shown in the network list and then activating it again. No help. YES I did type in the correct hexidecimal code into the WEP spot in networking for the wireless. I'm starting to think I need to find an updated linux driver for this card. Seems like the only thing I haven't done yet. But it WAS working before I encrypted in the first place.
Cross fingers. I will try to post the link to the new driver when I find it.
Cheers,
kb

---

### Post by knottyboy on 2006-09-21
OK this is what I was able to track down from the intel pro wireless site...

[Pro Wireless link to search for 3965abg card]("http://mysearch.intel.com/support/default.aspx?q=3965ABG+Network+Connection&id=&lang=eng&hidProductAlias=&as_q=3965ABG+Network+Connection&local-browsebyproduct-searchsupport-submit.x=25&local-browsebyproduct-searchsupport-submit.y=19")

But when you do that search and click on the link you get a linux driver download area that only goes up to 3945abg card. The 1.1.0 card driver is from 7/2006 which is a good thing. I'm just not sure is the difference is so monumental as to be so important. But PLEASE don't take my word for it unless you're willing to take a chance and install it.

I hope this helps a little and solves both our problems.
Cheers,
kb

---

