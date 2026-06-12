---
title: "WiFi disappears on System76, Intel controller, Ubuntu 16.04"
date: 2018-05-13
forum: Networking &amp; Wireless
---

### Post by rsholmes on 2018-05-13
I have a new-ish System76 Wild Dog Pro running Ubuntu 16.04 whose WiFi has lately been failing. Symptoms are that the internet connection abruptly is lost at which point the Network settings pane shows no or almost no WiFi networks and the message "Unavailable - 802.1x supplicant failed". If I then enable wired Ethernet, that works. (And yes, I can leave the wired connection on, but I'd like to diagnose and fix the wireless problem anyway.) Restarting sometimes temporarily fixes the problem, sometimes not.

I've followed the steps in [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108). wireless-info script output here: [http://paste.ubuntu.com/p/bh9kFVktDX/](http://paste.ubuntu.com/p/bh9kFVktDX/) . Wireless interface is described only as "Intel Corporation".

---

### Post by praseodym on 2018-05-15
Please run
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi-11n.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Check wifi. If not, reboot and run
```

dmesg | grep iwl
```

---

### Post by rsholmes on 2018-06-09
After most recent restart, wifi did not start up at all.

I did:
```
$ echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi-11n.confoptions iwlwifi 11n_disable=1
$ sudo modprobe -rfv iwlwifi
remove (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) && /sbin/modprobe -r mac80211
rmmod mac80211
rmmod cfg80211
$ sudo modprobe -v iwlwifi
insmod /lib/modules/4.13.0-43-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.13.0-43-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko 11n_disable=1 

```
after which wifi was still down.

I restarted and wifi worked.

I did:
```
$ dmesg | grep iwl[   13.263303] iwlwifi 0000:08:00.0: enabling device (0000 -> 0002)
[   13.277019] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-8265-33.ucode failed with error -2
[   13.278811] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-8265-32.ucode failed with error -2
[   13.287382] iwlwifi 0000:08:00.0: loaded firmware version 31.560484.0 op_mode iwlmvm
[   13.299854] iwlwifi 0000:08:00.0: Detected Intel(R) Dual Band Wireless AC 8265, REV=0x230
[   13.354131] iwlwifi 0000:08:00.0: base HW address: 74:e5:f9:06:b3:8c
[   13.429982] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   13.431933] iwlwifi 0000:08:00.0 wlp8s0: renamed from wlan0

```

An hour and a half later, wifi abruptly stopped working. Networks settings panel says [COLOR=#000000]"Unavailable - 802.1x supplicant failed". It shows one wifi network, the one I was using, my 2.4 GHz, but no connection. My 5 GHz and other nearby wifi networks do not appear.


[/COLOR]

---

