---
title: "gPodder database locked"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by mevets on 2008-12-18
So, truthfully I am running gpodder on maemo but I think this problem could occur on the desktop as well. I shut the device down incorrectly and gpodder. I think it had a hold on the database and it never unlocked so now I get this error whenever I try to run gpodder. I posted it below

```

~ $ gpodder -m
Traceback (most recent call last):
  File "/usr/bin/gpodder", line 171, in <module>
    sys.exit( main())
  File "/usr/bin/gpodder", line 128, in main
    from gpodder import console
  File "/usr/lib/python2.5/site-packages/gpodder/console.py", line 21, in <module>
    from gpodder import download
  File "/usr/lib/python2.5/site-packages/gpodder/download.py", line 29, in <module>
    from gpodder.libgpodder import gl
  File "/usr/lib/python2.5/site-packages/gpodder/libgpodder.py", line 514, in <module>
    gl = gPodderLib()
  File "/usr/lib/python2.5/site-packages/gpodder/libgpodder.py", line 123, in __init__
    not db.setup({ 'database': os.path.join(gpodder_dir, 'database.sqlite'), 'gl': self })
  File "/usr/lib/python2.5/site-packages/gpodder/dbsqlite.py", line 58, in setup
    self.__check_schema()
  File "/usr/lib/python2.5/site-packages/gpodder/dbsqlite.py", line 143, in __check_schema
    ("channel_is_locked", "INTEGER"),
  File "/usr/lib/python2.5/site-packages/gpodder/dbsqlite.py", line 562, in upgrade_table
    cur.execute("PRAGMA table_info(%s)" % table_name)
sqlite3.OperationalError: database is locked

```

---

### Post by TylerRick on 2009-02-16
I was getting an "sqlite3.OperationalError: database is locked" error too.

It turned out that a gpodder process was still running in the background even though I couldn't see it.

If this happens to anyone else, you can use the lsof command to see which process has the database open:

```
> lsof ~/.config/gpodder/database.sqlite-journal 
COMMAND  PID  USER   FD   TYPE DEVICE  SIZE    NODE NAME
python  1547 tyler   10u   REG    8,7 22184 1247668 /home/tyler/.config/gpodder/database.sqlite-journal
```

In my case it was process 1547 so I just did kill 1547 (ps 1547 first to see what the process was) and the lock was released.

I've read elsewhere that you can also try deleting the journal file, but fortunately this other approach worked for me and it seemed safer.

---

