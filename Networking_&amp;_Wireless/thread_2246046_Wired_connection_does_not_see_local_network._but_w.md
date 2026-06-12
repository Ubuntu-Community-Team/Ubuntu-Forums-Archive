---
title: "Wired connection does not see local network. but will connect to the internet"
date: 2014-09-28
forum: Networking &amp; Wireless
---

### Post by nickjhs on 2014-09-28
My wired connection works for the internet but will not see the other network connections, the WiFI on the other hand sees all the various nas drives and streaming devices and computers which are either connected via wifi or hard wired to the same router. When I turn off the Wifi and try to browse the network all I see is the "windows network" which asks for a user name and password, which has not been set. Everything worked just fine under 13.10 but not under this clean install of 14.04

Please help.

---

### Post by varunendra on 2014-09-29
The asking for password may be a samba related problem, which I may not be able to help with. But the local vs internet issue seems to be a simple routing issue.

Please show us the outputs of -
```
nm-tool
route -n
cat /etc/network/interfaces
```
Assuming you are using default Network Manager and haven't done any manual configuration in it. If you have, please let us know what.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

