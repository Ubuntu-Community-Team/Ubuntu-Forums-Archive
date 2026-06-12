---
title: "Uninstalling Software (not from repositories)"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Roger Allott on 2008-12-13
Earlier today I tried to install Google Earth. I used the following Terminal command as was recommended by a Linux blogger bod who seemed to know what he was talking about.

```
sudo wget http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin && sh GoogleEarthLinux.bin
```

All seemed OK during installation but then at the end I got an error message saying "sorry .... " (I can't remember exactly what the message was and stupidly forgot to copy/paste it into a text editor. D'OH!)

Anyway, it did enough to put an icon on my desktop as if it had installed, but when I double-click it I see the Google Earth intro screen and then ..... well, nothing at all.

I've tried finding Google Earth in my Applications>Add/Remove... list, but it's not there. So how can I uninstall the program so that I can attempt to reinstall it again some other day?

---

### Post by taurus on 2008-12-13
Look in your $HOME to see if you have a GoogleEarth (or googleearth) directory.  There should be an uninstall.sh script that you can run to uninstall it.

What's the output of this command from a terminal?

```
ls -la ~
```

An easier way to install GoogleEarth is through this guide, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

---

### Post by Roger Allott on 2008-12-13
> **taurus said:**
> Look in your $HOME to see if you have a GoogleEarth (or googleearth) directory.  There should be an uninstall.sh script that you can run to uninstall it.

Indeed there is. Is it just a case of double-clicking it and it does its stuff or do I need to run it in a Terminal window?


> **taurus said:**
> What's the output of this command from a terminal?

```
ls -la ~
```

