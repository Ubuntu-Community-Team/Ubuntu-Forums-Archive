---
title: "Intel 7260 wifi drops connection to router"
date: 2015-02-03
forum: Networking &amp; Wireless
---

### Post by sye737 on 2015-02-03
I have a Ubuntu 14.10 machine with the intel 7260 chipset. About once every hour or two it drops connection to the router, but the indicator still think it's connected. In this state I cannot ping my router or any other local computer. If I manually reconnect via gui or 'nmcli d wifi connect' then it works again, but it's definitely annoying. The only change is that I updated the microcode for iwlwifi-7265-9.ucode to the December 2014 release. 

Also when I try to connect to my AP for the first time it doesn't work, saying something along the lines of "Connection activation failed.", and only when editing the connection manually and adding my password then it works normally. It always works with nmcli.

My router is a Buffalo WHR-HP-G300N, and my OS X laptop has no problems with its wifi.

---

