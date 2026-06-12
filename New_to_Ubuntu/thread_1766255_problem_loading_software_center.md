---
title: "problem loading software center"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by newcruse on 2011-05-24
I just installed ubuntu server 10.10 on my laptop Hp pavilion dv5 after which I did sudo apt-get install ubuntu Destop. Software center was installed but whenever I click to launh, it shows for few seconds on taskbar and there after disappears without loading. I tried to remove and re-install using synaptic but that didnt change anything. When I tried sudo software center; this is the error message I got:

Traceback (most recent call last):
  File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 145, in __init__
    self.history = get_apt_history()
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 178, in get_apt_history
    apt_history = AptHistory()
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 83, in __init__
    self.rescan()
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 98, in rescan
    self._scan(history_gz_file)
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 116, in _scan
    trans = Transaction(stanza)
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 59, in __init__
    "%Y-%m-%d  %H:%M:%S")
  File "/usr/lib/python2.6/_strptime.py", line 270, in <module>
    _TimeRE_cache = TimeRE()
  File "/usr/lib/python2.6/_strptime.py", line 188, in __init__
    self.locale_time = LocaleTime()
  File "/usr/lib/python2.6/_strptime.py", line 70, in __init__
    self.lang = _getlang()
  File "/usr/lib/python2.6/_strptime.py", line 29, in _getlang
    return locale.getlocale(locale.LC_TIME)
  File "/usr/lib/python2.6/locale.py", line 497, in getlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.6/locale.py", line 410, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: en_NG

Can somebody assist?

Rgs,
Newcruse

---

### Post by jtarin on 2011-05-24
When you chose remove in Synaptic did you choose "Remove Completely" or words to that effect or just "remove"?
Use Synaptic to reinstall "app-install-data".
[And another fix.]("http://ubuntuforums.org/showthread.php?t=1635664")

---

### Post by newcruse on 2011-05-24
Thanks for response. I have done a complete removal & re-installation of both software-center and app-install-data yet the prob persists. The error localename is repeated can we deduce solution from the error, someone pls help:.

Traceback (most recent call last):
  File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 145, in __init__
    self.history = get_apt_history()
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 178, in get_apt_history
    apt_history = AptHistory()
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 83, in __init__
    self.rescan()
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 98, in rescan
    self._scan(history_gz_file)
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 116, in _scan
    trans = Transaction(stanza)
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 59, in __init__
    "%Y-%m-%d  %H:%M:%S")
  File "/usr/lib/python2.6/_strptime.py", line 270, in <module>
    _TimeRE_cache = TimeRE()
  File "/usr/lib/python2.6/_strptime.py", line 188, in __init__
    self.locale_time = LocaleTime()
  File "/usr/lib/python2.6/_strptime.py", line 70, in __init__
    self.lang = _getlang()
  File "/usr/lib/python2.6/_strptime.py", line 29, in _getlang
    return locale.getlocale(locale.LC_TIME)
  File "/usr/lib/python2.6/locale.py", line 497, in getlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.6/locale.py", line 410, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: en_NG

---

### Post by jtarin on 2011-05-24
Did you try the last link I gave you?

---

### Post by garycahill on 2011-05-24
I would head for the command line and try "apt-get install PACKAGE".

gary

---

