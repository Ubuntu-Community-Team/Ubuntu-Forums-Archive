---
title: "Wireless problem"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by I WILL DO IT on 2009-09-14
idk if this is the right place to post

ok so i have this old gateway laptop i install ubuntu on ect ect and i cant get none of my wireless cards to work.... idk what to do i went in to the new hard ware manger ect ect but it says that there nuthing new in the system even and i have the both of wireless cards in my system
(note: one is a usd)

what should i do?

---

### Post by nothingspecial on 2009-09-14
Post your wireless info

open a terminal and type

```
sudo lshw -C network
```

Then copy and paste the output here.

---

### Post by talsemgeest on 2009-09-14
Please don't forget to use a descriptive topic title, just about everyone in this forums has a problem ;)

---

### Post by I WILL DO IT on 2009-09-14
i cannt copy and past it, this lap top does not have internet


but when i typed that it sed it was in there 

and the network its under says its unclaimed

---

### Post by Perfect Storm on 2009-09-14
Do you have the possibilities to wired your laptop meanwhile?


Edit: title changed.

---

### Post by I WILL DO IT on 2009-09-14
yea butt the ethernet controller does not work.... same thing with the wireless....

---

### Post by nothingspecial on 2009-09-14
But you still need to post your wireless network info so someone can help

---

### Post by I WILL DO IT on 2009-09-14
omg i guess i need to tye it all....

*-network unclamied
description: ethernet controller
product: agn100 802.11 a/b/g true imio wireless card
vender: airgo networks inc
physical id:1
bus info: pci@0000:02:00.0
version: 03
width: 32 bits
Clock: 33mhz
capabilities: pm cap_list
configuration: latency=248 maxlatency=255 mingnt=24

*-network disabled
description: ethernet interface
physical id: 3
logical name: pan0
serial:7e:32:47:bc:dd:ac
capabilities: brodcast=yes driver=bridge driverversion=2.3 firmware=n/a link=yes multicat=yes

---

### Post by nothingspecial on 2009-09-14
Have a look at [[COLOR="Magenta"]this[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D8010").

You may have to use your sounless desktop to download the driver and copy it across

---

### Post by I WILL DO IT on 2009-09-14
what about the Ethernet controller?

---

### Post by stalkingwolf on 2009-09-14
What version are you using?

I had a similar problem on my NC8000.  with 8.10 and 9.04 my wireless adapters showed as disabled.  I installed 8.04 and all was fine.  Yesterday
i tried 9.04 on it again and ill be damned if everything didnt just work,
including the wireless.

---

