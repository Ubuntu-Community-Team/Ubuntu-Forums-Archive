---
title: "3945 ABG users - please read this (it works on opensuse 10.3)"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by Neil_The_Newbie on 2008-03-21
Having struggled to get Ubuntu working with the 3945ABG card I was recommend to try OpenSuse 10.3.

After a normal installation didnt get my wifi working i went to this page:

[http://en.opensuse.org/HCL/Network_Adapters_%28Wireless%29](http://en.opensuse.org/HCL/Network_Adapters_%28Wireless%29)

and followed this instruction on the page:

SuSE 10.3 - Works, but there is a bug [1]. There is an upstream fix, but it hasn't made it into the regular updates. You can install the update by adding "http://download.opensuse.org/repositories/driver:/wireless:/10.3/openSUSE_10.3_update/" as a software repository, then in YaST Software Management, search for ipw3945, and update your kernel module (reboot to take effect). The traditional "ifup" process is reported to work as an alternative to the GUI Network Manager. To connect to get this fix using Network Manager, you will need to turn the wireless radio on and off using the hardware switch on your computer until Network Manager finally connects (tip: turn radio off, wait until NM shows no connection icon, turn radio on, once the connecting icon appears, wait about 5-6 sec., and if no progress is made, turn radio off until no connection icon appears, repeat until connection progress is made, then wait for connection).

My wifi is now working! :)

---

