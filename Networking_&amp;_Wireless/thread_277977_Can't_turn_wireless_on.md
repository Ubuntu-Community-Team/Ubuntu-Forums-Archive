---
title: "Can't turn wireless on"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by MaxTeel on 2006-10-15
I have ubuntu 6.06 and it always had wireless( with an ipw2200). But a few day ago I installed pptp so I could log with vpn in my university. It worked, but when I started the computer again, the wireless wouldn't turn on. Using iwconfig and ifconfig I noticed the board was off, but I couldn't turn it on (it said something like "input/output error")

the dmesg said

"[17179593.928000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17179593.928000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179593.928000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!"

and 
"[17179599.212000] ADDRCONF(NETDEV_UP): eth0: link is not ready"

I know I have to update, but since it was working, I want to know if there a solution without using ndiswrapper.

I have my system with all the updates installed.

Thanks in advance...

---

