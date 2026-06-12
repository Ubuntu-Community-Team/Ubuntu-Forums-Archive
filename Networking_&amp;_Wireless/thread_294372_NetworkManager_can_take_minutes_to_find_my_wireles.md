---
title: "NetworkManager can take minutes to find my wireless network"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by sgarman on 2006-11-06
Hi there,

I'm running Edgy on a Sony VAIO S260 laptop. It uses the ipw2200 wireless chipset kernel driver. I'm using network-manager to connect to wireless networks. My home network uses WPA encryption, ssid broadcast enabled, and the access point is a D-Link DI-624 wifi router.

I'm finding that intermittently it can take network-manager 3-5 *minutes* to notice my network and begin to associate with it after booting up or resuming from suspend. If I click on the network manager icon, it sees some ssids, but not my own. If I run "iwpriv eth1 scanning", I notice my ssid is sometimes there and sometimes not if I run the command over and over again quickly. 

My router allows me to set the beacon interval for 802.11 packets, which is by default set to 100ms. That's pretty frequent. Under WindowsXP the wireless device associates immediately, so I don't believe it is a hardware issue. I also tried changing the wifi channel my access point uses, and that didn't make a difference either. 

Can anyone tell me how network-manager polls for wireless ssids? Is there anything I can do from a shell script to force it to poll faster?

Thanks,

Scott

---

### Post by wieman01 on 2006-11-07
I have dropped NetworkManager because I found it unreliable, plus it does not support Static IP & hidden ESSID. If you are interested in a manual configuration of your wireless network, you can try this instead:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

This works with no constraints (static IP, DHCP, broadcast of ESSID disabled, WPA1, WPA2, etc.).

_**EDIT:**_
I have a Sony Vaio with an "ipw2200" wireless adapter as well. The "wpa-driver" (see thread) is "wext"... No issues with it.

---

