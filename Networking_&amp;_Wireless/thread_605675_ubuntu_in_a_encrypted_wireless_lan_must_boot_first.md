---
title: "ubuntu in a encrypted wireless lan must boot first,instead connection does not work"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by irruenza on 2007-11-07
Hi,
I'll try to explane my wireless problem:
i've a toshiba satellite a100-881(intel 3945 ) running gutsy, a desktop running both windows and gutsy, a router digicom michelangelo wave and a wep encrypted wireless lan.
I can connect ubuntu (both on desktop and laptop) only if there's not another "ubuntu" connected:
let me try to do some examples to better explain the problem:

start router
start ubuntu on laptop => connection on laptop is working fine
then, if i start ubuntu on desktop it can't connect, returning me the "enter encryption key" diag (instead if i start win on desktop it can connect without problem).

another examples:
start router
start winxp on desktop (connection ok)
start ubuntu on laptop =>can't connect and  "enter encryption key" diag 

same thing if i connect first my desktop (ubuntu or winxp, is the same), laptop can't connect.

it seems that in my wlan i can't connect more than 1 pc with ubuntu, and, off course, it must be booted first.

does anyone has an idea on why it happen?
thanx 
ale

---

### Post by bliffle on 2007-11-07
Are you certain that this problem is ubuntu related? What if you try getting on the LAN with XP on both macines?

It may be the way your wireless AP is setup. Checkout the options setup when you logon to the AP in supervisor mode.

---

### Post by irruenza on 2007-11-07
two pc's running windows work.
Today i tried disabling roaming mode and setup network manually, it worked!
only i can't understand why automatic mode worked in that way?!?!?!
I will go into that.

---

### Post by irruenza on 2007-11-10
no way...
sometimes it works sometimes not....i can't understand.
i tried to check out the router's options and i think they are good..maybe the problem could be the encrypted wep key.....

---

