---
title: "[SOLVED] Wireless and wired conflict"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by speed32219 on 2008-08-23
I have a slight problem with the wireless and wired network.  In order for me to get the wireless running I need to disable both wired nic's and vica versa.  I have my wiress setup **(USB Netgear MA101 802.11b)** for a 192.168.**0**.100 network and the wired set up for 192.168.**1**.100 with **gateways** that are 192.168.0.1 wireless and 192.168.1.1 wired.

They both work fine independantly of each other but I need to shutdown the one I'm not using (Sometimes I need to reboot to have it take effect, **what is the command **to remove/re-load networking?) **Found it: sudo /etc/init.d/networking Restart**( didn't know that Restart disabled than enabled.)  What I am doing is setting up the wireless Ubuntu server with XBMC installed as an app using 8.04 hardy for testing (Native 720p and 1080i) and the wired one is for my Xbox Xbmc using the server as a file server (Upscales to 720P and 1080i).

I eventually would like to have the 192.168.1.100 Xbox Xbmc wired network to access the Gateway (Internet) via the Ubuntu wireless 192.168.0.100 network.   (That will be the next project, I might need to setup a VM or something to accomplish that)

PS.  The wireless works great at 11 Mbps and is fast.  Just having problems running both wired and wireless at the same time.

**Solved** this by making the changes to the wireless and wired network using the network tools under administration and then running the command from terminal: sudo /etc/init.d/networking Restart.

---

