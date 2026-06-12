---
title: "Ubuntu 20.04 Wifi Disassociated / Deauth at exact 10 minute intervals"
date: 2022-01-29
forum: Networking &amp; Wireless
---

### Post by shreyaslolage on 2022-01-29
I have noticed that my wifi disconnects frequently for a few seconds. I thought it was a network issue, but when i checked the dmesg logs, i see that it happens exactly with 10 minute intervals. I cannot seem to diagnose the issue?


Can anyone help?


```
[Sat Jan 29 04:35:38 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)[Sat Jan 29 04:45:39 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 04:55:40 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 05:05:42 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 05:15:43 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 05:25:44 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 05:35:45 2022] wlp3s0: disassociated from 3c:84:6a:*:*:* (Reason: 1=UNSPECIFIED)
[Sat Jan 29 05:45:51 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 05:55:52 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 06:05:53 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 06:15:54 2022] wlp3s0: disassociated from 3c:84:6a:*:*:* (Reason: 1=UNSPECIFIED)
[Sat Jan 29 06:26:01 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 06:36:03 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 06:46:04 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 06:56:05 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 07:06:06 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 07:16:07 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 07:26:08 2022] wlp3s0: disassociated from 3c:84:6a:*:*:* (Reason: 1=UNSPECIFIED)
[Sat Jan 29 07:36:14 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 08:00:12 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 08:10:13 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 08:20:14 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 08:30:15 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 08:40:16 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 08:50:17 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 09:00:18 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 09:10:20 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 09:20:21 2022] wlp3s0: disassociated from 3c:84:6a:*:*:* (Reason: 1=UNSPECIFIED)
[Sat Jan 29 09:30:27 2022] wlp3s0: disassociated from 3c:84:6a:*:*:* (Reason: 1=UNSPECIFIED)
[Sat Jan 29 09:40:33 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 09:50:34 2022] wlp3s0: disassociated from 3c:84:6a:*:*:* (Reason: 1=UNSPECIFIED)
[Sat Jan 29 10:00:40 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 10:10:41 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 10:20:42 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 10:30:44 2022] wlp3s0: deauthenticated from 3c:84:6a:*:*:* (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[Sat Jan 29 10:40:45 2022] wlp3s0: disassociated from 3c:84:6a:*:*:* (Reason: 1=UNSPECIFIED)





```

---

### Post by praseodym on 2022-01-31
Please run the wireless script from the sticky thread and show the outputs here

---

### Post by shreyaslolage on 2022-02-02
Sorry, I am new to forums and stuff. I have done everything specified in the Sticky Thread. My wifi disconnects every 10 minutes with Reason 1 disassociated or reason 6 deauth.

> [Wed Feb  2 21:12:06 2022] wlp3s0: disassociated from 3c:84:*:*:*:* (Reason: 1=UNSPECIFIED)


