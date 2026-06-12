---
title: "Ubuntu hostapd help"
date: 2014-05-30
forum: Networking &amp; Wireless
---

### Post by kenny13 on 2014-05-30
Hello all!  Recently switched to Linux and am running the latest Ubuntu 64-bit.  Now, on Windows I used Connectify to repeat my wireless internet so I could use it for my phone and other devices with lower wifi range.  However, I've heard the only Linux way involved hostapd.  I've read countless tutorials and have gotten it all set up to my knowledge, however, when I go into terminal and start the service using "sudo service hostapd start" It says it failed.  I've no idea why, I'm sure there's a way to get a much more informative description than "failed" if someone could tell me how I'd be more than happy to give the logs so we could work through this together.  Any and all help is appreciated!  (Sorry if this is in the wrong place, this seemed most appropriate to me.  Thank you.)

EDIT:  Forgot to mention, it's an Atheros wireless card that I've checked and it does have AP support.

EDIT2:  Believe I got some useful logs, appear to be a driver issue maybe?  
Probably doing spoilers wrong, but here's the log
[spoiler]kenny@kenny-Aspire-5733:~$ sudo hostapd -d /etc/hostapd/hostapd.confrandom: Trying to read entropy from /dev/random
Configuration file: /etc/hostapd/hostapd.conf
nl80211: Could not add multicast membership for vendor events: -2 (No such file or directory)
rfkill: initial event: idx=0 type=1 op=0 soft=0 hard=0
rfkill: initial event: idx=1 type=1 op=0 soft=0 hard=0
nl80211: TDLS supported
nl80211: TDLS external setup
nl80211: Supported cipher 00-0f-ac:1
nl80211: Supported cipher 00-0f-ac:5
nl80211: Supported cipher 00-0f-ac:2
nl80211: Supported cipher 00-0f-ac:4
nl80211: Supported cipher 00-0f-ac:6
nl80211: Using driver-based off-channel TX
nl80211: Use separate P2P group interface (driver advertised support)
nl80211: interface wlan0 in phy phy0
nl80211: Set mode ifindex 3 iftype 3 (AP)
nl80211: Setup AP(wlan0) - device_ap_sme=0 use_monitor=0
nl80211: Subscribe to mgmt frames with AP handle 0x14e8790
nl80211: Register frame type=0xb0 nl_handle=0x14e8790 match=
nl80211: Register frame type=0x0 nl_handle=0x14e8790 match=
nl80211: Register frame type=0x20 nl_handle=0x14e8790 match=
nl80211: Register frame type=0xa0 nl_handle=0x14e8790 match=
nl80211: Register frame type=0xc0 nl_handle=0x14e8790 match=
nl80211: Register frame type=0xd0 nl_handle=0x14e8790 match=
nl80211: Register frame command failed (type=208): ret=-114 (Operation already in progress)
nl80211: Register frame match - hexdump(len=0): [NULL]
nl80211: Could not configure driver mode
nl80211: Remove monitor interface: refcount=0
nl80211: Remove beacon (ifindex=3)
netlink: Operstate: ifindex=3 linkmode=0 (kernel-control), operstate=6 (IF_OPER_UP)
nl80211: Set mode ifindex 3 iftype 2 (STATION)
nl80211: Teardown AP(wlan0) - device_ap_sme=0 use_monitor=0
nl80211 driver initialization failed.
hostapd_interface_deinit_free(0x14e7d90)
hostapd_interface_deinit_free: num_bss=1 conf->num_bss=1
hostapd_interface_deinit(0x14e7d90)
hostapd_bss_deinit: deinit bss wlan0
hostapd_cleanup(hapd=0x14e9100 (wlan0))
hostapd_free_hapd_data: Interface wlan0 wasn't started
hostapd_interface_deinit_free: driver=(nil) drv_priv=(nil) -> hapd_deinit
hostapd_interface_free(0x14e7d90)
hostapd_interface_free: free hapd 0x14e9100
hostapd_cleanup_iface(0x14e7d90)
hostapd_cleanup_iface_partial(0x14e7d90)
hostapd_cleanup_iface: free iface=0x14e7d90
[\spoiler]

---

