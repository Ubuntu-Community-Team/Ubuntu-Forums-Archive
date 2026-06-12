---
title: "Locale problem with Compiz"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by locodog on 2010-12-02
I'm having problem with compiz settings. When I try to run it it show me this message:
```
(process:2659): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 100, in <module>
    import ccm
  File "/usr/lib/python2.6/dist-packages/ccm/__init__.py", line 1, in <module>
    from ccm.Conflicts import *
  File "/usr/lib/python2.6/dist-packages/ccm/Conflicts.py", line 27, in <module>
    from ccm.Constants import *
  File "/usr/lib/python2.6/dist-packages/ccm/Constants.py", line 88, in <module>
    locale.setlocale(locale.LC_ALL, "")
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

```
when i type command *locale* in console i get this output
```
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.utf8
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME=en_US_custom.UTF-8
LC_COLLATE="en_US.utf8"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=

```
after typing
```

export LC_ALL="en_US"

```
It all works fine and I can start CompizConfiguration Settings Manager, but only when in comsole I type ccsm, and ONLY while that console window is open, if i close it, and in another console type that again (ccsm) it doesn't work.
I've tried adding export LC_ALL="en_US" in startup, but it's not solution. I must everytime I want to start compiz setting manager first type in console export LC_ALL="en_US" and then ccsm. Is there a way to make LC_ALL to be "en_US" forever... I've tried everything I've found on this forum, but without results.

---

