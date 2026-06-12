---
title: "miro doesn't open"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by libihero on 2010-07-21
miro used to crash with me on playback, so i started fooling around with it (reinstalling, remove purging, installing, deleting all miro files and installing).  now when i install it, it wont open.  this is the output in the terminal i get

```
Traceback (most recent call last):
  File "/usr/bin/miro.real", line 116, in <module>
    gtcache.init()
  File "/usr/lib/pymodules/python2.6/miro/gtcache.py", line 68, in init
    _gt.bindtextdomain("miro", config.get(prefs.GETTEXT_PATHNAME))
  File "/usr/lib/pymodules/python2.6/miro/config.py", line 89, in get
    _check_validity()
  File "/usr/lib/pymodules/python2.6/miro/config.py", line 122, in _check_validity
    load()
  File "/usr/lib/pymodules/python2.6/miro/config.py", line 65, in load
    app.configfile = AppConfig(theme)
  File "/usr/lib/pymodules/python2.6/miro/appconfig.py", line 50, in __init__
    self.default_vars = util.read_simple_config_file(app_config_path)
  File "/usr/lib/pymodules/python2.6/miro/util.py", line 104, in read_simple_config_file
    filep = open(path, "rt")
IOError: [Errno 2] No such file or directory: '/usr/share/miro/resources/app.config'

```

---

### Post by libihero on 2010-07-22
bump :(

---

### Post by lidex on 2010-07-22
Are you using ubutu repo version or local install/PPA?
Try uninstalling it again:
```
sudo apt-get purge miro miro-data gstreamer1.10-plugins-ugly
```
Now in a terminal:
```
sudo updatedb
locate miro
```
Delete everything you find - make backups first if something you need. Re-run the last 2 commands until nothing remains. Now re-install:
```
sudo aptitude install miro miro-data gstreamer1.10-plugins-ugly
```

---

