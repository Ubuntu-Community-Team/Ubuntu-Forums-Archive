---
title: "Deluge - No GUI?"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by ehderube on 2009-05-01
Hi,

I just upgraded to jaunty (9.04) from 8.10 and for some reason every time I start deluge I see it load in the system monitor but no gui comes up.  I went into the terminal window and typed deluge -u gtk and it replied back with 1.1.7 but no GUI after reload.  I have uninstalled and reinstalled several different ways (synaptic, downloading source and compiling) hoping that would help without any luck.  Any ideas?

Thanks,Ed

---

### Post by CA_Warren on 2009-05-01
This may sound simple, but sometimes this stuff bites: did you install the 'deluge - 1.1.6...' package, or did you install the 'deluge-console...' package? Only the former comes with the UI. Go through a package manager/apt (as opposed to compiling it yourself) to make sure all of the dependencies are there.

---

### Post by ehderube on 2009-05-01
I installed the one with the gtk+ UI and its 1.1.7 I have installed.
So in the package manager I have:

deluge
deluge-common
deluge-core 

I do not have the following packages installed:
deluge-torrent
deluge-console
deluge-webui

---

### Post by Xero Xenith on 2009-05-01
Try just typing "deluge" and hit enter - tell us what happens?

---

### Post by ehderube on 2009-05-01
Ok ran deluge in terminal and the only output is 1.1.7, it basically hangs up there (cursor flash on the line before) and takes 50% of my CPU, I let it run for 3 minutes then killed it.  No UI.

---

### Post by lovinglinux on 2009-05-02
If you were using the Blocklist plugin, then delete ~/.config/deluge/blocklist.cache and see if it helps. If this is not the case, then you could try to delete all the contents of ~/.config/deluge/. You will loose settings, current torrent list, torrents state and plugins manually installed. So back it up first to see if this is the problem.

---

### Post by detroit/zero on 2009-05-02
You might want to take a look in your notification area. Sometimes, deluge will start in a minimized state and the only indication it's there is the deluge icon in your panel.

From there, it's a matter of right-clicking the icon and selecting 'show deluge'. Then, you can enter the preferences dialog and change the behavior so it doesn't start in a minimized state.

---

### Post by ehderube on 2009-05-02
Lovinglinux,

I already tried deleting ~/.config/deluge with no success

detroit/zero,

I am running the AWN manager and an icon does not show up in the tray so there is nothing to right click and hit show.

---

### Post by lovinglinux on 2009-05-02
> **ehderube said:**
> Lovinglinux,

I already tried deleting ~/.config/deluge with no success

Do you have rules for firewall (iptables) enabled? I have experienced some issues with Deluge because of the firewall blocking some connection between the daemon and the gtk GUI, making it freeze when loading. So try disabling the firewall and launch Deluge to check if this is the culprit.

---

### Post by detroit/zero on 2009-05-02
[IMG]http://img86.imageshack.us/img86/2331/200905021646301280x800s.png[/IMG]

---

### Post by ehderube on 2009-05-02
lovinglinux,

Tried disabling firewall, no success

detroit/zero,

There is no icon to right click on, the only indication that deluge in loading is from the system monitor otherwise I couldn't tell if it was loading or not.  See below for graphic explanation:

[ATTACH]112208[/ATTACH]

---

### Post by blueridgedog on 2009-05-02
> **ehderube said:**
> lovinglinux,

Tried disabling firewall, no success

detroit/zero,

There is no icon to right click on, the only indication that deluge in loading is from the system monitor otherwise I couldn't tell if it was loading or not.  See below for graphic explanation:

[ATTACH]112208[/ATTACH]

I don't see any system notification icons...where is the notification area on that setup?

---

### Post by darkz_ on 2009-05-03
i have the same issue. i upgraded from 8.10 to 9.04 and noticed deluge didn't work. then i upgraded deluge (1.1.6 > 1.1.7), but that didn't change anything. when i run it in console it gives me this: ```
darkz@darkz:~$ deluge
1.1.7
/var/lib/python-support/python2.6/deluge/ui/gtkui/mainwindow.py:63: GtkWarning: gtk_toolbar_set_icon_size: assertion `icon_size != GTK_ICON_SIZE_INVALID' failed
  "glade/main_window.glade"))
/var/lib/python-support/python2.6/deluge/ui/gtkui/mainwindow.py:63: GtkWarning: Attempting to read the recently used resources file at `/home/lg/.recently-used.xbel', but the parser failed: Error reading file '/home/lg/.recently-used.xbel': Is a directory.
  "glade/main_window.glade"))

```

it's basically a torrentbox i can live without currently, so i will not change my config files and just wait out till an update


edit: it's now working. i only messed around with gtk settings. weird.

---

### Post by pheex on 2009-05-03
darkz, how did you fix the issue? I did't get it.

What do you mean by "i only messed around with gtk settings"?

---

### Post by pheex on 2009-05-03
OK, fixed by changing the GTK theme in System -> Appearance -> Customize -> "Raleigh" (others should work?) then launching deluge... Be careful about the rights in ~/.config/deluge/ too.

---

### Post by Absorbed on 2009-05-03
I'm getting a similar problem.

When I run deluge from a terminal I get this:

```
deluge
1.1.6
/var/lib/python-support/python2.6/deluge/ui/gtkui/mainwindow.py:63: GtkWarning: gtk_toolbar_set_icon_size: assertion `icon_size != GTK_ICON_SIZE_INVALID' failed
  "glade/main_window.glade"))
```

I get the same message every time I start it. Messing with the gtk settings as mentioned above didn't work for me.

---

### Post by Absorbed on 2009-05-04
Well, I haven't fixed Deluge, but I have got around the problem.

I installed KTorrent, and then opened my torrents in /home/blah/.config/deluge/state/ in KTorrent, saved the data in the same folder I was using in Deluge, and fortunately it didn't overwrite but rechecked and resumed.

---

### Post by darkz_ on 2009-05-04
well i just enabled "show icons in menus" and noticed that deluge has started. pure luck, eh

---

### Post by lovinglinux on 2009-05-04
You might want to check if you have Python 2.5 along with Python 2.6.

Check these discussions for more info:

[http://dev.deluge-torrent.org/ticket/814#comment:10](http://dev.deluge-torrent.org/ticket/814#comment:10)

[http://ubuntuforums.org/showthread.php?t=1146943&page=2](http://ubuntuforums.org/showthread.php?t=1146943&page=2)

[http://ubuntuforums.org/showthread.php?t=1148336](http://ubuntuforums.org/showthread.php?t=1148336)

---

