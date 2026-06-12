---
title: "Issue in logs + notifications"
date: 2021-12-06
forum: Networking &amp; Wireless
---

### Post by alain.roger on 2021-12-06
Hello,

Today I got a warning notification that there are some issues with network.
Checking logs I can see such repetitive part:
```
déc. 06 09:54:52 PC0001 systemd[1]: Starting Network Manager Script Dispatcher Service...
déc. 06 09:54:52 PC0001 dbus-daemon[1288]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
déc. 06 09:54:52 PC0001 systemd[1]: Started Network Manager Script Dispatcher Service.
déc. 06 09:55:02 PC0001 systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
déc. 06 09:55:24 PC0001 NetworkManager[1289]: <info>  [1638780924.2573] manager: NetworkManager state is now CONNECTED_GLOBAL
déc. 06 09:55:24 PC0001 dbus-daemon[1288]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.11' (uid=0 pid=1289 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
déc. 06 09:55:24 PC0001 whoopsie[1677]: [09:55:24] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
déc. 06 09:55:24 PC0001 systemd[1]: Starting Network Manager Script Dispatcher Service...
déc. 06 09:55:24 PC0001 whoopsie[1677]: [09:55:24] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
déc. 06 09:55:24 PC0001 whoopsie[1677]: [09:55:24] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
déc. 06 09:55:24 PC0001 dbus-daemon[1288]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
déc. 06 09:55:24 PC0001 systemd[1]: Started Network Manager Script Dispatcher Service.
déc. 06 09:55:25 PC0001 whoopsie[1677]: [09:55:25] online
déc. 06 09:55:34 PC0001 systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
```

I see several issues here:
1. the time gap between messages is 9s, 10s, or 22s. Why does it take so long ?
2. Why am I getting notification as yesterday I did not get such notification ?

thx

---

