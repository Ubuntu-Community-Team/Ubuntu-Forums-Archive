---
title: "BCM4328, ndiswrapper + wireless N"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by mwarner on 2008-05-19
Hello All,

I've been using ubuntu on my laptop for sometime now and am having trouble with wireless N. I have a BCM4328 wireless card installed using ndiswrapper. For the most part its works great. However in certain situations it disconnects for no apparent reason.

This problem happens whenever trying to mount NFS shares, and basically anything bandwidth intense. Whenever I put the connection under load this happens (weather downloading from the net or accessing a samba shares). It seems to happen independent of the number of connections, just any continued transfer over a few hundred KB/s. 

When it disconnects networkmanager and iwconfig show it still being connected, however I can't access anything. dmesg doesn't have any output related to it at all. The only way I can reconnect is to remove the ndiswrapper module, then load it again.

After a little playing around the only work around I could find was to change my router to only accept wireless G connections. This is annoying as I do a lot of file transfers, with wireless G I get at best a quarter of the speed I can reach with wireless N. The router is a dlink DIR-655 and none of my other computers have any trouble with disconnects. Just this one card seems to be an issue.

Has anyone else encountered something similar to this? And where should I be looking to find whats wrong, If I could at least get an error message it would be nice. I've tried every driver version for my card I could find, I've also tried several router firmware versions just to be safe.

---

