---
title: "wifi RT5360 dropping packages, intermittent  connection"
date: 2018-07-15
forum: Networking &amp; Wireless
---

### Post by carlosjordao on 2018-07-15
Hi,
   I have a RT5360 (rt2800pci kernel module) and some days ago I've noticed that connection with the Access Points becomes intermittent
   I tested with ping -n -c 1000 192.168.15.1 (this is the IP of my router / AP). It lost 30% or more packages, in random time intervals. When navigating, it seems to "freeze". Then I just check the ping and it has stopped responding.

   I don't know what exactly could it be. It does back pinging without intervation intervention. However,  it  reconnects faster either by clicking in the network name, which reloads it, or with the command "systemctl restart network-manager.service", which  does the same but faster. But then it stops again in a random time, but  surely in less of 5 minutes again.

   I tried all common things I've found in the Internet, like disabling power saving (did this on rc.local and NetworkManager config). Also I tweaked the rt2800pci module param "nohwcrypt" on and off, with no result. I enabled NetworkManager debug through dbus but it didn't give me a clue at the time of the freeze.

   the wireless-info script output is here:

[http://paste.ubuntu.com/p/TNBzp347MR/](http://paste.ubuntu.com/p/TNBzp347MR/)

---

