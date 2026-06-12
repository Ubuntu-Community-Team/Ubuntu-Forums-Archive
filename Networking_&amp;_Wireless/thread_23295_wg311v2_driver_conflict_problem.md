---
title: "wg311v2 driver conflict problem"
date: 2005-04-01
forum: Networking &amp; Wireless
---

### Post by endrylthalan on 2005-04-01
Hello,

I've got a warty which tried to use the acx100 ( pre8 ) driver to manage my netgear wg311v2. As it was not working I tried to switch to ndiswrapper which is working really fine under my Knoppix. I don't remember everything I've done to remove acx (delete acx files,...) helped by an howto wiki I've found via acx100.sourceforge.net
I installed ndiswrapper (drivers are loaded and ndiswrapper modprobed) but the network really takes a long time to load for nothing
Impossible to activate the wireless network
I believe something of acx is still remaining and conflict with ndiswrapper...

I don't really know what to do now...  :-(

---

### Post by stevenyu on 2005-04-14
I got nidswrapper working with my netgear wg311v2, follow my step you should get it working too

1 - remove the acx driver from /lib/modules/kernal_uname/net/wireless

2 - compile the lastest ndiswrapper from sf

3 - install your windows driver for nidswrapper

4 - ndiswrapper -m to write to modprobe

5 - depmod -a

6 - edit /etc/network/interfaces

7 - reboot

---

