---
title: "NetworkManager and Internet state"
date: 2020-12-03
forum: Networking &amp; Wireless
---

### Post by snoopy1978 on 2020-12-03
Hi everybody,

I'm on an up to date Ubuntu 20.10, installed on a PC with wired network connection.
At irregular intervals the NetworkManager tray icon changes to "No Internet connection". But when using Firefox or pinging google.com there are no problems, internet connection works normal:
[ATTACH=CONFIG]287504[/ATTACH]

Only some other clients (Spotify for example) seem to rely on NetworkManagers state as they stop working until NetworkManager resets to normal connection.

After some time (sometimes seconds, somtime minutes) the state turns back to fully connected and a few or some more minutes later the state is back to "No internet connection".

This is in /var/log/syslog:

```

Dec  3 17:45:54 asterix NetworkManager[945]: <info>  [1607013954.1521] manager: NetworkManager state is now CONNECTED_SITE
Dec  3 17:45:54 asterix whoopsie[1589]: [17:45:54] offline
Dec  3 17:45:54 asterix dbus-daemon[937]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.10' (uid=0 pid=945 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Dec  3 17:45:54 asterix systemd[1]: Starting Network Manager Script Dispatcher Service...
Dec  3 17:45:54 asterix dbus-daemon[937]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec  3 17:45:54 asterix systemd[1]: Started Network Manager Script Dispatcher Service.
Dec  3 17:45:55 asterix goa-daemon[2039]: goa_http_client_check() failed: 401 — Unauthorized
Dec  3 17:45:56 asterix goa-daemon[2039]: secret_password_lookup_sync() returned NULL
Dec  3 17:45:56 asterix goa-daemon[2039]: goa_http_client_check() failed: 401 — Unauthorized
Dec  3 17:45:57 asterix NetworkManager[945]: <info>  [1607013957.6957] manager: NetworkManager state is now CONNECTED_GLOBAL
Dec  3 17:45:57 asterix whoopsie[1589]: [17:45:57] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/14
Dec  3 17:45:57 asterix whoopsie[1589]: [17:45:57] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/14
Dec  3 17:45:57 asterix whoopsie[1589]: [17:45:57] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/14
Dec  3 17:45:59 asterix whoopsie[1589]: [17:45:59] online
Dec  3 17:45:59 asterix goa-daemon[2039]: goa_http_client_check() failed: 401 — Unauthorized
Dec  3 17:46:00 asterix goa-daemon[2039]: secret_password_lookup_sync() returned NULL
Dec  3 17:46:01 asterix goa-daemon[2039]: goa_http_client_check() failed: 401 — Unauthorized
Dec  3 17:46:08 asterix systemd[1]: NetworkManager-dispatcher.service: Succeeded.
Dec  3 17:46:17 asterix NetworkManager[945]: <info>  [1607013977.1527] manager: NetworkManager state is now CONNECTED_SITE
Dec  3 17:46:17 asterix whoopsie[1589]: [17:46:17] offline
Dec  3 17:46:17 asterix dbus-daemon[937]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.10' (uid=0 pid=945 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Dec  3 17:46:17 asterix systemd[1]: Starting Network Manager Script Dispatcher Service...
Dec  3 17:46:17 asterix dbus-daemon[937]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec  3 17:46:17 asterix systemd[1]: Started Network Manager Script Dispatcher Service.
Dec  3 17:46:18 asterix goa-daemon[2039]: goa_http_client_check() failed: 401 — Unauthorized
Dec  3 17:46:20 asterix goa-daemon[2039]: secret_password_lookup_sync() returned NULL
Dec  3 17:46:20 asterix goa-daemon[2039]: goa_http_client_check() failed: 401 — Unauthorized
Dec  3 17:46:24 asterix NetworkManager[945]: <info>  [1607013984.5300] manager: NetworkManager state is now CONNECTED_GLOBAL
Dec  3 17:46:24 asterix whoopsie[1589]: [17:46:24] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/14
Dec  3 17:46:24 asterix whoopsie[1589]: [17:46:24] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/14
Dec  3 17:46:24 asterix whoopsie[1589]: [17:46:24] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/14
Dec  3 17:46:25 asterix goa-daemon[2039]: goa_http_client_check() failed: 401 — Unauthorized
Dec  3 17:46:26 asterix whoopsie[1589]: [17:46:26] online
Dec  3 17:46:26 asterix goa-daemon[2039]: secret_password_lookup_sync() returned NULL
Dec  3 17:46:27 asterix goa-daemon[2039]: goa_http_client_check() failed: 401 — Unauthorized
Dec  3 17:46:35 asterix systemd[1]: NetworkManager-dispatcher.service: Succeeded.

```
Notice the switching "CONNECTED_SITE" and "CONNECTED_GLOBAL"

Why does NetworkManager think there is no internet connection despite there is obviously no problem all the time?

Thx for any hint

---

