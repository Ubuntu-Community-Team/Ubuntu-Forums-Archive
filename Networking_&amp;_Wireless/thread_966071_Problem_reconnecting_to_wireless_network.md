---
title: "Problem reconnecting to wireless network"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by asundaresan on 2008-11-01
Hi:

I'm an experienced Linux user and have been using hardy for several months now. I moved to a new place where I set up the only wireless network in the neighborhood. I set up a WEP 64 bit hex for the network. Usually when I boot fresh, the wireless network connects seamlessly. However, when the router is restarted or I awake my laptop after hibernate, I have a problem connecting. I know the wireless network is available and well because there is another laptop (windows) which is able to connect. The following are the cases and there is no pattern I can discern here 

1. Sometimes, it connects to the network by itself (the key is stored)
2. Sometimes, it asks me for key and then connects. The wireless network is visible on the drop down menu in the NetworkManager applet. Sometimes I need to enter the key several times and then it connects.
3. Sometimes, it does not see the wireless network (I'm just meters away from the router). Then I have to choose the "Connect to other wireless network" option and then enter all the details and it connects.
4. Sometimes, it just does not connect for a couple of hours and I'm almost tearing my hair out. 

All of the above cases occur at least once a day. Once it connects to the network, it stays connected until I hibernate the laptop or turn off the router which I'm forced to do because there are some power cuts.

I'm running Ubuntu 8.04 with the latest packages. The wireless chipset is 

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

I've tried restarting the networking daemon and reloading the iwl3495 module to no avail. 

Any help is appreciated. 

Thanks,
Aravind.

---

