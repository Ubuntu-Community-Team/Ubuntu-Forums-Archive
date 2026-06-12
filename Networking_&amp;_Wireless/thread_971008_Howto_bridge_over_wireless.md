---
title: "Howto bridge over wireless?"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by zyberzero on 2008-11-04
Hi!

I got a network with a Wireless router with both WPA-encryption and MAC-addressfiltering for the wireless network.

I want to connect my laptop to a switch, and all the things connected to the switch will connect thru the laptop to my router.

I tried to achieve this by first connecting Wlan0 to my router (which works fine) but when I add the bridge the laptop disconnects from the router.

#ifconfig wlan0 0.0.0.0
#ifconfig eth0 0.0.0.0
#brctl addbr bridge0
#brctl addif bridge0 wlan0 <-- Here disconnects the laptop
#brctl addif bridge0 eth0
#brctl setfd bridge0 0
#ifconfig bridge0 up

 
How can I do this?

Thanks in advance,
Zyber

---

### Post by zyberzero on 2008-11-05
Another notice: I think I have a Intel wireless card (IPW2100 or IPW2200) if that makes any difference.


/Zyber

---

