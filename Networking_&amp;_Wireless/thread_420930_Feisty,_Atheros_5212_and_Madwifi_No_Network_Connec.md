---
title: "Feisty, Atheros 5212 and Madwifi: No Network Connection"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by ian on 2007-04-24
Hi,
yesterday I decided to upgrade to Feisty from Dapper (by going to Edgy in between). All went fine, except for the wireless not working anymore. I'm using 2.6.20-15-generic, tried the restricted modules, tried to compile the driver myself, but nothing works.
The symptoms: Module loading works perfectly, in dmesg all appropriate messages show up, I have an wifi0 and an ath0 interface. 
But: These interfaces do not connect to my WLAN and they see  no accesspoints.
Google has been not helpful this time, so I ask here. Any ideas someone?

Cheerio, ian

---

### Post by ian on 2007-04-26
Now it works... I reinstalled the kernel using linux-generic and then it worked again. No idea what was wrong before.
Cheerio, ian

---

### Post by ian on 2007-05-07
Ok, I think I found the reason: There seems to be a problem with IRQs on my thinkpad. After I added pci=routeirq to the boot options NetworkManager and WLAN are functioning.

---

