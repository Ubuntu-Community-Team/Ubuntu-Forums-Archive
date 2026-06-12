---
title: "Kernel upgrade = wireless AWOL!"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by dangermouse28 on 2006-09-07
Right, here's a good one for our wireless experts.

I've been using an old Xterasys wireless PC card (module adm8211)in my laptop ever since Dapper was released and it's worked perfectly. I installed and compiled a vanilla 2.6.17 kernel (using the existing .config as a starting point) which works great apart from my wireless connection. The machine boots, loads the module, the card bursts into life showing both link and activity but it won't cannect to my router. It will scan, find the essid etc but the router just doesn't want to know.

I rebooted back into the 2.6.15 kernel and everything is fine. Rebooted back into the 2.6.17 kernel and it's still no go.

I tried dumping ifconfig and iwconfig for both kernels and the only difference is that for the newer kernel there is a message

"Driver for device eth1 has been compiled with version 20 of Wireless Extension, while this program supports up to version 19"

I can't find any other difference - has anyone any ideas or will I need to go the ndiswrapper route? :-k

---

