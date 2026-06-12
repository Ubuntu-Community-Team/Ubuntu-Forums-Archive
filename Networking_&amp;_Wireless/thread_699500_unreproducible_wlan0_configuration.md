---
title: "unreproducible wlan0 configuration"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by Embiggens on 2008-02-17
Hi,
I've semi-successfully installed ndiswrapper for my smc 2802w v2 wirelss card.  I have 2 problems when I reboot, though:
1) Blacklisting the "incorrect" wireless driver doesn't work.  When I search around, most people say the name of the driver that should be blacklisted for this card is 'prism54'.  I'm seeing that it's 'prism54pci' for me.  So to be safe, my "etc/modprobe.d/blacklist" file contains

```
blacklist prism54pci
blacklist prism54
```

Despite this, prism54pci is still the driver associated with wlan0 when I reboot (I check this with lshw -C network)  To get my wirelss working, I have to "sudo modprobe -r ndiswrapper" (b/c i'm trying to load this instead of prism54pci in the first place) then "sudo modprobe -r prism54pci" then "sudo modprobe ndiswrapper".

2) my wlan0 doesn't always show up, period.  In my most recent reboot, in which wlan0 did show up and is associated with wlan0, I got the following message from "dmesg|grep wifi":
```
[  101.011871] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[  101.011942] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[  101.012018] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[  101.012142] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register

```
Any ideas?  Thanks.

---

### Post by mrsteveman1 on 2008-02-17
I'm not sure about the blacklist thing not working, but that last set of errors means that the driver you loaded for the wlan chipset is trying to use symbols in the kernel that aren't there, probably because other modules need to be loaded (which should have been automatic).

Not sure what to do about it though. Perhaps run depmod -ae and try loading the ieee80211 modules first

---

### Post by Embiggens on 2008-02-19
Ok, thanks Steve.  Your post suggested to me that these issues were linked.  Going one step deeper into dmesg, I noticed the following line just before the wifi errors:
> [  100.006339] p54: LM86 firmware
[  100.988146] ieee80211_init: failed to initialize WME (err=-17)
[  101.011871] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[  101.011942] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[  101.012018] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[  101.012142] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
I figured p54 was the prism54 driver that I wasn't blacklisting correctly.  So I added "blacklist p54pci" to my /etc/modprobe.d/hotplug file and voila, all those error lines were gone from dmesg and the blacklisting works. 

Still, I am really puzzled about why I need to call this module p54pci instead of prism54pci (moreover, why am I dealing with prism54pci instead of prism54 in the first place?)  Anyway, it's working now, thanks for the lead.

---

### Post by mrsteveman1 on 2008-02-19
From some quick checking it does appear that prism54 is an old driver and that p54 is the new one, which means there are in fact 2 drivers for that card in the kernel.

Have you tried just using the p54 driver? It might work better than ndiswrapper

---

