---
title: "Software center doesnot open"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by maqtanim on 2010-08-15
I can't open Software center from the Application menu. If I click on the Application > Software Center, the mouse pointer show a busy sign for a few seconds and after that nothing happens! But I can open Software center by using the following command

```
gksudo software-center
```

Can anyone help me to open the Software center from the Application menu? 

Thanks in advance.

---

### Post by Zorgoth on 2010-08-16
software-center can be opened as a normal user I believe.  Can you run the command "software-center" without gksudo?

---

### Post by maqtanim on 2010-08-16
> **Zorgoth said:**
> software-center can be opened as a normal user I believe.  Can you run the command "software-center" without gksudo?
Without gksudo it does not work. It shows the following output in the terminal:
```
$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 204, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 274, in _update_channel_list
    self.channels = self._get_channels()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 332, in _get_channels
    filter_required=True))
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 47, in __init__
    self._channel_icon = self._get_icon_for_channel(channel_name, channel_origin, channel_component)
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 107, in _get_icon_for_channel
    channel_icon = self._get_icon("distributor-logo")
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 133, in _get_icon
    icon = AnimatedImage(self.icons.load_icon(icon_name, self.ICON_SIZE, 0))
gio.Error: Error opening file: No such file or directory

```

---

### Post by Soul-Sing on 2010-08-16
```
/usr/bin/software-center
```?

---

### Post by maqtanim on 2010-08-18
> **leoquant said:**
> ```
/usr/bin/software-center
```?
If I donot use SUDO along with the above code then the software center does not open and shows the following output: 
```
$ /usr/bin/software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 204, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 274, in _update_channel_list
    self.channels = self._get_channels()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 332, in _get_channels
    filter_required=True))
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 47, in __init__
    self._channel_icon = self._get_icon_for_channel(channel_name, channel_origin, channel_component)
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 107, in _get_icon_for_channel
    channel_icon = self._get_icon("distributor-logo")
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 133, in _get_icon
    icon = AnimatedImage(self.icons.load_icon(icon_name, self.ICON_SIZE, 0))
gio.Error: Error opening file: No such file or directory
tanim@maqbook:~$ sudo /usr/bin/software-center
[sudo] password for tanim: 
/usr/share/software-center/softwarecenter/apt/aptcache.py:40: GtkWarning: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main_iteration()
ERROR:dbus.proxies:Introspect error on :1.171:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.169" (uid=0 pid=14571 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.171" (uid=0 pid=14600 comm="/usr/bin/python))
tanim@maqbook:~$ /usr/bin/software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 204, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 274, in _update_channel_list
    self.channels = self._get_channels()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 332, in _get_channels
    filter_required=True))
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 47, in __init__
    self._channel_icon = self._get_icon_for_channel(channel_name, channel_origin, channel_component)
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 107, in _get_icon_for_channel
    channel_icon = self._get_icon("distributor-logo")
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 133, in _get_icon
    icon = AnimatedImage(self.icons.load_icon(icon_name, self.ICON_SIZE, 0))
gio.Error: Error opening file: No such file or directory
tanim@maqbook:~$ clear

tanim@maqbook:~$ /usr/bin/software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 204, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 274, in _update_channel_list
    self.channels = self._get_channels()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 332, in _get_channels
    filter_required=True))
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 47, in __init__
    self._channel_icon = self._get_icon_for_channel(channel_name, channel_origin, channel_component)
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 107, in _get_icon_for_channel
    channel_icon = self._get_icon("distributor-logo")
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 133, in _get_icon
    icon = AnimatedImage(self.icons.load_icon(icon_name, self.ICON_SIZE, 0))
gio.Error: Error opening file: No such file or directory

```

But if i use SUDO then the software center opens.

---

### Post by xerxes0072 on 2011-08-31
Tried using  ´/usr/bin/software-center´ on the terminal,it came up and went off with this error:

/usr/share/software-center/softwarecenter/app.py:1190: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.window_main.show_all()
2011-08-31 17:25:29,922 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.7/zeitgeist/client.py', 367, 'reconnect_monitors')'
2011-08-31 17:25:29,921 - zeitgeist.client - INFO - Reconnected to Zeitgeist engine...
/usr/share/software-center/softwarecenter/SimpleGtkbuilderApp.py:50: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  gtk.main()
Segmentation fault


Please this is rely discouraging,cant install anything on my system.....I need help

---

