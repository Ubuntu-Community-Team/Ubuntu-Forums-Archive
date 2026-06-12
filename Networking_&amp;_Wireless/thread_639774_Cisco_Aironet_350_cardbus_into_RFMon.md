---
title: "Cisco Aironet 350 cardbus into RFMon"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by Junglizer on 2007-12-13
Just throwin' this one out there:

I need help or some drivers for a Cisco Aironet 350 cardbus that will allow me to manually drop the card into rfmon mode. I can get this card to work in permiscious using the cisco_wifix drivers with Kismet however this is rather unacceptable, I would prefer to find a way to drop the card manually and then be able to use airsnort and other apps. Full channel hopping would obviously be preffered but it is not mandatory. Runing on a 2.6 kernel currently. 
```

iwconfig eth1 mode Monitor

``` or whatever it is, I can't remember it off the top of my head. However it returns ```
 echo $?
0

```
But neither the ifconfig eth1 listing is changed nor is the card actually dropped to rfmon. Is this a kernel issue also? I know that there were a lot of issues with the 2.4x cisco drivers. I'm not opposed to recompiling but 90% of the wireless opts should be built-in already.

I know chances are slim of others have this perticular problem on these forums, but I thought I'd give it a go.

---

### Post by Junglizer on 2007-12-13
Bump for response?

---

