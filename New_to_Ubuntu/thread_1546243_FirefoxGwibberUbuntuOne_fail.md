---
title: "Firefox/Gwibber/UbuntuOne fail"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by Chris1274 on 2010-08-05
Since my last update, Firefox doesn't seem to want to work, and along with it Gwibber, and my computer won't sync with Ubuntu One. When I try to start Firefox, nothing happens. When I try to start Gwibber from the terminal, I get a strange response:
```
** (gwibber:8361): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:8361): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:8361): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/8576
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/8576/fd'
ERROR:root:Starting couchdb failed on try 0
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))
RuntimeError: Couchdb PID8576 exited.  Permissions?
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
```
It seems to get caught in a loop because it keeps repeating that.

Does anyone have an idea of what might be going on?

---

