---
title: "wireless problems after 8.10 upgrade"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by popus57 on 2008-11-06
Hi,

I upgraded my older laptop from xubuntu 8.04 to 8.10. Everything ran well previously. Right now the machine won't boot with my netgear usb 80211.b adapter plugged it. It boots fine if I have ethernet or nothing plugged in. It hangs after the post login splash screen where it goes to terminal and shows some output about configuring bluetooth devices (which I don't have).

If I boot the machine without the wireless and plug the modem in, it does not recognize it. If I click on network configuration, I get a message that network-admin is missing. I have tried looking for this file using synaptic but no luck.

Any help would be greatly appreciated.

Thanks

---

### Post by popus57 on 2008-11-07
OK, 

I've made some progress here. I installed gnome-network-admin and I am able to adjust my network settings again. I also removed anything bluetooth using synaptic and I am not getting the crash and errors when I boot with the usb modem plugged in. The wireless still doesn't work though.

Any suggestions appreciated.

Thanks.

---

### Post by popus57 on 2008-11-08
OK,

I,ve continued messing around with this and due to the fact that my installation is a bit gummed up (been on there since 6.04), I decided to backup my home directory and reinstall from a cd. The reinstillation process went without a hitch but now I am back to the same problem where it is trying to load bluetooth drivers and hangs on boot. If I boot with the ethernet cable plugged in, all works fine with the boot. However, when I plug in the usb wireless modem, it sees the network but can't make the connection. If I traceroute, it doesn,t see the router.

Please Help!

Thanks

---

### Post by popus57 on 2008-11-09
OK,

I went and bought a new wireless g PMCIA card. It was able to make a connection immediately. Problem solved ($50 later).

---

