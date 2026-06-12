---
title: "Wicd does not work on Ubuntu 13.10 mininal"
date: 2013-10-26
forum: Networking &amp; Wireless
---

### Post by wsxadf on 2013-10-26
Hello,

I recently am having problem with Wicd in my newly installed Ubuntu 13.10 minimal installation. It worked very well on previous 13.04. So I think the problem resides only on this new version. I first had problem with wicd-daemon, but I fixed it using
```

[COLOR=#333333][FONT=Ubuntu Mono]rm /etc/resolv.conf[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]ln -s /run/resolvconf[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]/resolv.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]conf[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]rm /var/lib/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]wicd/resolv.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]conf.orig[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]ln -s /run/resolvconf[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]/resolv.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]conf /var/lib/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]wicd/resolv.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]conf.orig[/FONT][/COLOR]

```
the command that I found in this thread: [https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/1132529](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/1132529). Seems like the new Ubuntu has resolv.conf file in different location compared to that of previous Ubuntu.

But I am still having a problem with wicd-curses and wicd-client. It is producing following error:
```

user@user:/etc/init.d$ wicd-curses
Can't connect to the daemon, trying to start it automatically...
Traceback (most recent call last):
  File "/usr/share/wicd/curses/wicd-curses.py", line 1043, in <module>
    setup_dbus()
  File "/usr/share/wicd/curses/wicd-curses.py", line 1031, in setup_dbus
    dbus_ifaces = dbusmanager.get_dbus_ifaces()
  File "/usr/lib/python2.7/dist-packages/wicd/dbusmanager.py", line 36, in get_dbus_ifaces
    return DBUS_MANAGER.get_dbus_ifaces()
  File "/usr/lib/python2.7/dist-packages/wicd/dbusmanager.py", line 62, in get_dbus_ifaces
    if not self._dbus_ifaces: connect_to_dbus()
  File "/usr/lib/python2.7/dist-packages/wicd/dbusmanager.py", line 48, in connect_to_dbus
    return DBUS_MANAGER.connect_to_dbus()
  File "/usr/lib/python2.7/dist-packages/wicd/dbusmanager.py", line 79, in connect_to_dbus
    proxy_obj = self._bus.get_object("org.wicd.daemon", '/org/wicd/daemon')
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.wicd.daemon was not provided by any .service files

```

Wicd daemon is running. and Dbus is also running too

```

user@user:/etc/init.d$ sudo wicd start
It seems like the daemon is already running.
If it is not, please remove /var/run/wicd/wicd.pid and try again.


```

When I run service command, I get

```

user@user:/etc/init.d$ sudo service wicd start
wicd: unrecognized service
user@user:/etc/init.d$ sudo service dbus start
start: Job is already running: dbus

```


My guess is that dbus or wicd daemon is not correctly connected to the service program. Reinstalling is not working for me, and I hope to gain some insight or direction so that I can figure this problem out.

Thanks in advance!

---

### Post by wsxadf on 2013-11-08
Could anyone help me on this please?

I am instead using wpa_supplicant for now, but It will be really nice If i can run wicd back!

---

