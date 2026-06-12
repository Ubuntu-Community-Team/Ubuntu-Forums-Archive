---
title: "Network manager + wireless"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by woopud on 2007-01-19
I'm running Edgy 64bit on my AMD 64 HP laptop with no problems, installed fwcutter and gnome-Network-Manager and my Broadcom 4306 works perfect. Everytime I boot into Edgy it picks up my wireless network with no problem including my WEP. But i can't connect to another network, network manager only shows wired network ?

Bert
__________________

---

### Post by x64Jimbo on 2007-01-19
Go into your /etc/network/interfaces file and comment or remove the lines pertaining to your wifi card. Counter-intuitive as it may be, that is 100% of your issue.

---

### Post by woopud on 2007-01-19
Thanks, that did the trick.  Just wondering why in XP on the same laptop i only see two wireless networks available and in Unbuntu i see seven different networks ?

Bert

---

### Post by x64Jimbo on 2007-01-19
Cause Ubuntu is the bomb. :)
Actually, it probably has more to do with the linux implementation of your wifi driver.

---

### Post by x64Jimbo on 2007-01-19
<accidental double-post>

---

