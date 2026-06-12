---
title: "wireless causes my HP dv2510 to crash."
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by elsatani on 2007-11-08
Very often my laptop completely freezes. As far as I can tel the wirelesscard/driver is the reason for this. I have copied the log for the time when the crash is. I need to restart the computer in order to make it work. Cursor and everything freezes..

Does any of you bright minds got a clue on how to fix this problem? It is starting to annoy me so much that (god forbid) I might need to return to windows :(



Kernel.log
```
Nov  8 19:45:15 twoduo kernel: [ 7528.396000] NVRM: Xid (0001:00): 8, Channel 00000003
Nov  8 19:45:16 twoduo kernel: [ 7529.648000] ipw3945: Error sending cmd #07 to daemon: time out after 500ms.
Nov  8 19:45:18 twoduo kernel: [ 7531.248000] ipw3945: Error sending SCAN_ABORT_CMD: time out after 500ms.
Nov  8 19:45:19 twoduo kernel: [ 7531.748000] ipw3945: Error sending cmd #08 to daemon: time out after 500ms.
Nov  8 19:45:19 twoduo kernel: [ 7532.248000] ipw3945: Error sending ADD_STA: time out after 500ms.
Nov  8 19:45:20 twoduo kernel: [ 7532.748000] ipw3945: Error sending SCAN_ABORT_CMD: time out after 500ms.
Nov  8 19:45:23 twoduo kernel: [ 7536.448000] NVRM: Xid (0001:00): 30,  L1 -> L0
Nov  8 19:45:23 twoduo kernel: [ 7536.448000] ipw3945: Microcode SW error detected.  Restarting.
Nov  8 19:45:24 twoduo kernel: [ 7536.948000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
Nov  8 19:45:24 twoduo kernel: [ 7537.448000] ipw3945: Error sending ADD_STA: time out after 500ms.
Nov  8 19:45:25 twoduo kernel: [ 7537.948000] ipw3945: Error sending RATE_SCALE: time out after 500ms.
Nov  8 19:45:39 twoduo kernel: [ 7544.448000] NVRM: Xid (0001:00): 8, Channel 00000001
Nov  8 19:45:39 twoduo kernel: [ 7552.472000] NVRM: Xid (0001:00): 30,  L1 -> L0
Nov  8 19:45:39 twoduo kernel: [ 7552.500000] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00001314 00000207 00000040
Nov  8 19:45:39 twoduo kernel: [ 7552.504000] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00001314 00000207 00000000
Nov  8 19:45:43 twoduo kernel: [ 7556.560000] NVRM: Xid (0001:00): 30,  L0 -> L0
Nov  8 19:45:43 twoduo kernel: [ 7556.580000] NVRM: Xid (0001:00): 13, 0001 00000000 0000502d 00000214 00008000 00000100
```


syslog
```
Nov  8 19:45:15 twoduo kernel: [ 7528.396000] NVRM: Xid (0001:00): 8, Channel 00000003
Nov  8 19:45:16 twoduo kernel: [ 7529.648000] ipw3945: Error sending cmd #07 to daemon: time out after 500ms.
Nov  8 19:45:18 twoduo kernel: [ 7531.248000] ipw3945: Error sending SCAN_ABORT_CMD: time out after 500ms.
Nov  8 19:45:19 twoduo kernel: [ 7531.748000] ipw3945: Error sending cmd #08 to daemon: time out after 500ms.
Nov  8 19:45:19 twoduo kernel: [ 7532.248000] ipw3945: Error sending ADD_STA: time out after 500ms.
Nov  8 19:45:20 twoduo kernel: [ 7532.748000] ipw3945: Error sending SCAN_ABORT_CMD: time out after 500ms.
Nov  8 19:45:23 twoduo kernel: [ 7536.448000] NVRM: Xid (0001:00): 30,  L1 -> L0
Nov  8 19:45:23 twoduo kernel: [ 7536.448000] ipw3945: Microcode SW error detected.  Restarting.
Nov  8 19:45:23 twoduo NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable
Nov  8 19:45:23 twoduo NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable
Nov  8 19:45:24 twoduo kernel: [ 7536.948000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
Nov  8 19:45:24 twoduo kernel: [ 7537.448000] ipw3945: Error sending ADD_STA: time out after 500ms.
Nov  8 19:45:25 twoduo kernel: [ 7537.948000] ipw3945: Error sending RATE_SCALE: time out after 500ms.
Nov  8 19:45:25 twoduo NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable
Nov  8 19:45:39 twoduo last message repeated 7 times
Nov  8 19:45:39 twoduo kernel: [ 7544.448000] NVRM: Xid (0001:00): 8, Channel 00000001
Nov  8 19:45:39 twoduo kernel: [ 7552.472000] NVRM: Xid (0001:00): 30,  L1 -> L0
Nov  8 19:45:39 twoduo kernel: [ 7552.500000] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00001314 00000207 00000040
Nov  8 19:45:39 twoduo kernel: [ 7552.504000] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00001314 00000207 00000000
Nov  8 19:45:43 twoduo kernel: [ 7556.560000] NVRM: Xid (0001:00): 30,  L0 -> L0
Nov  8 19:45:43 twoduo NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable
Nov  8 19:45:43 twoduo NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable
Nov  8 19:45:43 twoduo NetworkManager: <info>  eth1: link timed out.
Nov  8 19:45:43 twoduo NetworkManager: <info>  SWITCH: found better connection 'eth1/SpeedTouch8BC9E9' than current connection 'eth1/SpeedTouch8BC9E9'.  same_ssid=1, have_link=0
Nov  8 19:45:43 twoduo NetworkManager: <info>  Will activate connection 'eth1/SpeedTouch8BC9E9'.
Nov  8 19:45:43 twoduo NetworkManager: <info>  Device eth1 activation scheduled...
Nov  8 19:45:43 twoduo NetworkManager: <info>  Deactivating device eth1.
Nov  8 19:45:43 twoduo dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6045
Nov  8 19:45:43 twoduo dhclient: killed old client process, removed PID file
Nov  8 19:45:43 twoduo kernel: [ 7556.580000] NVRM: Xid (0001:00): 13, 0001 00000000 0000502d 00000214 00008000 00000100
```


Many thanx for any help :)

---

