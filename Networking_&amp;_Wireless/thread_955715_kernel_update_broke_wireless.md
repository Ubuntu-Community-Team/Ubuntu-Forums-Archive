---
title: "kernel update broke wireless"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by craiggale on 2008-10-22
i recenty upgraded to kernel 2.6.27 from 2.6.24. My wireless works fine on the old kernel but on the new kernel network manager doesn't find my network.

I have a Intel PRO/Wireless 2915ABG Network Connection adapter, and im using ubuntu 8.04. I have set the secuirity of the network to open whilts trying to connect incase ncyption was the problem.

Also iwconfig shows wlan0 but ifconfig does not. 

Any help getting my wireless connected would be apreciated

---

### Post by btidwell on 2008-10-22
I am still on the 2.26-24 kernel, and a couple of days ago my wireless started acting weird. I have an Atheros card. The rig is dual boot, wireless works fine in Windows XP. My card will connect to my network, and then drop off. Sometimes I have to re-enter the WPA passcode. I'm wondering if one of the other updates has changed something. It worked like a champ until a couple of days ago.

---

### Post by majoridiot on 2008-10-22
> **btidwell said:**
> I am still on the 2.26-24 kernel, and a couple of days ago my wireless started acting weird. I have an Atheros card. The rig is dual boot, wireless works fine in Windows XP. My card will connect to my network, and then drop off. Sometimes I have to re-enter the WPA passcode. I'm wondering if one of the other updates has changed something. It worked like a champ until a couple of days ago.

updating the kernel to 2.6.24-21-generic from 2.6.24-19-generic the other day pretty
much makes wireless on my serval laptop useless now... it just creeeeeeeeps along.

-19 works fine, -21 not... so definitely something going on with the kernel.
definitely interested in what's going on there.

---

