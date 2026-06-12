---
title: "BCM4328 on Ubuntu 14.04 (Macbook Pro)"
date: 2014-10-20
forum: Networking &amp; Wireless
---

### Post by kmand on 2014-10-20
I have a older generation Macbook Pro with a built in BCM4328 wireless chip. I dual boot OS X and Ubuntu 14.04. The wirelless works on OS X but not Ubuntu. It does come up as wlan0, sees all the wireless access points, but never connects. I'm up on a USB wireless adapter but would really like to use the built in wireless.

Here is what the log shows even when I try to connect to an open  access point with security turned off.

Oct 20 22:50:39 km-MacBookPro NetworkManager[771]: <info> Activation (wlan0) starting connection 'wrtn'
Oct 20 22:50:39 km-MacBookPro NetworkManager[771]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 20 22:50:39 km-MacBookPro NetworkManager[771]: <info> NetworkManager state is now CONNECTING
Oct 20 22:50:39 km-MacBookPro NetworkManager[771]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 20 22:50:39 km-MacBookPro NetworkManager[771]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 20 22:50:39 km-MacBookPro NetworkManager[771]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 20 22:50:39 km-MacBookPro NetworkManager[771]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 20 22:50:39 km-MacBookPro NetworkManager[771]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 20 22:50:39 km-MacBookPro NetworkManager[771]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 20 22:50:39 km-MacBookPro NetworkManager[771]: <info> Activation (wlan0/wireless): connection 'wrtn' requires no security.  No secrets needed.
Oct 20 22:50:39 km-MacBookPro NetworkManager[771]: <info> Config: added 'ssid' value 'wrtn'
Oct 20 22:50:39 km-MacBookPro NetworkManager[771]: <info> Config: added 'scan_ssid' value '1'
Oct 20 22:50:39 km-MacBookPro NetworkManager[771]: <info> Config: added 'key_mgmt' value 'NONE'
Oct 20 22:50:39 km-MacBookPro NetworkManager[771]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 20 22:50:39 km-MacBookPro NetworkManager[771]: <info> Config: set interface ap_scan to 1
Oct 20 22:50:39 km-MacBookPro NetworkManager[771]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 20 22:51:04 km-MacBookPro NetworkManager[771]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Oct 20 22:51:04 km-MacBookPro NetworkManager[771]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Oct 20 22:51:04 km-MacBookPro NetworkManager[771]: <info> NetworkManager state is now DISCONNECTED
Oct 20 22:51:04 km-MacBookPro NetworkManager[771]: <warn> Activation (wlan0) failed for connection 'wrtn'
Oct 20 22:51:04 km-MacBookPro NetworkManager[771]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct 20 22:51:04 km-MacBookPro NetworkManager[771]: <info> (wlan0): deactivating device (reason 'none') [0]

---

### Post by Bucky Ball on 2014-10-21
Do you mean BCM43228? You need the wl driver. See [HERE]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Drivers_available_in_Ubuntu"). Under the heading 'Drivers available in Ubuntu' you will see the wl driver first in the list. If you are running BCM43228, then that is for you (it is mentioned last in the list of cards for that driver).

But first, if you can get online with a cable, do that, update the machine then check 'Additional Drivers' (maybe called Hardware Drivers in Ubuntu, I use a custom mini install with xfce4 so unsure). Is there anything in there that suggests B43 or STA drivers for your card?

Failing all this, please provide the output of:

```
sudo lshw -C network
```

... and please use [code][/ code] tags. Thanks.

---

