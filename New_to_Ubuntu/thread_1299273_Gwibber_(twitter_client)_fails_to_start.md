---
title: "Gwibber (twitter client) fails to start"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-10-23
I have installed gwibber from the repo and whenever I start it by clicking on the icon in the applications menu it fails to start.

Starting it from the terminal I get the following error:
```

$ gwibber -v -d
DEBUG:root:Launched from /usr/bin
DEBUG:root:Assuming path is correct
INFO:root:No existing Gwibber session: starting...
error: duplicate REP tables used
Failure loading aff file /usr/share/myspell/dicts/en_ZA.aff
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 74, in <module>
    GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 238, in __init__
    self.indicate.set_desktop_file(resources.get_desktop_file())
TypeError: IndicateServer.set_desktop_file() argument 1 must be string, not

```

---

### Post by GDR! on 2009-10-23
[This bug]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org-dictionaries/+bug/330454") seems to be related (but not helpful in solving your issue)

---

### Post by abhiroopb on 2009-10-23
Thanks, but, you're right now solution is actually offered!

What about the end bit of my error which refers to /usr/lib/python2.6? I remember another app that had a python related error. Unfortunately, can't remember which app this was!

---

