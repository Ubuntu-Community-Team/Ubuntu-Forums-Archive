---
title: "Exaile Launch Problems"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by thePowerworks on 2010-02-16
Exaile will not start. When I try to run it I get the following error: 

> INFO    : Loading Exaile 0.3.0.1...
INFO    : Loading settings...
INFO    : Setting up deferred idle manager function...
INFO    : Loading plugins...
INFO    : Loading collection...
Traceback (most recent call last):
  File "/usr/lib/exaile/exaile.py", line 56, in <module>
    main()
  File "/usr/lib/exaile/exaile.py", line 53, in main
    exaile = main.Exaile()
  File "/usr/lib/exaile/xl/main.py", line 90, in __init__
    self.__init()
  File "/usr/lib/exaile/xl/main.py", line 157, in __init
    location=os.path.join(xdg.get_data_dirs()[0], 'queue.state') )
  File "/usr/lib/exaile/xl/player/queue.py", line 51, in __init__
    self.load_from_location(location)
  File "/usr/lib/exaile/xl/playlist.py", line 832, in load_from_location
    locs.append(line.decode('utf-8').strip())
  File "/usr/lib/python2.6/encodings/utf_8.py", line 16, in decode
    return codecs.utf_8_decode(input, errors, True)
UnicodeDecodeError: 'utf8' codec can't decode byte 0xfe in position 98: unexpected code byte


Any ideas of what could be wrong? I can't see to find a .exaile/ file in my home directory. I had a huge collect so recovery would be helpful. 

Thanks.

---

### Post by Flimm on 2010-02-16
> **thePowerworks said:**
> Any ideas of what could be wrong? I can't see to find a .exaile/ file in my home directory. I had a huge collect so recovery would be helpful. 
I'm not sure what's wrong, but I can tell why you can't find a .exaile directory in ~/. Exaile follows XDG Freedesktop standards: it stores configuration details in ~/.config/exaile and user data in ~/.local/share/exaile
You might want to try deleting those after backing them up.

---

### Post by thePowerworks on 2010-02-16
After removing the folder exaile will start if I run it with sudo. It will not run normally as it once did.

I should mention I changed my user password before this started. 

Also my battery completely died while exaile was open.

Not sure if either situation is relevant. 

Thanks!

EDIT:

Sorry, forgot to paste output:

> Traceback (most recent call last):
  File "/usr/lib/exaile/exaile.py", line 56, in <module>
    main()
  File "/usr/lib/exaile/exaile.py", line 53, in main
    exaile = main.Exaile()
  File "/usr/lib/exaile/xl/main.py", line 77, in __init__
    self.setup_logging()
  File "/usr/lib/exaile/xl/main.py", line 266, in setup_logging
    mode='a', backupCount=5)
  File "/usr/lib/python2.6/logging/handlers.py", line 107, in __init__
    BaseRotatingHandler.__init__(self, filename, mode, encoding, delay)
  File "/usr/lib/python2.6/logging/handlers.py", line 59, in __init__
    logging.FileHandler.__init__(self, filename, mode, encoding, delay)
  File "/usr/lib/python2.6/logging/__init__.py", line 819, in __init__
    StreamHandler.__init__(self, self._open())
  File "/usr/lib/python2.6/logging/__init__.py", line 838, in _open
    stream = open(self.baseFilename, self.mode)
IOError: [Errno 13] Permission denied: '/home/donald/.config/exaile/exaile.log'


---

### Post by lmihaila on 2010-03-11
When I try to start Exaile it doesn't work and I get a slightly different output:
File "/usr/lib/exaile/exaile.py", line 56, in <module>
    main()
  File "/usr/lib/exaile/exaile.py", line 51, in main
    from xl import main
  File "/usr/lib/exaile/xl/main.py", line 39, in <module>
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.6/locale.py", line 515, in setlocale
    return _setlocale(category, locale)

This might have something to do with the change I did in the Ubuntu calendar in order to make it European, to start the week on Monday, but I didn't figured it out yet.

While installing Exaile, it said:

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LC_TIME = "en_US_custom.UTF-8",
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/usr/bin/mandb: can't set the locale; make sure $LC_* and $LANG are correct

---

