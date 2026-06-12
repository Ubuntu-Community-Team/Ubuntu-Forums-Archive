---
title: "Firefox/Gwibber won't start"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by Chris1274 on 2010-08-04
I'm having a strange problem since the most recent update. When I try to start Firefox, I get the "starting Firefox" indicator in my panel, but it never opens up. Same when I try to start Gwibber. When I tried opening Gwibber from the terminal, here's what I get:
```
** (gwibber:4128): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:4128): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:4128): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/4343
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/4343/fd'
ERROR:root:Starting couchdb failed on try 0
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID4343 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/4555
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/4555/fd'
ERROR:root:Starting couchdb failed on try 1
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID4555 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.

```
It just repeats that over and over, as if it's caught in a loop.

Any ideas as to what's going on?

---

### Post by SpockVulcan on 2010-08-07
Try reinstalling both FireFox and Gwibber from the synaptic package manager.

---

