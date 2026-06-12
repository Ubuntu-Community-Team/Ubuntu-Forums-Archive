---
title: "hostapd fails during autostart"
date: 2018-08-01
forum: Networking &amp; Wireless
---

### Post by jirkarck on 2018-08-01
I have a problem with hostapd. Hostapd is not active after startup with this error log:
```
&#9679; hostapd.service - Advanced IEEE 802.11 AP and IEEE 802.1X/WPA/WPA2/EAP Authenticator
   Loaded: loaded (/lib/systemd/system/hostapd.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Wed 2018-08-01 13:58:37 CEST; 3min 13s ago
  Process: 648 ExecStart=/usr/sbin/hostapd -P /run/hostapd.pid -B $DAEMON_OPTS ${DAEMON_CONF} (code=exited, status=1/FAILURE)

Aug 01 13:58:36 incremo hostapd[648]: Configuration file: /etc/hostapd/hostapd.conf
Aug 01 13:58:37 incremo hostapd[648]: nl80211: Driver does not support authentication/association or connect commands
Aug 01 13:58:37 incremo hostapd[648]: nl80211: deinit ifname=wlp9s0 disabled_11b_rates=0
Aug 01 13:58:37 incremo hostapd[648]: nl80211 driver initialization failed.
Aug 01 13:58:37 incremo hostapd[648]: wlp9s0: interface state UNINITIALIZED->DISABLED
Aug 01 13:58:37 incremo hostapd[648]: wlp9s0: AP-DISABLED
Aug 01 13:58:37 incremo hostapd[648]: hostapd_free_hapd_data: Interface wlp9s0 wasn't started
Aug 01 13:58:37 incremo systemd[1]: hostapd.service: Control process exited, code=exited status=1
Aug 01 13:58:37 incremo systemd[1]: hostapd.service: Failed with result 'exit-code'.
Aug 01 13:58:37 incremo systemd[1]: Failed to start Advanced IEEE 802.11 AP and IEEE 802.1X/WPA/WPA2/EAP Authenticator.
```

But configuration is ok. If I restart hostapd manually (sudo service hostapd restart), it starts and I can connect to the AP.

```
&#9679; hostapd.service - Advanced IEEE 802.11 AP and IEEE 802.1X/WPA/WPA2/EAP Authenticator
   Loaded: loaded (/lib/systemd/system/hostapd.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2018-08-01 14:09:59 CEST; 39s ago
  Process: 1286 ExecStart=/usr/sbin/hostapd -P /run/hostapd.pid -B $DAEMON_OPTS ${DAEMON_CONF} (code=exited, status=0/SUCCESS)
 Main PID: 1287 (hostapd)
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/hostapd.service
           &#9492;&#9472;1287 /usr/sbin/hostapd -P /run/hostapd.pid -B /etc/hostapd/hostapd.conf

Aug 01 14:09:58 incremo systemd[1]: Starting Advanced IEEE 802.11 AP and IEEE 802.1X/WPA/WPA2/EAP Authenticator...
Aug 01 14:09:58 incremo hostapd[1286]: Configuration file: /etc/hostapd/hostapd.conf
Aug 01 14:09:59 incremo hostapd[1286]: wlp9s0: interface state UNINITIALIZED->COUNTRY_UPDATE
Aug 01 14:09:59 incremo systemd[1]: Started Advanced IEEE 802.11 AP and IEEE 802.1X/WPA/WPA2/EAP Authenticator.
Aug 01 14:10:32 incremo hostapd[1287]: wlp9s0: STA 60:57:18:91:a6:95 IEEE 802.11: authenticated
Aug 01 14:10:32 incremo hostapd[1287]: wlp9s0: STA 60:57:18:91:a6:95 IEEE 802.11: associated (aid 1)
Aug 01 14:10:32 incremo hostapd[1287]: wlp9s0: STA 60:57:18:91:a6:95 RADIUS: starting accounting session DAFA37AF216B1D72
Aug 01 14:10:32 incremo hostapd[1287]: wlp9s0: STA 60:57:18:91:a6:95 WPA: pairwise key handshake completed (RSN)

```

Where would be the problem, please? :-o

---

