---
title: "Content Filter/Willow package fails"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by mkro on 2007-11-03
I installed "Content filter" (Willowng-gnome) from Add/remove programs in Gutsy, but I can't seem to get it started. No entries in the programs menu, and when trying console:

> 
root@seier:~# willowng
root@seier:~# willowng-config 
Traceback (most recent call last):
  File "/usr/bin/willowng-config", line 187, in <module>
    foo = MainWindow()
  File "/usr/bin/willowng-config", line 51, in __init__
    remote_object = bus.get_object('com.ubuntu.WillowNG', '/com/ubuntu/WillowNG')
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 240, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 236, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 179, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 277, in start_service_by_name
    'su', (bus_name, flags)))
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 603, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name com.ubuntu.WillowNG was not provided by any .service files
root@seier:~# apt-cache search python profiles
root@seier:~# apt-cache search python |grep -i profil
python-profiler - deterministic profiling of any Python programs
root@seier:~# /opt/willow/willow.py --config=/opt/willow/willow.conf
bash: /opt/willow/willow.py: No such file or directory


Any hints?

---

### Post by mkro on 2007-11-15
Okay, how do I find the package maintainer?  Guess I have to mail her directly.

---

### Post by veonline on 2007-12-12
you have to restart the dbus service before running willowng-config...

---

