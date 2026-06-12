---
title: "Systemd dbus-org.freedesktop.nm-dispatcher.service continuously reloading"
date: 2015-08-16
forum: Networking &amp; Wireless
---

### Post by Albionx on 2015-08-16
In looking at the syslog, I found the following. What I don't understand is why it continues to cycle through this every 1 minute or so. It seems to succeed when it runs, so I wonder why it gets inactive and active again.

```
Aug 16 17:20:51 midgard dbus[849]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Aug 16 17:20:51 midgard systemd[1]: Starting Network Manager Script Dispatcher Service...
Aug 16 17:20:51 midgard dbus[849]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug 16 17:20:51 midgard systemd[1]: Started Network Manager Script Dispatcher Service.
Aug 16 17:20:51 midgard nm-dispatcher: Dispatching action 'dhcp6-change' for wlan0
Aug 16 17:21:06 midgard dhclient: PRC: Renewing lease on wlan0.
Aug 16 17:21:06 midgard dhclient: XMT: Renew on wlan0, interval 9720ms.
Aug 16 17:21:06 midgard dhclient: RCV: Reply message on wlan0 from fe80::c627:95ff:fe30:d05.
Aug 16 17:21:06 midgard NetworkManager[823]: <info> (wlan0): DHCPv6 state changed renew6 -> renew6
Aug 16 17:21:06 midgard NetworkManager[823]: <info>   valid_lft 60
Aug 16 17:21:06 midgard NetworkManager[823]: <info>   preferred_lft 30
Aug 16 17:21:06 midgard NetworkManager[823]: <info>   address 2601:647:4500:770c::6
Aug 16 17:21:06 midgard NetworkManager[823]: <info>   nameserver '2001:558:feed::1'
Aug 16 17:21:06 midgard NetworkManager[823]: <info>   nameserver '2001:558:feed::2'
```

I did a bunch of systemctl status until I found the service going from active to inactive:

```
albion@midgard:~$ sudo systemctl status dbus-org.freedesktop.nm-dispatcher.service
&#9679; NetworkManager-dispatcher.service - Network Manager Script Dispatcher Service
   Loaded: loaded (/lib/systemd/system/NetworkManager-dispatcher.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2015-08-16 17:14:05 PDT; 9s ago
 Main PID: 4710 (nm-dispatcher)
   CGroup: /system.slice/NetworkManager-dispatcher.service
           &#9492;&#9472;4710 /usr/lib/NetworkManager/nm-dispatcher

Aug 16 17:14:05 midgard systemd[1]: Starting Network Manager Script Dispatcher Service...
Aug 16 17:14:05 midgard systemd[1]: Started Network Manager Script Dispatcher Service.
Aug 16 17:14:05 midgard nm-dispatcher[4710]: Dispatching action 'dhcp6-change' for wlan0
albion@midgard:~$ sudo systemctl status dbus-org.freedesktop.nm-dispatcher.service
&#9679; NetworkManager-dispatcher.service - Network Manager Script Dispatcher Service
   Loaded: loaded (/lib/systemd/system/NetworkManager-dispatcher.service; enabled; vendor preset: enabled)
   Active: inactive (dead)

Aug 16 17:13:20 midgard nm-dispatcher[4630]: Dispatching action 'dhcp6-change' for wlan0
Aug 16 17:13:35 midgard systemd[1]: Starting Network Manager Script Dispatcher Service...
Aug 16 17:13:35 midgard systemd[1]: Started Network Manager Script Dispatcher Service.
```

Unfortunately, ```
journalctl _SYSTEMD_UNIT=dbus-org.freedesktop.nm-dispatcher.service offers
``` no extra insights (nothing is logged).
Any idea on how to troubleshoot this?

---

### Post by YumaJim on 2016-06-05
I have found that Ubuntu 16.04 on my desktop is renewing the lease for eth0 for dchp6 (ip6 only)
every 10-15 seconds. See syslog data below:

Jun  5 11:23:25 powder dbus[777]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Jun  5 11:23:25 powder systemd[1]: Starting Network Manager Script Dispatcher Service...
Jun  5 11:23:25 powder dbus[777]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun  5 11:23:25 powder systemd[1]: Started Network Manager Script Dispatcher Service.
Jun  5 11:23:25 powder nm-dispatcher: req:1 'dhcp6-change' [eth0]: new request (1 scripts)
Jun  5 11:23:25 powder nm-dispatcher: req:1 'dhcp6-change' [eth0]: start running ordered scripts...
Jun  5 11:23:40 powder dhclient[1112]: PRC: Renewing lease on eth0.
Jun  5 11:23:40 powder dhclient[1112]: XMT: Renew on eth0, interval 10850ms.
Jun  5 11:23:40 powder dhclient[1112]: RCV: Reply message on eth0 from fe80::a62b:8cff:fe27:64b3.
Jun  5 11:23:40 powder NetworkManager[876]: <info>  [1465151020.3188]   valid_lft 60
Jun  5 11:23:40 powder NetworkManager[876]: <info>  [1465151020.3188]   preferred_lft 30
Jun  5 11:23:40 powder NetworkManager[876]: <info>  [1465151020.3188]   address 2600:8800:6202:6000:4637:e6ff:fe76:ed7b
Jun  5 11:23:40 powder NetworkManager[876]: <info>  [1465151020.3189]   nameserver '2001:578:3f::30'
Jun  5 11:23:40 powder NetworkManager[876]: <info>  [1465151020.3189]   nameserver '2001:578:3f:1::30'
Jun  5 11:23:40 powder NetworkManager[876]: <info>  [1465151020.3189] dhcp6 (eth0): state changed bound -> bound, event ID="e6:76:ed:7b|1465151020"
Jun  5 11:23:40 powder dbus[777]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Jun  5 11:23:40 powder systemd[1]: Starting Network Manager Script Dispatcher Service...
Jun  5 11:23:40 powder dbus[777]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun  5 11:23:40 powder systemd[1]: Started Network Manager Script Dispatcher Service.
Jun  5 11:23:40 powder nm-dispatcher: req:1 'dhcp6-change' [eth0]: new request (1 scripts)
Jun  5 11:23:40 powder nm-dispatcher: req:1 'dhcp6-change' [eth0]: start running ordered scripts...

---

### Post by navajo3460 on 2016-12-03
I'm having the same issue, continues to reload every couple of secs and this just started today. Does anyone have any answers.?

---

