---
title: "Wicd help, wont start, cant connect to internet"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Defiant Rat on 2010-01-17
So, i start up my computer and wicd dosnt start :S
When i run 
```
wicd-client -n
```
I get
```
Traceback (most recent call last):
  File "/usr/share/wicd/wicd-client.py", line 50, in <module>
    import wicd.gui as gui
  File "/usr/share/wicd/wicd/gui.py", line 2005, in <module>
    setup_dbus()
  File "/usr/share/wicd/wicd/gui.py", line 177, in setup_dbus
    proxy_obj = bus.get_object("org.wicd.daemon", '/org/wicd/daemon')
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.wicd.daemon was not provided by any .service files


```

Any ideas how to get it working again? I would be willing to switch back to network manager if it got me back on the internet, but am not sure how to install it without internet access. Can i install it from the Live CD?

Thanks.

---

