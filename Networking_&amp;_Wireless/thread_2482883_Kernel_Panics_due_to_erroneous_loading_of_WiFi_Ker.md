---
title: "Kernel Panics due to erroneous loading of WiFi Kernel Modules"
date: 2023-01-13
forum: Networking &amp; Wireless
---

### Post by poddus2 on 2023-01-13
Ubuntu 20.10 LTS 5.15.0-57-generic

I have been having soft lockups since January 3rd. They had been getting more frequent to the point that my computer would freeze up right on the login screen. journalctl consistently showed a failure of the ethernet connection, followed by usb.

```
igb 0000:04:00.0 enp4s0: PCIe link lost
xhci_hcd 0000:06:00.1: xHCI host controller not responding, 
xhci_hcd 0000:06:00.1: HC died; cleaning up
usb 1-2: USB disconnect, device number 2
usb 1-2.1: USB disconnect, device number 4
usb 2-2: USB disconnect, device number 2
usb 2-2.1: USB disconnect, device number 3
usb 1-2.3: USB disconnect, device number 6
acpid[1116]: input device has been disconnected, fd 17
acpid[1116]: input device has been disconnected, fd 18
usb 1-2.4: USB disconnect, device number 7
acpid[1116]: input device has been disconnected, fd 19
usb 1-3: USB disconnect, device number 3
usb 1-4: USB disconnect, device number 5
------------[ cut here ]------------
NETDEV WATCHDOG: enp4s0 (igb): transmit queue 0 timed out
```

the traces would sometimes show cpu idle, however often they included messages about kernel modules used for WiFi connectivity

```

? rtl_hal_pwrseqcmdparsing+0x129/0x220 [rtlwifi]
_rtl8821ae_init_mac+0xac1/0xb00 [rtl8821ae]
rtl8821ae_hw_init+0x130/0x630 [rtl8821ae]
rtl_ps_enable_nic+0x44/0x130 [rtlwifi]
_rtl8821ae_phy_set_rf_power_state+0x2d5/0x330 [rtl8821ae]
rtl8821ae_phy_set_rf_power_state+0x1a/0x30 [rtl8821ae]
rtl_ps_set_rf_state.isra.0+0xd0/0x120 [rtlwifi]
_rtl_ps_inactive_ps+0x3b/0xd0 [rtlwifi]
rtl_ips_nic_on+0xae/0xf0 [rtlwifi]
rtl_op_config+0x2ce/0x4a0 [rtlwifi]
ieee80211_hw_config+0x8c/0x100 [mac80211]
ieee80211_recalc_idle+0x2d/0x40 [mac80211]
__ieee80211_start_scan+0x224/0x690 [mac80211]
ieee80211_request_scan+0x30/0x60 [mac80211]
ieee80211_scan+0x66/0x100 [mac80211]
rdev_scan+0x2d/0xb0 [cfg80211]
cfg80211_scan+0xf6/0x120 [cfg80211]
nl80211_trigger_scan+0x47e/0x930 [cfg80211]
genl_family_rcv_msg_doit+0xe7/0x150
genl_rcv_msg+0xe2/0x1f0
? nl80211_send_scan_start+0xb0/0xb0 [cfg80211]
...

```

this is strange, since I do not have any wifi-capable hardware installed. After adding the kernel modules to /etc/modprobe.d/blacklist.conf via recovery mode the system is once again stable (fingers crossed).

```
# these may be causing kernel panics. there are no wifi cards in this computer
# so lets forego these for now
blacklist rtl8821ae
blacklist rtlwifi
blacklist mac80211
blacklist rtl_pci
blacklist cfg80211

```

I'm wondering now where I should report this bug. It took a long time to get here and in the process I tried live-imgs of Debian 11 and Fedora 37 with the same problem, so I think this might be a distro-independent bug.

---

