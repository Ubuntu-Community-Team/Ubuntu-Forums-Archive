---
title: "DNS trouble"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by szekelyrobi on 2007-10-28
On our wifi ubuntu uses a bad dns, In system-Administration-Network I tried to add the right dns, but it keeps changing it back to the bad one... very annoying! Is there a way of adding dns as a root or something?:confused:

---

### Post by jackocleebrown on 2007-10-28
If you are using DHCP (Ubuntu automatically gets IP from wireless router) then the DNS is passed to ubuntu by the DHCP server (probably in the router). If you are not sure what this means and you just select the wifi network you want and click to connect then you are probably using DHCP. If this is the case you need to change the DNS setting on the router so that it tells Ubunu the correct addresses when it connects. 

Does this make sense??
Good Luck!

Jack.

---

### Post by dburnett77 on 2007-10-29
There is a command within --netstat--, and some routers are configurable for this, but I can't even pull off a search for it right now,,

Sorry,

---

### Post by szekelyrobi on 2008-02-10
Thank you, we solved it!

---

