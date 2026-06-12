---
title: "Firefox/Gwibber/Ubuntu One failure"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by Chris1274 on 2010-08-05
[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Since my last update, Firefox doesn't seem to want to work, and along with it Gwibber, and my computer won't sync with Ubuntu One. When I try to start Firefox, nothing happens. When I try to start Gwibber from the terminal, I get a strange response:[/SIZE][/FONT][/COLOR]


```
                           [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]** (gwibber:8361): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'[/SIZE][/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]** (gwibber:8361): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'[/SIZE][/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]** (gwibber:8361): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Removing stale, deceptive pid file.[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Apache CouchDB has started, time to relax.[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]ERROR:root:Unable to find file descriptors in /proc/8576[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Traceback (most recent call last):[/SIZE][/FONT][/COLOR]
[COLOR=#000000]  [FONT=Verdana, Arial, Tahoma][SIZE=2]File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux[/SIZE][/FONT][/COLOR]
[COLOR=#000000]    [FONT=Verdana, Arial, Tahoma][SIZE=2]for dirent in os.listdir(fd_dir):[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]OSError: [Errno 2] No such file or directory: '/proc/8576/fd'[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]ERROR:root:Starting couchdb failed on try 0[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Traceback (most recent call last):[/SIZE][/FONT][/COLOR]
[COLOR=#000000]  [FONT=Verdana, Arial, Tahoma][SIZE=2]File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 251, in start_couchdb[/SIZE][/FONT][/COLOR]
[COLOR=#000000]    [FONT=Verdana, Arial, Tahoma][SIZE=2]pid, port = run_couchdb(ctx=ctx)[/SIZE][/FONT][/COLOR]
[COLOR=#000000]  [FONT=Verdana, Arial, Tahoma][SIZE=2]File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb[/SIZE][/FONT][/COLOR]
[COLOR=#000000]    [FONT=Verdana, Arial, Tahoma][SIZE=2]raise RuntimeError("Couchdb PID%d exited.  Permissions?" % (pid,))[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]RuntimeError: Couchdb PID8576 exited.  Permissions?[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Removing stale, deceptive pid file.[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Apache CouchDB has started, time to relax.[/SIZE][/FONT][/COLOR]  
```
                                   [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]It seems to get caught in a loop because it keeps repeating that.

Does anyone have an idea of what might be going on?[/SIZE][/FONT][/COLOR]

---

### Post by Chris1274 on 2010-08-05
I seem to have gotten things working again, at least with Firefox. I started it in safe-mode and uninstalled the add-ons. Now it's back up and running. I also uninstalled Gwibber and Ubuntu One but haven't yet gotten around to re-installing them yet.

Sorry about the multiple postings of this thread. I didn't realize the forum was down, I thought the problem was with my machine.

---

