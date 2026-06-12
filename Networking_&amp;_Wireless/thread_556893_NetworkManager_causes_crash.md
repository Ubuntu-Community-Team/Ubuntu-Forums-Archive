---
title: "NetworkManager causes crash"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by duffrecords on 2007-09-21
I'm running Feisty 7.04 with kernel 2.6.20-16-lowlatency on a Dell Inspiron 8200 laptop.  Everything was going fine for a few weeks but recently I'm discovering some unrecoverable crashes when leaving it idle for several hours.  It wasn't doing it before and I'm using the same kernel on a desktop with no such problem.  I looked in the system log and at the time of each crash, there are debug messages related to NetworkManager:
> Sep 21 17:34:55 inspiron NetworkManager: <debug info>^I[1190421295.259302] nm_device_802_11_wireless_update_bssid (): Roamed from BSSID 00:13:10:A1:18:C6 to 00:12:17:04:0C:57 on wireless network 'linksys' 
Sep 21 17:36:55 inspiron NetworkManager: <debug info>^I[1190421415.242193] nm_device_802_11_wireless_update_bssid (): Roamed from BSSID 00:13:10:A1:18:C6 to 00:12:17:04:0C:57 on wireless network 'linksys' 
Sep 21 17:38:55 inspiron NetworkManager: <debug info>^I[1190421535.224890] nm_device_802_11_wireless_update_bssid (): Roamed from BSSID 00:13:10:A1:18:C6 to 00:12:17:04:0C:57 on wireless network 'linksys' 
Sep 21 17:40:55 inspiron NetworkManager: <debug info>^I[1190421655.210465] nm_device_802_11_wireless_update_bssid (): Roamed from BSSID 00:13:10:A1:18:C6 to 00:12:17:04:0C:57 on wireless network 'linksys' 
Sep 21 17:42:55 inspiron NetworkManager: <debug info>^I[1190421775.193265] nm_device_802_11_wireless_update_bssid (): Roamed from BSSID 00:13:10:A1:18:C6 to 00:12:17:04:0C:57 on wireless network 'linksys' 
Sep 21 17:52:58 inspiron NetworkManager: <debug info>^I[1190422378.402256] nm_device_802_11_wireless_update_bssid (): Roamed from BSSID 00:13:10:A1:18:C6 to 00:12:17:04:0C:57 on wireless network 'linksys' 
Sep 21 17:54:58 inspiron NetworkManager: <debug info>^I[1190422498.384967] nm_device_802_11_wireless_update_bssid (): Roamed from BSSID 00:13:10:A1:18:C6 to 00:12:17:04:0C:57 on wireless network 'linksys' 
Sep 21 17:56:58 inspiron NetworkManager: <debug info>^I[1190422618.366484] nm_device_802_11_wireless_update_bssid (): Roamed from BSSID 00:13:10:A1:18:C6 to 00:12:17:04:0C:57 on wireless network 'linksys' 
Sep 21 17:58:58 inspiron NetworkManager: <debug info>^I[1190422738.348425] nm_device_802_11_wireless_update_bssid (): Roamed from BSSID 00:13:10:A1:18:C6 to 00:12:17:04:0C:57 on wireless network 'linksys' 
Sep 21 18:00:58 inspiron NetworkManager: <debug info>^I[1190422858.332044] nm_device_802_11_wireless_update_bssid (): Roamed from BSSID 00:13:10:A1:18:C6 to 00:12:17:04:0C:57 on wireless network 'linksys' 
Sep 21 18:02:58 inspiron NetworkManager: <debug info>^I[1190422978.314554] nm_device_802_11_wireless_update_bssid (): Roamed from BSSID 00:13:10:A1:18:C6 to 00:12:17:04:0C:57 on wireless network 'linksys' 
Sep 21 18:04:58 inspiron NetworkManager: <debug info>^I[1190423098.297431] nm_device_802_11_wireless_update_bssid (): Roamed from BSSID 00:13:10:A1:18:C6 to 00:12:17:04:0C:57 on wireless network 'linksys' 
Sep 21 18:06:58 inspiron NetworkManager: <debug info>^I[1190423218.279957] nm_device_802_11_wireless_update_bssid (): Roamed from BSSID 00:13:10:A1:18:C6 to 00:12:17:04:0C:57 on wireless network 'linksys' 
Sep 21 18:09:00 inspiron NetworkManager: <debug info>^I[1190423340.455517] nm_device_802_11_wireless_update_bssid (): Roamed from BSSID 00:13:10:A1:18:C6 to 00:12:17:04:0C:57 on wireless network 'linksys' 
Sep 21 18:11:00 inspiron NetworkManager: <debug info>^I[1190423460.437367] nm_device_802_11_wireless_update_bssid (): Roamed from BSSID 00:13:10:A1:18:C6 to 00:12:17:04:0C:57 on wireless network 'linksys' 
What's the next step I should take to troubleshoot this?

---

### Post by duffrecords on 2007-09-28
Actually, the problem seems to have disappeared since I got the most recent software updates via update-manager.

---

### Post by duffrecords on 2007-10-01
Actually, I take it back.  The crashes only happened when I had the GIMP running, and I realized it began after I installed the dds-1.2.1 and normalmap-1.2.1 plugins.  After uninstalling those, everything went back to normal.

---