```
stuart@stuart-laptop:~$ ls -la ~
total 24844
drwxr-xr-x 54 stuart stuart     4096 2008-12-14 01:39 .
drwxr-xr-x  4 root   root       4096 2008-12-05 04:50 ..
drwx------  3 stuart stuart     4096 2008-12-05 10:02 .adobe
drwx------  9 stuart stuart     4096 2008-12-10 14:30 .amsn
drwx------  2 stuart stuart     4096 2008-12-10 14:29 amsn_received
-rw-------  1 stuart stuart      931 2008-12-14 00:50 .bash_history
-rw-r--r--  1 stuart stuart      220 2008-12-05 04:50 .bash_logout
-rw-r--r--  1 stuart stuart     3115 2008-12-05 04:50 .bashrc
drwxr-xr-x  6 stuart stuart     4096 2008-12-11 18:41 .cache
drwxr-xr-x 11 stuart stuart     4096 2008-12-13 09:56 .config
drwx------  3 stuart stuart     4096 2008-12-05 04:54 .dbus
drwxr-xr-x  2 stuart stuart     4096 2008-12-13 16:57 Desktop
-rw-------  1 stuart stuart        2 2008-12-13 23:23 .dmrc
drwxr-xr-x  2 stuart stuart     4096 2008-12-05 04:54 Documents
drwxr-xr-x  2 stuart stuart     4096 2008-12-05 06:27 dwhelper
-rw-------  1 stuart stuart        0 2008-12-06 14:18 en_GB.UTF-8
-rw-------  1 stuart stuart       16 2008-12-05 04:54 .esd_auth
drwxr-xr-x  8 stuart stuart     4096 2008-12-05 15:20 .evolution
lrwxrwxrwx  1 stuart stuart       26 2008-12-05 04:50 Examples -> /usr/share/example-content
-rw-r--r--  1 stuart stuart  2050819 2008-12-11 17:04 Firefox_wallpaper.png
drwxr-xr-x  2 stuart stuart     4096 2008-12-10 15:56 .fontconfig
drwx------  5 stuart stuart     4096 2008-12-13 23:23 .gconf
drwx------  2 stuart stuart     4096 2008-12-14 01:39 .gconfd
drwx------  4 stuart stuart     4096 2008-12-06 02:16 .gegl-0.0
drwxr-xr-x 22 stuart stuart     4096 2008-12-11 17:14 .gimp-2.6
-rw-r-----  1 stuart stuart        0 2008-12-13 23:56 .gksu.lock
drwx------  3 stuart stuart     4096 2008-12-13 16:57 .gnome
drwx------ 12 stuart stuart     4096 2008-12-14 01:39 .gnome2
drwx------  2 stuart stuart     4096 2008-12-05 04:54 .gnome2_private
drwx------  2 stuart stuart     4096 2008-12-05 04:54 .gnupg
lrwxrwxrwx  1 stuart stuart       38 2008-12-13 16:57 googleearth -> /home/stuart/google-earth//googleearth
drwx------  5 stuart stuart     4096 2008-12-13 17:44 .googleearth
drwxr-xr-x  9 stuart stuart     4096 2008-12-13 16:57 google-earth
-rw-r--r--  1 stuart stuart 23048189 2008-11-25 08:00 GoogleEarthLinux.bin
drwx------  3 stuart stuart     4096 2008-12-11 13:59 .gphpedit
drwxr-xr-x  2 stuart stuart     4096 2008-12-13 14:31 .gstreamer-0.10
-rw-r--r--  1 stuart stuart      112 2008-12-13 23:23 .gtk-bookmarks
dr-x------  2 stuart stuart        0 2008-12-13 23:23 .gvfs
drwxr-----  2 stuart stuart     4096 2008-12-05 09:52 .hplip
-rw-------  1 stuart stuart     2768 2008-12-13 23:23 .ICEauthority
drwx------  2 stuart stuart     4096 2008-12-10 14:31 .icedteaplugin
drwxr-xr-x  2 stuart stuart     4096 2008-12-05 22:36 .icons
drwx------  3 stuart stuart     4096 2008-12-11 16:08 .kde
drwx------  3 stuart stuart     4096 2008-12-05 04:54 .local
drwx------  3 stuart stuart     4096 2008-12-13 16:57 .loki
drwx------  3 stuart stuart     4096 2008-12-05 10:02 .macromedia
drwxr-xr-x  3 stuart stuart     4096 2008-12-11 16:10 .mcop
-rw-------  1 stuart stuart       31 2008-12-11 16:10 .mcoprc
drwx------  4 stuart stuart     4096 2008-12-05 06:04 .mozilla
drwxr-xr-x  2 stuart stuart     4096 2008-12-05 04:54 Music
drwx------  5 stuart stuart     4096 2008-12-13 07:46 .mysqlgui
-rw-------  1 stuart stuart      627 2008-12-13 05:31 .mysqlnavigator.rc
drwxr-xr-x  3 stuart stuart     4096 2008-12-05 04:54 .nautilus
drwx------  3 stuart stuart     4096 2008-12-13 07:03 .openoffice.org2
drwxr-xr-x  2 stuart stuart     4096 2008-12-05 04:54 Pictures
-rw-r--r--  1 stuart stuart      675 2008-12-05 04:50 .profile
drwxr-xr-x  2 stuart stuart     4096 2008-12-05 04:54 Public
drwxr-xr-x  2 stuart stuart     4096 2008-12-05 04:55 .pulse
-rw-------  1 stuart stuart      256 2008-12-05 04:54 .pulse-cookie
drwxr-xr-x  2 stuart stuart     4096 2008-12-11 16:09 .qt
drwxr-xr-x  3 stuart stuart     4096 2008-12-12 10:39 .rapache
drwxr-xr-x  2 stuart stuart     4096 2008-12-05 13:05 .rasmol
-rw-------  1 stuart stuart      618 2008-12-10 16:26 .recently-used
-rw-------  1 stuart stuart    26520 2008-12-14 01:39 .recently-used.xbel
drwx------  4 stuart stuart     4096 2008-12-06 14:18 .screem
-rw-r--r--  1 stuart stuart        0 2008-12-05 04:56 .sudo_as_admin_successful
drwxr-xr-x  4 stuart stuart     4096 2008-12-05 13:09 .sudoku
drwxr-xr-x  2 stuart stuart     4096 2008-12-05 04:54 Templates
drwxr-xr-x  2 stuart stuart     4096 2008-12-05 22:36 .themes
drwx------  4 stuart stuart     4096 2008-12-06 02:02 .thumbnails
drwxr-xr-x  2 stuart stuart     4096 2008-12-05 10:03 .update-manager-core
drwx------  2 stuart stuart     4096 2008-12-05 04:55 .update-notifier
drwxr-xr-x  2 stuart stuart     4096 2008-12-05 04:54 Videos
drwxr-xr-x  3 stuart stuart     4096 2008-12-06 02:42 .worldwind
-rw-------  1 stuart stuart      124 2008-12-13 23:23 .Xauthority
-rw-r--r--  1 stuart stuart     4716 2008-12-14 00:55 .xsession-errors
```


> **taurus said:**
> An easier way to install GoogleEarth is through this guide, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

Ah. Thanks for that. I'll take a look there once I've uninstalled the current bad installation.

---

### Post by taurus on 2008-12-13
It's best to run it from a terminal.

---

### Post by Roger Allott on 2008-12-13
> **taurus said:**
> It's best to run it from a terminal.

OK, but bearing in mind that I'm a Linux noob, would you mind just checking what I'm about to do?

navigate to the google-earth directory by:
```
cd google-earth
```

From there, simply type:
```
sudo uninstall
```

Does that look OK to you or do I need some prefix and/or suffix appendages to the uninstall command?

---

### Post by taurus on 2008-12-13
No need to include the sudo in this case since you only installed it to your $HOME.

---

### Post by Roger Allott on 2008-12-13
Well I seem to have made a boo-boo then, because this is what happens:

```
stuart@stuart-laptop:~/google-earth$ uninstall
bash: uninstall: command not found
```

But there's definitely a file in my google-earth directory called 'uninstall'.

---

### Post by taurus on 2008-12-13
The reason you get that error message because the current directory is not in your path.  So, run it like

```
./uninstall
```

---

### Post by Roger Allott on 2008-12-13
Ah. That's better!

```
stuart@stuart-laptop:~/google-earth$ ./uninstall
Product: Google Earth
Installed in /home/stuart/google-earth
Uninstalling desktop menu entries...
Uninstalling mimetypes...
Google Earth has been successfully uninstalled.
```

Thanks for your help.

---

