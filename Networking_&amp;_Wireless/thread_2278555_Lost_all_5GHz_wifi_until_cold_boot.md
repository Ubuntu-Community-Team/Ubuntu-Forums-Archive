---
title: "Lost all 5GHz wifi until cold boot"
date: 2015-05-17
forum: Networking &amp; Wireless
---

### Post by Brandon_MacEachern on 2015-05-17
For some reason, Ubuntu 15.04 lost all 5GHz wifi completely, and nothing would return.  I tried warm rebooting, nothing, only 2.4GHz wireless SSID's showed up.  There's a few 5GHz networks in my area, but none would show up.  I ran wifi analyzer, and they were all still there (on my android phone), and verified I couild connect to mine just fine, and even my neighbors (whom we share networks in emergency situations like this for troubleshooting reasons).

So I poked through the log, and found this.

```
May 17 13:48:37 ThinkPad-W541 wpa_supplicant[937]: wlan0: CTRL-EVENT-DISCONNECTED bssid=48:f8:b3:b1:95:9c reason=4 locally_generated=1May 17 13:48:37 ThinkPad-W541 NetworkManager[801]: <warn> Connection disconnected (reason -4)
May 17 13:48:37 ThinkPad-W541 kernel: [22153.259290] cfg80211: Calling CRDA to update world regulatory domain
May 17 13:48:37 ThinkPad-W541 kernel: [22153.261033] cfg80211: World regulatory domain updated:
May 17 13:48:37 ThinkPad-W541 kernel: [22153.261036] cfg80211:  DFS Master region: unset
May 17 13:48:37 ThinkPad-W541 kernel: [22153.261037] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
May 17 13:48:37 ThinkPad-W541 kernel: [22153.261039] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
May 17 13:48:37 ThinkPad-W541 kernel: [22153.261040] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
May 17 13:48:37 ThinkPad-W541 kernel: [22153.261041] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
May 17 13:48:37 ThinkPad-W541 kernel: [22153.261042] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
May 17 13:48:37 ThinkPad-W541 kernel: [22153.261043] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
May 17 13:48:37 ThinkPad-W541 NetworkManager[801]: <info> (wlan0): supplicant interface state: completed -> disconnected
May 17 13:48:37 ThinkPad-W541 wpa_supplicant[937]: wlan0: CTRL-EVENT-SCAN-STARTED
May 17 13:48:37 ThinkPad-W541 NetworkManager[801]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May 17 13:48:53 ThinkPad-W541 NetworkManager[801]: <warn> (wlan0): link timed out.
May 17 13:48:53 ThinkPad-W541 NetworkManager[801]: <info> (wlan0): device state change: activated -> failed (reason 'ssid-not-found') [100 120 53]
May 17 13:48:53 ThinkPad-W541 NetworkManager[801]: <info> NetworkManager state is now CONNECTED_LOCAL
May 17 13:48:53 ThinkPad-W541 NetworkManager[801]: <info> NetworkManager state is now DISCONNECTED
May 17 13:48:53 ThinkPad-W541 NetworkManager[801]: <warn> Activation (wlan0) failed for connection 'HomePWN-AC5'
May 17 13:48:53 ThinkPad-W541 NetworkManager[801]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 17 13:48:53 ThinkPad-W541 NetworkManager[801]: <info> (wlan0): deactivating device (reason 'none') [0]
May 17 13:48:53 ThinkPad-W541 dbus[824]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
May 17 13:48:53 ThinkPad-W541 systemd[1]: Starting Network Manager Script Dispatcher Service...
May 17 13:48:53 ThinkPad-W541 dbus[824]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 17 13:48:53 ThinkPad-W541 systemd[1]: Started Network Manager Script Dispatcher Service.
May 17 13:48:53 ThinkPad-W541 nm-dispatcher: Dispatching action 'down' for wlan0
May 17 13:48:53 ThinkPad-W541 NetworkManager[801]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 12922
May 17 13:48:53 ThinkPad-W541 avahi-daemon[813]: Withdrawing address record for fe80::5ec5:d4ff:fede:9360 on wlan0.
May 17 13:48:53 ThinkPad-W541 avahi-daemon[813]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::5ec5:d4ff:fede:9360.
May 17 13:48:53 ThinkPad-W541 avahi-daemon[813]: Interface wlan0.IPv6 no longer relevant for mDNS.
May 17 13:48:53 ThinkPad-W541 gnome-session[1682]: (deja-dup-monitor:2674): GLib-CRITICAL **: Source ID 114 was not found when attempting to remove it
May 17 13:48:53 ThinkPad-W541 avahi-daemon[813]: Withdrawing address record for 192.168.1.235 on wlan0.
May 17 13:48:53 ThinkPad-W541 avahi-daemon[813]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.235.
May 17 13:48:53 ThinkPad-W541 avahi-daemon[813]: Interface wlan0.IPv4 no longer relevant for mDNS.
May 17 13:48:53 ThinkPad-W541 NetworkManager[801]: <info> Writing DNS information to /sbin/resolvconf
May 17 13:48:53 ThinkPad-W541 dnsmasq[1052]: setting upstream servers from DBus
May 17 13:48:53 ThinkPad-W541 gnome-session[1682]: [13104:13162:0517/134853:ERROR:get_updates_processor.cc(240)] PostClientToServerMessage() failed during GetUpdates
May 17 13:48:53 ThinkPad-W541 NetworkManager[801]: <info> Writing DNS information to /sbin/resolvconf
May 17 13:48:53 ThinkPad-W541 NetworkManager[801]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
May 17 13:48:53 ThinkPad-W541 gnome-session[1682]: [13104:13162:0517/134853:ERROR:get_updates_processor.cc(240)] PostClientToServerMessage() failed during GetUpdates
May 17 13:48:54 ThinkPad-W541 gnome-session[1682]: [13104:13162:0517/134854:ERROR:get_updates_processor.cc(240)] PostClientToServerMessage() failed during GetUpdates
May 17 13:48:55 ThinkPad-W541 gnome-session[1682]: [13104:13137:0517/134855:ERROR:connection_factory_impl.cc(366)] Failed to connect to MCS endpoint with error -106
May 17 13:48:56 ThinkPad-W541 gnome-session[1682]: [13104:13162:0517/134856:ERROR:get_updates_processor.cc(240)] PostClientToServerMessage() failed during GetUpdates
May 17 13:48:57 ThinkPad-W541 NetworkManager[801]: <info> (wlan0): supplicant interface state: scanning -> inactive
May 17 13:49:00 ThinkPad-W541 NetworkManager[801]: <info> (wlan0): supplicant interface state: inactive -> scanning
```

That seems to have shown up around the time I initially lost the network connection.

Now mind you, I could warm reboot into Windows, and the networks were fine.  Warm reboot into Ubuntu, nothing.  So I shut down completely, and performed a cold reboot, and THEN the 5Ghz wifi networks showed up again and started working.

Seems odd, I would point to a hardware fault, but Windows accessed it just fine, and this is a brand new laptop not even a month old yet..  Not sure what was different that needed a cold reboot.

I am using an Intel Corporation Wireless 7260 (rev bb) wireless controller.

---

### Post by Brandon_MacEachern on 2015-05-17
Just ran a Lenovo hardware test (Thinkpad W541), and the hardware all checks out.

---

### Post by Brandon_MacEachern on 2015-05-21
Bump.  Please someone help me on this.

---

