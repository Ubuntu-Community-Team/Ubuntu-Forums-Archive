---
title: "problem whith deluge bittorrent client"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by Ramo666 on 2007-10-26
The problem still only in user session but works fine in root session after an accidental reboot i have this message :
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Traceback (most recent call last):
  File "/usr/bin/deluge", line 121, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 109, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 54, in __init__
    common.CONFIG_DIR)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 262, in __init__
    self.state = pickle.load(pkl_file)
EOFError
i have reinstalled deluge in dual mode but no result please help 
i love this bittorrent client i don't want use other

---

### Post by spd106 on 2007-10-26
You've probably got corrupted config files, I recommend you delete the contents of your ~/.config/deluge/ directory. 

This means you'll lose some settings and you will have to restart any torrents you were in the middle of, but you shouldn't lose any data files.

---

### Post by Zone17 on 2007-10-26
I also have a problem with Deluge not loading. I have tried everything, please help.

> zone@zone-laptop:~$ rm -Rf ~/.config/deluge/


> zone@zone-laptop:~$ deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG value: 1
Applying preferences
/usr/lib/python2.5/site-packages/deluge/core.py:782: DeprecationWarning: integer argument expected, got float
  PREF_FUNCTIONS[pref](self.get_pref(pref))
Scanning plugin dir /usr/share/deluge/plugins
Loading module SpeedLimiter
Initialising plugin SpeedLimiter
Loading module Locations
Initialising plugin Locations
Loading module BlocklistImport
Initialising plugin BlocklistImport
Loading module TorrentPeers
Initialising plugin TorrentPeers
Loading module ExtraStats
Initialising plugin ExtraStats
Loading module NetworkGraph
Initialising plugin NetworkGraph
Loading module ExamplePlugin
Initialising plugin ExamplePlugin
Loading module TorrentNotification
Initialising plugin TorrentNotification
Loading module DesiredRatio
Initialising plugin DesiredRatio
Loading module TorrentPieces
Initialising plugin TorrentPieces
Loading module NetworkHealth
Initialising plugin NetworkHealth
Loading module TorrentCreator
Initialising plugin TorrentCreator
Loading module TorrentSearch
Initialising plugin TorrentSearch
Loading module TorrentFiles
Traceback (most recent call last):
  File "/usr/bin/deluge", line 140, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 127, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/usr/lib/python2.5/site-packages/deluge/interface.py", line 65, in __init__
    self.plugins.scan_for_plugins()
  File "/usr/lib/python2.5/site-packages/deluge/plugins.py", line 60, in scan_for_plugins
    mod = __import__(modname, globals(), locals(), [''])
  File "/usr/share/deluge/plugins/TorrentFiles/__init__.py", line 38, in <module>
    from TorrentFiles.tab_files import FilesTabManager
  File "/usr/share/deluge/plugins/TorrentFiles/tab_files.py", line 6, in <module>
    from deluge.files import FilesBaseManager
ImportError: No module named files


---

### Post by Zone17 on 2007-10-26
I having been essing with it more and now this is what I get.

> zone@zone-laptop:~$ deluge
Traceback (most recent call last):
  File "/usr/bin/deluge", line 45, in <module>
    import deluge._dbus as dbus
ImportError: No module named _dbus


---

### Post by craigforceone on 2007-11-03
I cant seem to delete completed torrents, i know this is probably a stupid thing to ask but i really like deluge other than this can anyone help

---

