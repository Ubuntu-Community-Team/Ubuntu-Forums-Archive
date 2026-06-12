---
title: "Working wifi router doesn't show up in wicd scan list"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by damagednoob on 2008-10-25
I have public, unsecured (for the moment) wifi router that I'm trying to connect to. I know the router works because I used to be able to connect to it when I was running Xandros and I have another pc that can connect to it fine. I can connect to other wifi routers without any problem. It doesn't show up in wicd/network manager/iwlist. I also can't seem to connect to it manually (explicitly specifying the ESSID) in wicd.

I have an ASUS EEE 701 4G PC. I've installed Ubuntu 8.04 and the madwifi-hal-0.10.5.6 drivers. 

Any ideas where I can begin to start trouble-shooting this?

---

### Post by damagednoob on 2008-10-26
Okay. With the help of someone on #wicd on freenode, I managed to figure it out. Months ago I was having connectivity issues with the wifi on dell laptop, so I manually set channel selection on my router from Auto to Manual. I then set the channel to 13. When I set it back to Auto, it chose channel 1 and my router started showing up again in my list.

---

