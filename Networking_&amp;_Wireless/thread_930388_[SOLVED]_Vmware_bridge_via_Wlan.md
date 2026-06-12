---
title: "[SOLVED] Vmware bridge via Wlan"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by jiggygent on 2008-09-26
Hello all..

I had Vmware running fine when it was bridging to my lan via eth0.. I now have internet setup via wlan and my Vmware internet is no longer working.. I'm certain it has something to do with the fact that it is using wlan now.. I tried the following with no successful results thus far:

[http://blog.gunbladeiv.com/2008/05/change-vmware-bridge-network-interface.html](http://blog.gunbladeiv.com/2008/05/change-vmware-bridge-network-interface.html)

[http://ubuntuforums.org/showthread.php?t=795125](http://ubuntuforums.org/showthread.php?t=795125)

[http://ubuntuforums.org/showthread.php?t=785114](http://ubuntuforums.org/showthread.php?t=785114)

I'd really like to get my internet working on my xp virtual machine via wlan.. anyone have any updates or info on this??

---

### Post by willca on 2008-09-26
You tried changing the configuration via vmware-server-console, I think its Host Settings...where you can edit the network portion...

---

### Post by jiggygent on 2008-09-26
I'm not exactly sure what you mean by host settings.  I have the NIC card set to bridged in the VMware server console. I can't change the fact that the Host interface is WLan there.. and thats what my problem is.

---

### Post by jiggygent on 2008-09-26
Nevermind.. Setting it up to use bridged networking for wlan apparently is not too common.  I searched high and low and haven't really found much on that.  I decided to use NAT.  Using NAT I am now able to connect to the internet.  Thanks anyways.

---

