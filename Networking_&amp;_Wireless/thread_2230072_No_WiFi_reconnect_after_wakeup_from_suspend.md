---
title: "No WiFi reconnect after wakeup from suspend"
date: 2014-06-17
forum: Networking &amp; Wireless
---

### Post by cYbercOsmOnauT on 2014-06-17
When I reopen the lid from my Laptop everything works fine. Just my WiFi isn't able to reconnect to our WLAN. dmesg shows me:
```
[40349.860133] Intel(R) Wireless WiFi driver for Linux, in-tree:
[40349.860139] Copyright(c) 2003- 2014 Intel Corporation
[40349.860354] iwlwifi 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[40349.860516] iwlwifi 0000:08:00.0: irq 47 for MSI/MSI-X
[40349.861297] iwlwifi 0000:08:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[40349.864788] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUG disabled
[40349.864791] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[40349.864793] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[40349.864794] iwlwifi 0000:08:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[40349.864886] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[40349.884016] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[40350.265837] r8169 0000:07:00.0 eth0: link down
[40350.265899] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[40350.266847] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[40350.274535] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[40350.519480] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[40350.527165] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[40350.599960] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[40370.665892] wlan0: authenticate with --Router MAC adress--
[40370.670083] wlan0: send auth to --Router MAC adress-- (try 1/3)
[40370.674389] wlan0: authenticated
[40375.679504] wlan0: aborting authentication with --Router MAC adress-- by local choice (Reason: 3=DEAUTH_LEAVING)
[40385.798885] wlan0: authenticate with --Router MAC adress--
[40385.802224] wlan0: send auth to --Router MAC adress-- (try 1/3)
[40385.806246] wlan0: authenticated
[40385.994398] wlan0: aborting authentication with --Router MAC adress-- by local choice (Reason: 3=DEAUTH_LEAVING)
... and so on...
```
I tried to set the IP manually without DCHP. Same problem. I disabled 11n in iwlwifi. Same problem. I attached the output of the wireless_script. Any help with this somewhat annoying problem is appreciated :)

---

### Post by chili555 on 2014-06-17
Did you try this? [http://ubuntuforums.org/showthread.php?t=2004690&p=12031410#post12031410](http://ubuntuforums.org/showthread.php?t=2004690&p=12031410#post12031410)

---

### Post by cYbercOsmOnauT on 2014-06-17
Thanks for your reply chili555. I forgot to mention that this was even my first try. ;)
```
tekin@Ubuntu-Laptop:~$ cat /etc/pm/config.d/config 
SUSPEND_MODULES="iwlwifi"
```

---

### Post by chili555 on 2014-06-17
Would you please try a couple of other things? Please edit the file to make it:```
SUSPEND_MODULES="iwldvm"
```If that doesn't help, then:```
SUSPEND_MODULES="iwldvm iwlwifi"
```If all of these are ineffective, see if, rather than trying to reload the module, this helps:```
sudo service network-manager restart
```

---

### Post by cYbercOsmOnauT on 2014-06-17
I tried all three ways (with a reboot between them) and still no chance. I always see the DEAUTH_LEAVING inside dmesg. But the connection after a clean boot works fine. Only after suspend it cannot reconnect.

---

### Post by cYbercOsmOnauT on 2014-06-21
The only way I found to somewhat solve this is to try
```
sudo killall wpa_supplicant
```
until it connects correctly. :(

---

