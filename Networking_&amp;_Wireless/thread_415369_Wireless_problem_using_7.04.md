---
title: "Wireless problem using 7.04"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by pikz on 2007-04-20
I have managed to get my wireless connection working using ndiswrapper, but there is a problem. I have to start the wireless connection every time I have restarted my computer. I use the following commands to start it:

sudo iwconfig eth1 essid wlan-ap
sudo ifconfig eth1 up
sudo dhclient

But 'ifconfig eth1 up' only works after I have put the computer to sleep and wake it up. If I don't do that then ifconfig won't find eth1.

Can someone help me?

---

