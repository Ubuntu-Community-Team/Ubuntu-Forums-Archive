---
title: "Wireless only works when ethernet is plugged in (hotplug issue?)"
date: 2005-06-06
forum: Networking &amp; Wireless
---

### Post by briguy on 2005-06-06
I recently upgraded the driver and firmware on my ipw2200 adaptor.  In the process of doing this, I managed to completely remove the driver by mistake.  It's back on and working, however during the one boot where there was no driver, the network configuration got messed up and now the wireless adaptor (eth0) will only connect when the wired lan adaptor (eth1) is plugged in.  Kind of defeats the purpose really.

I'm assuming that this is a hotplug related problem, that somewhere along the line eth1 is referred to as eth0 in a configuration file.  Unfortunately the inner workings of hotplug are a mystery to me and I don't know where to start looking.  Can anyone point me in the right direction?

---

### Post by briguy on 2005-06-09
Okay, problem solved.  I tried to install Network Manager, which broke the wireless.  I had to apt-get remove network-manager-gnome network-manager libgcrypt7 and reboot to get it to work again.

---

