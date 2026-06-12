---
title: "Adjusting Tx power?"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by baguahsing on 2010-06-04
I loose my connection if I get too far away from the router.  Will adjusting the Tx power help?  If so, how do I do that?

---

### Post by bkratz on 2010-06-04
Sorry but it may or may not.  To change the setting try

sudo iwconfig wlan0 txpower 21

substitute the name of your wireless connection for the wlan0 above. Also, i picked the 21 arbitrarily, you can raise or lower this figure until you get an error response, but this is pretty high.

---

