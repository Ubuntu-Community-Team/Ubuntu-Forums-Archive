---
title: "Gwibber Error"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by skymera on 2010-04-22
I'm getting this error starting Gwibber.

```
scott@scott-desktop:~$ gwibber

** (gwibber:3402): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:3402): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:3402): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
** Message: secret service operation failed: The name org.freedesktop.secrets was not provided by any .service files
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 50, in <module>
    from gwibber import client
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 3, in <module>
    import gtk, gobject, gwui, util, resources, actions, json, gconf
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 2, in <module>
    import os, json, urlparse, resources, util
  File "/usr/lib/python2.6/dist-packages/gwibber/util.py", line 2, in <module>
    from microblog.util.couch import RecordMonitor
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/util/couch.py", line 4, in <module>
    import desktopcouch, pycurl, oauth, threading, urllib, re, json
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 20, in <module>
    from desktopcouch.start_local_couchdb import process_is_couchdb, read_pidfile
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 38, in <module>
    from desktopcouch import local_files
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 297, in <module>
    xdg_base_dirs.save_config_path("desktop-couch"))
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 237, in __init__
    self.configuration = _Configuration(self)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 91, in __init__
    {'desktopcouch': 'basic'})
gnomekeyring.IOError
scott@scott-desktop:~$ 

```

Any ideas?

---

### Post by durand on 2010-04-22
Probably better to post a bug here: [https://bugs.edge.launchpad.net/gwibber/+bugs](https://bugs.edge.launchpad.net/gwibber/+bugs)

---

