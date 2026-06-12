---
title: "Capturing verbose wpa_supplicant log on [x]ubuntu 15.04"
date: 2015-11-18
forum: Networking &amp; Wireless
---

### Post by ROBAT on 2015-11-18
I am running a completely up to date XUbuntu 15.04. I would like to capture a verbose wpa_supplicant log. I have modified */usr/share/dbus-1/system-services/fi.w1.wpa_supplicant1.service* to look like this:

```
[D-BUS Service]
Name=fi.w1.wpa_supplicant1
# Exec=/sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant
Exec=/sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -t -ddd -f /var/log/wpa_supplicant.log -O /var/run/wpa_supplicant
User=root
SystemdService=wpa_supplicant.service

```

However, I still get normal logging level output to syslog. For example, if I *tail -f /var/log/syslog | grep wpa_supplicant* and kill my wpa_supplicant process I still get the following:

```
Nov 18 11:20:57 tabor-xps-13 NetworkManager[734]: <info> wpa_supplicant stopped
Nov 18 11:20:57 tabor-xps-13 dbus[787]: [system] Activating via systemd: service name='fi.w1.wpa_supplicant1' unit='wpa_supplicant.service'
Nov 18 11:20:57 tabor-xps-13 systemd[1]: wpa_supplicant.service: main process exited, code=killed, status=9/KILL
Nov 18 11:20:57 tabor-xps-13 systemd[1]: Unit wpa_supplicant.service entered failed state.
Nov 18 11:20:57 tabor-xps-13 systemd[1]: wpa_supplicant.service failed.
Nov 18 11:20:57 tabor-xps-13 dbus[787]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Nov 18 11:20:57 tabor-xps-13 wpa_supplicant[2818]: Successfully initialized wpa_supplicant
Nov 18 11:20:57 tabor-xps-13 wpa_supplicant[2818]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Nov 18 11:20:57 tabor-xps-13 wpa_supplicant[2818]: dbus: Failed to construct signal
Nov 18 11:20:57 tabor-xps-13 NetworkManager[734]: <info> wpa_supplicant started
Nov 18 11:20:57 tabor-xps-13 wpa_supplicant[2818]: wlan3: CTRL-EVENT-SCAN-STARTED
Nov 18 11:20:59 tabor-xps-13 wpa_supplicant[2818]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Nov 18 11:20:59 tabor-xps-13 wpa_supplicant[2818]: wlan3: SME: Trying to authenticate with 2c:41:38:f5:3a:e3 (SSID='rand10' freq=5200 MHz)
Nov 18 11:20:59 tabor-xps-13 wpa_supplicant[2818]: wlan3: Trying to associate with 2c:41:38:f5:3a:e3 (SSID='rand10' freq=5200 MHz)
Nov 18 11:20:59 tabor-xps-13 wpa_supplicant[2818]: wlan3: Associated with 2c:41:38:f5:3a:e3
Nov 18 11:20:59 tabor-xps-13 wpa_supplicant[2818]: wlan3: WPA: Key negotiation completed with 2c:41:38:f5:3a:e3 [PTK=CCMP GTK=CCMP]
Nov 18 11:20:59 tabor-xps-13 wpa_supplicant[2818]: wlan3: CTRL-EVENT-CONNECTED - Connection to 2c:41:38:f5:3a:e3 completed [id=0 id_str=]
Nov 18 11:21:07 tabor-xps-13 NetworkManager[734]: <info> wpa_supplicant die count reset

```

I'm not very familiar with systemd or NetworkManager, any help is greatly appreciated.

---

