---
title: "wireless network not picke up on boot"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by kditty on 2006-11-07
i recently switched from a wired connection, to my old wireless, and now when i boot, my wireless doesnt load automaticaly. what do i need to edit for my computer to load ath0 as the default networking device? 

in sys>admin>networking i selected use ath0 as default device, but it still doesnt load. thanks.

kyle

---

### Post by nickmcg on 2006-11-07
I had a similar problem and found that tere was no 'auto rausb0' in  /etc/network/interfaces

In your case it will be 'auto ath0'

HTH

Nick

---

