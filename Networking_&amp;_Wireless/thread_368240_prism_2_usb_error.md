---
title: "prism 2 usb error"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by kski on 2007-02-23
i'm trying to get my linksys wusb11 2.5 working on edgy.  iwconfig says wlan0 has no wireless extensions. 


from dmesg:

[17179593.808000] prism2usb_init: prism2_usb.o: 0.2.5 Loaded
[17179593.808000] prism2usb_init: dev_info is: prism2_usb
[17179593.848000] usbcore: registered new driver prism2_usb
[17179594.084000] ieee80211_crypt: registered algorithm 'NULL'
[17179594.088000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179594.088000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179595.024000] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)
[17179595.024000] hfa384x_drvr_start: cmd_initialize() failed, result=-5
[17179595.024000] prism2sta_ifstate: hfa384x_drvr_start() failed,result=-5
[17179596.024000] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)
[17179596.024000] hfa384x_drvr_start: cmd_initialize() failed, result=-5
[17179596.024000] prism2sta_ifstate: hfa384x_drvr_start() failed,result=-5

help!

---

