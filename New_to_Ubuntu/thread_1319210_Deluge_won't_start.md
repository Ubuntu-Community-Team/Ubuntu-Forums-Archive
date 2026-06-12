---
title: "Deluge won't start"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by Falc7 on 2009-11-08
Installed deluge from PPA on karmic, here is the message in terminal

```
jamie@jamie-kubuntu:~$ deluge
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Traceback (most recent call last):
  File "/usr/bin/deluge", line 8, in <module>
    load_entry_point('deluge==1.2.0-rc3', 'console_scripts', 'deluge')()
  File "/usr/lib/pymodules/python2.6/deluge/main.py", line 121, in start_ui
    UI(options, args, options.args)
  File "/usr/lib/pymodules/python2.6/deluge/ui/ui.py", line 128, in __init__
    ui = GtkUI(args)
  File "/usr/lib/pymodules/python2.6/deluge/ui/gtkui/gtkui.py", line 193, in __init__
    self.ipcinterface = IPCInterface(args)
  File "/usr/lib/pymodules/python2.6/deluge/ui/gtkui/ipcinterface.py", line 110, in __init__
    reactor.listenUNIX(socket, self.factory, wantPID=True)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/posixbase.py", line 315, in listenUNIX
    p.startListening()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/unix.py", line 71, in startListening
    if not self.lockFile.lock():
  File "/usr/lib/python2.6/dist-packages/twisted/python/lockfile.py", line 147, in lock
    kill(int(pid), 0)
OSError: [Errno 1] Operation not permitted
jamie@jamie-kubuntu:~$

```

---

### Post by bacardiandwatermelon on 2009-11-08
Could be related it this...
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/369123](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/369123)

---

### Post by lovinglinux on 2009-11-08
I love Deluge, but since I have switched to KDE I'm running Ktorrent and I'm very satisfied. Give it a try.

Anyway, I think you will find a solution [here](http://www.google.com/search?q=deluge+start+site%3Aubuntuforums.org)

---

### Post by Falc7 on 2009-11-10
2 questions:
What are the advantages of ktorrent?

Also, i've seen people always recommend native software for kde, what advantage does native software have considering that gnome apps run on kde and visa versa?

---

### Post by lovinglinux on 2009-11-10
> **Falc7 said:**
> 2 questions:
What are the advantages of ktorrent?

They both have pretty much the same features, but there are some things about Ktorrent that I like:

[list][*]the way you can organize groups of torrents in different tabs, while deluge has only labels. 
[*]the UPnP plugin that allows you to close the port manually after seeding, while Deluge UPnP doesn't even work for me and can't be closed manually. 
[*] Deluge Blockiist plugin doesn't seem to work very well, although I have changed the way I compile the lists since I moved to Ktorrent.
[*]the fact that you can assign a torrent to a specific group when a new torrent is detected in the watched folder.[/list]

> **Falc7 said:**
> Also, i've seen people always recommend native software for kde, what advantage does native software have considering that gnome apps run on kde and visa versa?

The major advantage for me is that you don't need to install a bunch of dependencies. This is probably not the case with Deluge, but for example when I try to install screenlets, this is the list of packages that would be installed:

```
alacarte capplets-data desktop-file-utils evolution-data-server     
  evolution-data-server-common gnome-about gnome-applets              
  gnome-applets-data gnome-control-center gnome-desktop-data          
  gnome-media gnome-media-common gnome-menus gnome-panel              
  gnome-panel-data gnome-session gnome-session-bin                    
  gnome-settings-daemon gnome-system-monitor gnome-user-guide         
  indicator-applet indicator-messages libatspi1.0-0 libcamel1.2-14    
  libcanberra-gtk-module libcanberra-gtk0 libdbusmenu-glib0           
  libdbusmenu-gtk0 libdevkit-power-gobject1 libebackend1.2-0          
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13
  libgdata-google1.2-1 libgdata1.2-1 libgnome-desktop-2-11
  libgnome-media0 libgnome-menu2 libgnome-window-settings1
  libgnomekbd-common libgnomekbd4 libgnomekbdui4 libgucharmap7
  libgweather-common libgweather1 libmetacity0 libpulse-mainloop-glib0
  libtidy-0.99-0 libunique-1.0-0 metacity metacity-common mousetweaks
  nautilus nautilus-data python-chardet python-evolution
  python-feedparser python-gmenu python-gnomeapplet
  python-gnomekeyring python-rsvg python-utidylib python-wnck
  screen-resolution-extra screenlets ubuntu-system-service
```

No way I'm going to install alacarte, nautilus, gnome-menus, gnome-panel, evolution-data-server and a bunch of other gnome stuff just to get screenlets. ;)

---

### Post by Falc7 on 2009-11-10
Ah thanks for that :) 
Sillly they make it require so many dependencies, i see no reason screenlets would require evolution packages for example

---

