---
title: "Can't launch gwibber from Applications&gt;Internet&gt;Gwibber Social Client"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by mvalviar on 2010-07-01
I'm hoping I could view tweets by launching this app. But it doesn't do anything. I ran 'gwibber' from the terminal and got this```
mvalviar@mumee:~$ gwibber

** (gwibber:10341): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:10341): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:10341): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 67, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 447, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 58, in __init__
    self.setup_ui()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 98, in setup_ui
    self.stream_view = view_class(self.model)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 340, in __init__
    self.navigation.render()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 309, in render
    small_icons=self.small_icons)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 267, in render
    self.web_settings.set_property("default-font-size", int(font_size))
ValueError: invalid literal for int() with base 10: '8.599609375'

```

As I am typing this I figured out what's wrong. It seems the gwibber developers assumed that my desktop font size is an integer value. How do I report a bug?

---

### Post by b20963a2 on 2010-07-01
> **mvalviar said:**
> How do I report a bug?

[https://bugs.launchpad.net/gwibber/+filebug](https://bugs.launchpad.net/gwibber/+filebug)

---