Please check this pastebin as the script suggested I do this or post a tar file.
[https://pastebin.com/iVZ5NgUH](https://pastebin.com/iVZ5NgUH)


Thanks and Regards

---

### Post by praseodym on 2022-02-03
Try deactivating the power management

```
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by shreyaslolage on 2022-02-03
> 
[Thu Feb  3 22:25:58 2022] wlp3s0: associate with 3c:84:6a:**:**:** (try 1/3)
[Thu Feb  3 22:25:58 2022] wlp3s0: RX AssocResp from 3c:84:6a:**:**:** (capab=0x1011 status=0 aid=1)
[Thu Feb  3 22:25:58 2022] wlp3s0: associated
[Thu Feb  3 22:32:52 2022] wlp3s0: deauthenticating from 3c:84:6a:**:**:** by local choice (Reason: 3=DEAUTH_LEAVING)
[Thu Feb  3 22:32:53 2022] pcieport 0000:00:1c.5: AER: Multiple Corrected error received: 0000:00:1c.5
[Thu Feb  3 22:32:53 2022] pcieport 0000:00:1c.5: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
[Thu Feb  3 22:32:53 2022] pcieport 0000:00:1c.5:   device [8086:9d15] error status/mask=00000001/00002000
[Thu Feb  3 22:32:53 2022] pcieport 0000:00:1c.5:    [ 0] RxErr                 
[Thu Feb  3 22:32:53 2022] pcieport 0000:00:1c.5: AER: Multiple Corrected error received: 0000:00:1c.5
[Thu Feb  3 22:32:53 2022] pcieport 0000:00:1c.5: AER: can't find device of ID00e5
[Thu Feb  3 22:32:53 2022] pcieport 0000:00:1c.5: AER: Multiple Corrected error received: 0000:00:1c.5
[Thu Feb  3 22:32:53 2022] pcieport 0000:00:1c.5: AER: can't find device of ID00e5
[Thu Feb  3 22:32:53 2022] pcieport 0000:00:1c.5: AER: Multiple Corrected error received: 0000:00:1c.5
[Thu Feb  3 22:32:53 2022] pcieport 0000:00:1c.5: AER: can't find device of ID00e5
[Thu Feb  3 22:32:53 2022] pcieport 0000:00:1c.5: AER: Multiple Corrected error received: 0000:00:1c.5
[Thu Feb  3 22:32:53 2022] pcieport 0000:00:1c.5: AER: can't find device of ID00e5
[Thu Feb  3 22:32:53 2022] pcieport 0000:00:1c.5: AER: Multiple Corrected error received: 0000:00:1c.5
[Thu Feb  3 22:32:53 2022] pcieport 0000:00:1c.5: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
[Thu Feb  3 22:32:53 2022] pcieport 0000:00:1c.5:   device [8086:9d15] error status/mask=00002001/00002000
[Thu Feb  3 22:32:53 2022] pcieport 0000:00:1c.5:    [ 0] RxErr                 
[Thu Feb  3 22:32:58 2022] wlp3s0: authenticate with 3c:84:6a:**:**:**
[Thu Feb  3 22:32:58 2022] wlp3s0: send auth to 3c:84:6a:**:**:** (try 1/3)
[Thu Feb  3 22:32:58 2022] wlp3s0: authenticated
[Thu Feb  3 22:32:58 2022] wlp3s0: associate with 3c:84:6a:**:**:** (try 1/3)
[Thu Feb  3 22:32:58 2022] wlp3s0: RX AssocResp from 3c:84:6a:**:**:** (capab=0x1011 status=0 aid=1)
[Thu Feb  3 22:32:58 2022] wlp3s0: associated
[Thu Feb  3 22:32:58 2022] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[Thu Feb  3 22:42:58 2022] wlp3s0: disassociated from 3c:84:6a:**:**:** (Reason: 1=UNSPECIFIED)
[Thu Feb  3 22:43:04 2022] wlp3s0: authenticate with 3c:84:6a:**:**:**
[Thu Feb  3 22:43:04 2022] wlp3s0: send auth to 3c:84:6a:**:**:** (try 1/3)
[Thu Feb  3 22:43:04 2022] wlp3s0: authenticated
[Thu Feb  3 22:43:04 2022] wlp3s0: associate with 3c:84:6a:**:**:** (try 1/3)
[Thu Feb  3 22:43:04 2022] wlp3s0: RX AssocResp from 3c:84:6a:**:**:** (capab=0x1011 status=0 aid=1)
[Thu Feb  3 22:43:04 2022] wlp3s0: associated


Did not work :( Is there something more i can share? That deauth is the network manager restart i did after changing the powersave settings.

You can see again exactly 10 minutes after the successful connection it disconnected and reconnected.

---

### Post by shreyaslolage on 2022-02-03
> 
Feb 04 00:55:03 w1sd0m-Inspiron whoopsie[1425]: [00:55:03] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
Feb 04 00:55:03 w1sd0m-Inspiron whoopsie[1425]: [00:55:03] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
Feb 04 00:55:03 w1sd0m-Inspiron whoopsie[1425]: [00:55:03] online
Feb 04 00:55:13 w1sd0m-Inspiron systemd[1]: NetworkManager-dispatcher.service: Succeeded.
Feb 04 01:01:19 w1sd0m-Inspiron gnome-shell[4881]: [4947:4:0204/010119.473450:ERROR:node_controller.cc(585)] Trying to re-add dropped peer E887F84C11DF3A0C.82C457E73090852E
Feb 04 01:03:17 w1sd0m-Inspiron gnome-shell[4881]: [4947:4:0204/010317.768235:ERROR:node_controller.cc(585)] Trying to re-add dropped peer 9117EB32FD856292.F82C6F62603DCFD7
Feb 04 01:04:26 w1sd0m-Inspiron kernel: wlp3s0: disassociated from 3c:84:6a:**:**:** (Reason: 1=UNSPECIFIED)
Feb 04 01:04:26 w1sd0m-Inspiron wpa_supplicant[1059]: wlp3s0: CTRL-EVENT-DISCONNECTED bssid=3c:84:6a:**:**:** reason=1
Feb 04 01:04:26 w1sd0m-Inspiron wpa_supplicant[1059]: wlp3s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Feb 04 01:04:26 w1sd0m-Inspiron NetworkManager[55748]: <warn>  [1643916866.2856] sup-iface[0x561034fcb910,wlp3s0]: connection disconnected (reason 1)
Feb 04 01:04:26 w1sd0m-Inspiron NetworkManager[55748]: <info>  [1643916866.2914] device (wlp3s0): supplicant interface state: completed -> disconnected
Feb 04 01:04:26 w1sd0m-Inspiron NetworkManager[55748]: <info>  [1643916866.2915] device (p2p-dev-wlp3s0): supplicant management interface state: completed -> disconnected
Feb 04 01:04:26 w1sd0m-Inspiron gnome-shell[1679]: An active wireless connection, in infrastructure mode, involves no access point?
Feb 04 01:04:26 w1sd0m-Inspiron NetworkManager[55748]: <info>  [1643916866.3906] device (wlp3s0): supplicant interface state: disconnected -> scanning
Feb 04 01:04:26 w1sd0m-Inspiron NetworkManager[55748]: <info>  [1643916866.3907] device (p2p-dev-wlp3s0): supplicant management interface state: disconnected -> scanning
Feb 04 01:04:26 w1sd0m-Inspiron gnome-shell[4881]: [4875:4908:0204/010426.654984:ERROR:connection_factory_impl.cc(425)] Failed to connect to MCS endpoint with error -106
Feb 04 01:04:27 w1sd0m-Inspiron wpa_supplicant[1059]: wlp3s0: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN
Feb 04 01:04:31 w1sd0m-Inspiron wpa_supplicant[1059]: wlp3s0: SME: Trying to authenticate with 3c:84:6a:**:**:** (SSID='Tz_5G' freq=5180 MHz)
Feb 04 01:04:31 w1sd0m-Inspiron kernel: wlp3s0: authenticate with 3c:84:6a:**:**:**
Feb 04 01:04:31 w1sd0m-Inspiron kernel: wlp3s0: send auth to 3c:84:6a:**:**:** (try 1/3)
Feb 04 01:04:31 w1sd0m-Inspiron kernel: wlp3s0: authenticated
Feb 04 01:04:31 w1sd0m-Inspiron NetworkManager[55748]: <info>  [1643916871.2634] device (wlp3s0): supplicant interface state: scanning -> authenticating
Feb 04 01:04:31 w1sd0m-Inspiron NetworkManager[55748]: <info>  [1643916871.2635] device (p2p-dev-wlp3s0): supplicant management interface state: scanning -> authenticating
Feb 04 01:04:31 w1sd0m-Inspiron wpa_supplicant[1059]: wlp3s0: Trying to associate with 3c:84:6a:**:**:** (SSID='Tz_5G' freq=5180 MHz)
Feb 04 01:04:31 w1sd0m-Inspiron kernel: wlp3s0: associate with 3c:84:6a:**:**:** (try 1/3)
Feb 04 01:04:31 w1sd0m-Inspiron kernel: wlp3s0: RX AssocResp from 3c:84:6a:**:**:** (capab=0x1011 status=0 aid=1)
Feb 04 01:04:31 w1sd0m-Inspiron wpa_supplicant[1059]: wlp3s0: Associated with 3c:84:6a:**:**:**
Feb 04 01:04:31 w1sd0m-Inspiron wpa_supplicant[1059]: wlp3s0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Feb 04 01:04:31 w1sd0m-Inspiron kernel: wlp3s0: associated





Herer are the sudo journalctl logs

---

