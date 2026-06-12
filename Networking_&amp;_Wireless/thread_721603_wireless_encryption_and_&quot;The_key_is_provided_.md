---
title: "wireless encryption and &quot;The key is provided for me automatically&quot;"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by Fittersman on 2008-03-11
im trying to get connected to the 'better' wireless internet my school supplies, but i cannot figure out how to get past the part where in XP i should check the box saying "The key is provided for me automatically". Where is this option in linux?

apparently (from what ive heard) the WEP key changes every now and then, and i cannot get the WEP key from them everytime it changes.

here is the actual site with the instructions on how to connect:
[http://www.uregina.ca/compserv/services/wireless/XPuofrx/wireless_setup.shtml](http://www.uregina.ca/compserv/services/wireless/XPuofrx/wireless_setup.shtml)

if anyone has any idea on how i could get connected to this under linux, it would be greatly appreciated.

---

### Post by prshah on 2008-03-13
> **Fittersman said:**
> im trying to get connected to the 'better' wireless internet my school supplies, but i cannot figure out how to get past the part where in XP i should check the box saying "The key is provided for me automatically". Where is this option in linux?

apparently (from what ive heard) the WEP key changes every now and then, and i cannot get the WEP key from them everytime it changes.

here is the actual site with the instructions on how to connect:
[http://www.uregina.ca/compserv/services/wireless/XPuofrx/wireless_setup.shtml](http://www.uregina.ca/compserv/services/wireless/XPuofrx/wireless_setup.shtml)

if anyone has any idea on how i could get connected to this under linux, it would be greatly appreciated.

ASSUMPTION: The default setting in linux is similar to "key provided automatically"

BECAUSE: I need to manually specify a key-index using iwconfig at a particular location, where they use the 2nd key-index and ignore the 1st, 3rd and 4th.

I would say ignore this and finish the rest of the setup and see if it works for you.

If it doesn't I'm sure we can figure it out with the output messages.

---

