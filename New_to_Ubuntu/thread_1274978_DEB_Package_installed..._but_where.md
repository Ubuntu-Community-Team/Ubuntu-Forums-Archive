---
title: "DEB Package installed... but where?"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by CmdGabriel on 2009-09-25
I would like to add it to my main menu. But I don't find the installed application on the harddrive... oops.

I have downloaded it and the package manager installed it.

---

### Post by MelDJ on 2009-09-25
what is the package installed? 
you could go to system-preferences-main menu, then select the menu you want the package to be. then select new item. put the name of the program. then put the command which runs the program ( as you would in terminal. for example: *songbird*, *firefox.*then press ok and you will find it in the menu.:KS

---

### Post by scorp123 on 2009-09-25
> **CmdGabriel said:**
>  But I don't find the installed application on the harddrive. ```
dpkg -L nameOfpackage
```

Example ... find out where "FrostWire" put its files:

```
> dpkg -L frostwire

/.
/usr
/usr/share
/usr/share/applications
/usr/share/applications/frostwire.desktop
/usr/share/icons
/usr/share/icons/hicolor
/usr/share/icons/hicolor/48x48
/usr/share/icons/hicolor/48x48/apps
/usr/share/icons/hicolor/48x48/apps/frostwire.png
/usr/share/icons/hicolor/64x64
/usr/share/icons/hicolor/64x64/apps
/usr/share/icons/hicolor/64x64/apps/frostwire.png
/usr/share/icons/hicolor/32x32
/usr/share/icons/hicolor/32x32/apps
/usr/share/icons/hicolor/32x32/apps/frostwire.png
/usr/share/icons/hicolor/16x16
/usr/share/doc
/usr/share/doc/frostwire
/usr/share/doc/frostwire/changelog
/usr/bin
/usr/bin/frostwire
/usr/lib
/usr/lib/frostwire
/usr/lib/frostwire/root
/usr/lib/frostwire/root/magnet10
/usr/lib/frostwire/root/magnet10/options.js
/usr/lib/frostwire/root/magnet10/canHandle.img
/usr/lib/frostwire/root/magnet10/badge.img
/usr/lib/frostwire/root/magnet10/silentdetect.js
/usr/lib/frostwire/root/magnet10/limewire.gif
/usr/lib/frostwire/httpcore-nio-4.0-beta2.pack
/usr/lib/frostwire/onion-common.pack
/usr/lib/frostwire/jmdns.pack
/usr/lib/frostwire/jdic.pack
/usr/lib/frostwire/daap.pack
/usr/lib/frostwire/foxtrot.pack
/usr/lib/frostwire/jogg.pack
/usr/lib/frostwire/mp3spi.pack
/usr/lib/frostwire/themes.pack
/usr/lib/frostwire/unpack200.py
/usr/lib/frostwire/icu4j.pack
/usr/lib/frostwire/junit.pack
/usr/lib/frostwire/ProgressTabs.pack
/usr/lib/frostwire/jdic_stub.pack
/usr/lib/frostwire/FrostWire.icns
/usr/lib/frostwire/jflac.pack
/usr/lib/frostwire/jython.pack
/usr/lib/frostwire/onion-fec.pack
/usr/lib/frostwire/httpcore-4.0-beta2.pack
/usr/lib/frostwire/aopalliance.pack
/usr/lib/frostwire/clink.pack
/usr/lib/frostwire/lw-all.pack
/usr/lib/frostwire/vorbisspi.pack
/usr/lib/frostwire/jcraft.pack
/usr/lib/frostwire/log4j.pack
/usr/lib/frostwire/forms.pack
/usr/lib/frostwire/log4j.properties
/usr/lib/frostwire/jaudiotagger.pack
/usr/lib/frostwire/messages.pack
/usr/lib/frostwire/FrostWire.pack
/usr/lib/frostwire/jl.pack
/usr/lib/frostwire/guice-1.0.pack
/usr/lib/frostwire/gettext-commons.pack
/usr/lib/frostwire/commons-logging.pack
/usr/lib/frostwire/looks.pack
/usr/lib/frostwire/jorbis.pack
/usr/lib/frostwire/docs
/usr/lib/frostwire/docs/GPL.txt
/usr/lib/frostwire/docs/EULA.txt
/usr/lib/frostwire/httpcore-niossl-4.0-alpha7.pack
/usr/lib/frostwire/update.ver
/usr/lib/frostwire/libtray.so
/usr/lib/frostwire/libjdic.so
/usr/lib/frostwire/commons-codec-1.3.pack
/usr/lib/frostwire/tritonus.pack
/usr/lib/frostwire/pmf.ico
/usr/lib/frostwire/httpclient-4.0-alpha3.pack
/usr/lib/frostwire/runFrostwire.sh


```

---

### Post by gdonwallace on 2009-09-25
When you install using a .deb the installed files that run the program are generally in the directory /usr/bin or in some odd cases /usr/share.  

To find out where the program is installed you can do a search from terminal.  Choose Applications -> Accesories -> Terminal.  

Type **sudo find / -name [name of program]**

This will run the find program based on a filename starting in the root directory and search for the name that you enter.  The final part of this will accept wild cards as well.  So if you only know part of the name or are not sure how to spell the program name us an asterisk (i.e. naut*)

**locate** is also a good one to use, and does not display as much information as find.  Locate works the same way.  Type **locate [name of program]** it will search and only display the directories that have exactly what you are looking for.

---

### Post by drs305 on 2009-09-25
Other useful commands to get info about an installed package:

File locations:
```
whereis <packagename>
```
Example: whereis gimp

To find the run command:
```
which <packagename>
```
Example: which gimp

Package info:
```
apt-cache show <packagename>
```
Example: apt-cache show gimp

---

### Post by cgroza on 2009-09-25
to start it just type the name of the program in terminal...

---

### Post by CmdGabriel on 2009-09-25
Thanks to all of you. I am deeply impressed of Ubuntu and the Ubuntu community!

---

