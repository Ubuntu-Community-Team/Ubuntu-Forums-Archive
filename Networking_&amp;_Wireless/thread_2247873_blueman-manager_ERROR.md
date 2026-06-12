---
title: "blueman-manager ERROR"
date: 2014-10-11
forum: Networking &amp; Wireless
---

### Post by jhay2 on 2014-10-11
hi , i try to start blueman-manager ,but with some unknown reason it does not start 

and to know what exactly the error i try to execute it by a command line 


heres the error message

Loading configuration plugins
Using gconf config backend
_________
Load (/usr/lib/python2.7/dist-packages/blueman/main/PluginManager.py:54)
['Services', 'PulseAudioProfile'] 
ERROR:dbus.proxies:Introspect error on org.blueman.Applet:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Traceback (most recent call last):
  File "/usr/bin/blueman-manager", line 299, in <module>
    Blueman()
  File "/usr/bin/blueman-manager", line 64, in __init__
    self.Plugins.Load()
  File "/usr/lib/python2.7/dist-packages/blueman/main/PluginManager.py", line 84, in Load
    __import__(self.module_path.__name__ + ".%s" % plugin, None, None, [])
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/manager/PulseAudioProfile.py", line 12, in <module>
    if not "PulseAudio" in a.QueryPlugins():
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)


please help

---

