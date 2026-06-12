---
title: "Synaptic says I have Google Earth installed but I can't find it to run it"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by jrgonzalez on 2010-10-03
My Synaptic Package Manager tells me the following regarding Google Earth:

google-earth package

Installed Version

0.5.6.Ubuntu 2

I have looked under my Apllications menu tab and I can not find Google Earth anywhere.

Am I looking in the wrong place?

Where is my Google Earth?  :confused:

Thanks for any help that you may give me.

Ubuntu Linux rocks!   and I love it.

---

### Post by gandaran on 2010-10-03
should be in applications » internet, if it ins't try reboot the computer.

---

### Post by jrgonzalez on 2010-10-03
> **gandaran said:**
> should be in applications » internet, if it ins't try reboot the computer.

I rebooted my laptop twice, and Google Earth does not show under the Internet tab.

What should I do next. Thanks for replying and your help.

JRG

---

### Post by oldos2er on 2010-10-03
Open a terminal and enter ```
googleearth
```

---

### Post by Surkow on 2010-10-03
Start Google Earth by typing "googleearth" after pressing alt+f2 (start an application) or by typing "googleearth" in the terminal. If that works you can add a menu item yourself.

---

### Post by beew on 2010-10-03
If you really have google earth installed and somehow it doesn't show up in the menus you can create a menu launcher for it manually. Go to System > Preference > Main Menu. Choose Internet from the left panel. On the right panel click "New Item". A dialogue box will then appear for creating a new launcher.

In the box "Name" type "Google Earth" (or anything, it doesn't matter, it is just for you, not the OS).
Then in the box "Command" type "googleearth %f".  Now to add the icon to your launcher click the little box on the upper left corner and a window will open up to ask you to choose the icon you want to put on the launcher. You should be able to find "googleearth.xpm" in File System/usr/share/pixmaps. Click it and choose "open" and the icon will be added to the launcher. Now you should be able to launch Google Earth from the Panel drop down menu (Applications > Internet)
[B]
P.S.[/B] For those who are knowlegeable, what is the meaning of "%f"? I notice some applications are launched by typing its full path (and entering it in the "command" box of the launcher creation dialogue box) and sometimes just its name (presumably an alias to the full path) But sometime I find a name followed by "%f" like here. What is the meaning of "%f"? (Maybe I should start a thread on this?)

---

### Post by wojox on 2010-10-03
You have the google-earth package. You need to make it into a .deb now. Open your terminal and enter

```
make-googleearth-package --force
```

You should see a .deb package. Install that by clicking it.

You could also install it this way. [Look at #7]("http://ubuntuforums.org/showthread.php?t=1560497")

---

### Post by jrgonzalez on 2010-10-03
> **oldos2er said:**
> Open a terminal and enter ```
googleearth
```

OK. Here is what happened.

When I go to my terminal, it shows the following:
[FONT=monospace]jorge[/FONT]@ubuntu:~$

followed by a blinking cursor, where I type googleearth

and then I hit  the <enter> key.

I get the following response "command not found"

---

### Post by jrgonzalez on 2010-10-03
> **oldos2er said:**
> Open a terminal and enter ```
googleearth
```

See my response to Surkow below. Thanks for the help.

---

### Post by Hakunka-Matata on 2010-10-03
beew - Re: %f  

> P.S.  For those who are knowlegeable, what is the meaning of "%f"? I notice some applications are launched by typing its full path (and entering it in the "command" box of the launcher creation dialogue box) and sometimes just its name (presumably an alias to the full path) But sometime I find a name followed by "%f" like here. What is the meaning of "%f"? (Maybe I should start a thread on this?)
beew is online now Report Post   	Reply With Quote

Slightly off-topic perhaps............


[http://manpages.ubuntu.com/manpages/lucid/man1/xdg-desktop-icon.1.html]("http://manpages.ubuntu.com/manpages/lucid/man1/xdg-desktop-icon.1.html")

---

### Post by jcolyn on 2010-10-03
Uninstall googleearth-package then go here [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and follow instructions to enable Medibuntu.. Then ```
sudo apt-get update
```. Then open synaptic and type googleearth. It should be the first on the list check it for install then apply..

---

### Post by jrgonzalez on 2010-10-03
> **wojox said:**
> You have the google-earth package. You need to make it into a .deb now. Open your terminal and enter

```
make-googleearth-package --force
```You should see a .deb package. Install that by clicking it.

You could also install it this way. [Look at #7]("http://ubuntuforums.org/showthread.php?t=1560497")

-------------------------------------------------------------------------------------------
Thanks again for your help!

I got a very long report after going through all the percentages. (extraction and installation????)

Here is the report. I looked for anything that says  .deb and I could not find it

See below:  

jorge@ubuntu:~$ make-googleearth-package --force
--2010-10-03 16:58:58--  [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)
Resolving dl.google.com... 74.125.45.93, 74.125.45.136, 74.125.45.190, ...
Connecting to dl.google.com|74.125.45.93|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31406473 (30M) [application/octet-stream]
Saving to: `GoogleEarthLinux.bin'

100%[======================================>] 31,406,473   182K/s   in 2m 38s  

2010-10-03 17:01:36 (194 KB/s) - `GoogleEarthLinux.bin' saved [31406473/31406473]

Google Earth for GNU/Linux 5.2.1.1588
Unrecognized Google Earth version; using anyway (because of --force).
Guessed Google Earth version: 5.2.1.1588
tar: Record size = 8 blocks
./
./README.linux
./bin/
./bin/googleearth
./googleearth-icon.png
./googleearth.xpm
./linux/
./linux/xdg/
./linux/xdg/xdg-desktop-icon
./linux/xdg/xdg-desktop-menu
./linux/xdg/xdg-mime
./postinstall.sh
./preuninstall.sh
./setup.data/
./setup.data/bin/
./setup.data/bin/Linux/
./setup.data/bin/Linux/x86/
./setup.data/bin/Linux/x86/setup.gtk
./setup.data/bin/Linux/x86/setup.gtk2
./setup.data/bin/Linux/x86/uninstall
./setup.data/bin/Linux/amd64
./setup.data/bin/Linux/x86_64
./setup.data/bin/NetBSD
./setup.data/bin/OpenBSD
./setup.data/bin/FreeBSD
./setup.data/config.sh
./setup.data/locale/
./setup.data/locale/de/
./setup.data/locale/de/LC_MESSAGES/
./setup.data/locale/de/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/de/LC_MESSAGES/setup.mo
./setup.data/locale/es/
./setup.data/locale/es/LC_MESSAGES/
./setup.data/locale/es/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/es/LC_MESSAGES/setup.mo
./setup.data/locale/fr/
./setup.data/locale/fr/LC_MESSAGES/
./setup.data/locale/fr/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/fr/LC_MESSAGES/setup.mo
./setup.data/locale/it/
./setup.data/locale/it/LC_MESSAGES/
./setup.data/locale/it/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/it/LC_MESSAGES/setup.mo
./setup.data/locale/nl/
./setup.data/locale/nl/LC_MESSAGES/
./setup.data/locale/nl/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/nl/LC_MESSAGES/setup.mo
./setup.data/locale/ru/
./setup.data/locale/ru/LC_MESSAGES/
./setup.data/locale/ru/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/ru/LC_MESSAGES/setup.mo
./setup.data/locale/sv/
./setup.data/locale/sv/LC_MESSAGES/
./setup.data/locale/sv/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/sv/LC_MESSAGES/setup.mo
./setup.data/setup.glade
./setup.data/setup.gtk2.glade
./setup.data/setup.xml
./setup.data/splash.xpm
./setup.sh
./googleearth-linux-x86.tar
./googleearth-data.tar
mv: cannot stat `libcrypto.so.0.9.8': No such file or directory
mv: cannot stat `libssl.so.0.9.8': No such file or directory
Checking shlib deps: gpsbabel
Checking shlib deps: libcommon_gui.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
Checking shlib deps: libspatial.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
Checking shlib deps: libflightsim.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
Checking shlib deps: libevll.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libsgutil.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGAttrs.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libalchemyext.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGSg.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGMath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGGfx.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libspatial.so'
Checking shlib deps: libnavigate.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libauth.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_gui.so'
Checking shlib deps: libicuuc.so.38
Checking shlib deps: libalchemyext.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGMath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGAttrs.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGGfx.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
Checking shlib deps: libgeobaseutils.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libspatial.so'
Checking shlib deps: libcommon_webbrowser.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `librender.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
Checking shlib deps: libIGMath.so
Checking shlib deps: libmath.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
Checking shlib deps: libcomponentframework.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
Checking shlib deps: libQtNetwork.so.4
Checking shlib deps: libQtCore.so.4
Checking shlib deps: libbasicingest.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libfusioncommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Checking shlib deps: librender.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Checking shlib deps: libport.so
Checking shlib deps: libcommon_platform.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
Checking shlib deps: libviewsync.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libsgutil.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libspatial.so'
Checking shlib deps: libcommon.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_platform.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libfusioncommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Checking shlib deps: libicudata.so.38
Checking shlib deps: libgps.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
Checking shlib deps: liblayer.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libwmsbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_webbrowser.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `librender.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libauth.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_gui.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libwebbrowser.so'
Checking shlib deps: libIGSg.so
Checking shlib deps: libfusioncommon.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
Checking shlib deps: libgeobase.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Checking shlib deps: libIGExportCommon.so
Checking shlib deps: libauth.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libreporting.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_gui.so'
Checking shlib deps: libge_net.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libfusioncommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
Checking shlib deps: libreporting.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
Checking shlib deps: libbase.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGMath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
Checking shlib deps: googleearth-bin
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgoogleearth_free.so'
Checking shlib deps: libproj.so.0
Checking shlib deps: libgooglesearch.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Checking shlib deps: libwebbrowser.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_platform.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_webbrowser.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `librender.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_gui.so'
Checking shlib deps: libIGUtils.so
Checking shlib deps: libgdal.so.1
Checking shlib deps: libQtWebKit.so.4
Checking shlib deps: libmoduleframework.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
Checking shlib deps: libgoogleearth_free.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libsgutil.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_platform.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libreporting.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_webbrowser.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `librender.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libauth.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_gui.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libspatial.so'
Checking shlib deps: libIGOpt.so
Checking shlib deps: liblayout.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
Checking shlib deps: libinput_plugin.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
Checking shlib deps: libnss_mdns4_minimal.so.2
Checking shlib deps: libcurl.so.4
Checking shlib deps: libapiloader.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGMath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
Checking shlib deps: libwmsbase.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
Checking shlib deps: libQtGui.so.4
Checking shlib deps: libmeasure.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Checking shlib deps: libqgif.so
Checking shlib deps: libqjpeg.so
Checking shlib deps: libIGGfx.so
Checking shlib deps: libsgutil.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGAttrs.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGMath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGSg.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGGfx.so'
Checking shlib deps: libIGCore.so
Checking shlib deps: libIGAttrs.so
Checking shlib deps: libcollada.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGExportCommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGOpt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGAttrs.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libalchemyext.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGMath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGSg.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGGfx.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Checking shlib deps: libGLU.so.1
Package: googleearth
Version: 5.2.1.1588+0.5.6-1
Section: non-free/science
Priority: optional
Maintainer:  <jorge@ubuntu.ubuntu-domain>
Architecture: i386
Depends: ttf-dejavu | ttf-bitstream-vera | msttcorefonts, libc6 (>= 2.0), libc6 (>= 2.1.3), libc6 (>= 2.3), libc6 (>= 2.3.2), libc6 (>= 2.3.6-6~), libc6 (>= 2.4), libexpat1 (>= 1.95.8), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libstdc++6 (>= 4.1.1), libstdc++6 (>= 4.2.1), libx11-6, libxext6, libxrender1, zlib1g (>= 1:1.1.4), zlib1g (>= 1:1.2.0) 
Description: Google Earth, a 3D map/planet viewer
 Package built with googleearth-package.
dpkg-deb: building package `googleearth' in `./googleearth_5.2.1.1588+0.5.6-1_i386.deb'.
Success!
You can now install the package with e.g. sudo dpkg -i <package>.deb
jorge@ubuntu:~$

---

### Post by jrgonzalez on 2010-10-03
> **wojox said:**
> You have the google-earth package. You need to make it into a .deb now. Open your terminal and enter

```
make-googleearth-package --force
```You should see a .deb package. Install that by clicking it.

You could also install it this way. [Look at #7]("http://ubuntuforums.org/showthread.php?t=1560497")

I clicked on Look at #7 and most of it I could not understand.

I am a super-new newbie and most of this jargon I do not understand.

Doing stuff in the command line is like trying to speak Chinese. I get lost. This is the first "big" problem that I have encountered with Ubuntu. Before this my problems were rather small. This seems to be "huge." Specially the big report.

Do I have to do all that is in #7 or just part of it.

I really appreciate all your help.

---

### Post by wojox on 2010-10-03
Open your Home Folder and press Ctrl+H 

Look for anything google.

---

### Post by wojox on 2010-10-03
> **jrgonzalez said:**
> I clicked on Look at #7 and most of it I could not understand.

I am a super-new newbie and most of this jargon I do not understand.

Doing stuff in the command line is like trying to speak Chinese. I get lost. This is the first "big" problem that I have encountered with Ubuntu. Before this my problems were rather small. This seems to be "huge." Specially the big report.

Do I have to do all that is in #7 or just part of it.

I really appreciate all your help.

Just open a terminal and copy and paste this

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

```
sudo apt-get install googleearth
```

---

### Post by Hakunka-Matata on 2010-10-03
D> escription: Google Earth, a 3D map/planet viewer
Package built with googleearth-package.
dpkg-deb: building package `googleearth' in `./googleearth_5.2.1.1588+0.5.6-1_i386.deb'.
Success!
You can now install the package with e.g. sudo dpkg -i <package>.deb
jorge@ubuntu:~$


Jorge, install it now as described in the last lines of your terminal output. 

```
sudo dpkg -i ./googleearth_5.2.1.1588+0.5.6-1_i386.deb
```

wojox, Excuse me if I should not be contributing this last bit of code, you explained how to 'make' it.

---

### Post by alphacrucis2 on 2010-10-03
> **Hakunka-Matata said:**
> D


Jorge, install it now as described in the last lines of your terminal output. 

```
sudo dpkg -i ./googleearth_5.2.1.1588+0.5.6-1_i386.deb
```

wojox, Excuse me if I should not be contributing this last bit of code, you explained how to 'make' it.

Well I believe you have given the correct advice. The thread has got rather confused as some are telling the OP to install via medibuntu, which will get an older version. To the OP. Once you have done the sudo dpkg -i command as above you will find googleearth in the menu under internet apps. If it doesn't actually work, then remove it via ```
sudo apt-get remove googleearth
``` and try the medibuntu method. Some people do seem to have trouble with the newer version.

---

### Post by jrgonzalez on 2010-10-03
> **wojox said:**
> Open your Home Folder and press Ctrl+H 

Look for anything google.

Thanks again.

There are two icons.

One says:  googleearth_5.2.1.1588+0.5.6-1_i386.deb
(it looks like a shipping box)

The other one looks like a paper page and says:
GoogleEarthLinux.bin

Another paper page icon says:
Desktop.pgn        -----> I think this is one of my chess game. I know pgn has to do with chess.

---

### Post by jrgonzalez on 2010-10-03
> **Hakunka-Matata said:**
> D


Jorge, install it now as described in the last lines of your terminal output. 

```
sudo dpkg -i ./googleearth_5.2.1.1588+0.5.6-1_i386.deb
```wojox, Excuse me if I should not be contributing this last bit of code, you explained how to 'make' it.

More problems.

Here is the report from the terminal:

[FONT=monospace]jorge@ubuntu:~$ googleearth
googleearth: command not found
jorge@ubuntu:~$ googlearth
googlearth: command not found
jorge@ubuntu:~$ sudo dpkg -i ./googleearth_5.2.1.1588+0.5.6-1_i386.deb
[sudo] password for jorge: 
Selecting previously deselected package googleearth.
(Reading database ... 140341 files and directories currently installed.)
Unpacking googleearth (from .../googleearth_5.2.1.1588+0.5.6-1_i386.deb) ...
dpkg: dependency problems prevent configuration of googleearth:
 googleearth depends on ttf-dejavu | ttf-bitstream-vera | msttcorefonts; however:
  Package ttf-dejavu is not installed.
  Package ttf-bitstream-vera is not installed.
  Package msttcorefonts is not installed.
dpkg: error processing googleearth (--install):
 dependency problems - leaving unconfigured
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for shared-mime-info ...
Errors were encountered while processing:
 googleearth
jorge@ubuntu:~$ ^C
jorge@ubuntu:~$ ^C
jorge@ubuntu:~$ ^C
jorge@ubuntu:~$ 
[/FONT]

---

### Post by jrgonzalez on 2010-10-03
> **wojox said:**
> Just open a terminal and copy and paste this

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
``````
sudo apt-get install googleearth
```

OK. I am going to try this next. Hope it works.

Thanks again.

---

### Post by harrisonk on 2010-10-03
The problem is that googleearth requires:

ttf-dejavu ttf-bitstream-vera msttcorefonts

Run this: ```
 sudo apt-get install ttf-dejavu ttf-bitstream-vera msttcorefonts 
```

then run that install command again.

Harrison

---

### Post by jrgonzalez on 2010-10-03
> **jrgonzalez said:**
> OK. I am going to try this next. Hope it works.

Thanks again.

More problems. Here is the report.

jorge@ubuntu:~$ sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
--2010-10-03 18:01:49--  [http://www.medibuntu.org/sources.list.d/karmic.list](http://www.medibuntu.org/sources.list.d/karmic.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 272 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[=======================================================================================================================================>] 272         --.-K/s   in 0s      

2010-10-03 18:01:49 (14.2 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [272/272]

Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release [9,237B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages [3,279B]
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages [7,553B]
Fetched 20.3kB in 1s (10.3kB/s)
Reading package lists...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  googleearth: Depends: ttf-dejavu but it is not going to be installed or
                        ttf-bitstream-vera but it is not installable or
                        msttcorefonts
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release [9,237B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Fetched 198B in 1s (164B/s)
Reading package lists...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
jorge@ubuntu:~$ 
jorge@ubuntu:~$ 
jorge@ubuntu:~$ 
jorge@ubuntu:~$ sudo apt-get install googleearth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
googleearth is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  googleearth: Depends: ttf-dejavu but it is not going to be installed or
                        ttf-bitstream-vera but it is not installable or
                        msttcorefonts
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
jorge@ubuntu:~$

---

### Post by jrgonzalez on 2010-10-03
> **harrisonk said:**
> The problem is that googleearth requires:

ttf-dejavu ttf-bitstream-vera msttcorefonts

Run this: ```
 sudo apt-get install ttf-dejavu ttf-bitstream-vera msttcorefonts 
```then run that install command again.

Harrison

Harrison:

Here is the report when I ran the sudo command:  (I did not run the install command, since there were errors.

I aprreciate all the help you guys are giving me. Command line stuff is like Chisnese to me.

Here it is: 

jorge@ubuntu:~$ sudo apt-get install ttf-dejavu ttf-bitstream-vera msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ttf-bitstream-vera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ttf-bitstream-vera has no installation candidate

---

### Post by jrgonzalez on 2010-10-03
Waiting for further instructions.

Thanks.

Jorge

---

### Post by harrisonk on 2010-10-03
Hello

Go ahead and try the install command.

It might work. It might be it needs one of those ttf fonts not all of them.

Harrison

---

### Post by harrisonk on 2010-10-03
Or I just thought try installing ttf-bitstream-vera by its self:

```
 sudo apt-get install ttf-bitstream-vera 
```

report back the errors if any.

Harrison

---

### Post by jrgonzalez on 2010-10-03
> **harrisonk said:**
> Or I just thought try installing ttf-bitstream-vera by its self:

```
 sudo apt-get install ttf-bitstream-vera 
```report back the errors if any.

Harrison

Here is the report:

jorge@ubuntu:~$ sudo apt-get install ttf-bitstream-vera
[sudo] password for jorge: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ttf-bitstream-vera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ttf-bitstream-vera has no installation candidate
jorge@ubuntu:~$

---

### Post by jrgonzalez on 2010-10-03
E: Package ttf-bitstream-vera has no installation candidate

I gues we are stuck if we don't have dear Vera?

JRG

---

### Post by mikewhatever on 2010-10-03
jrgonzalez, what version of Ubuntu do you have?
Generally, if GE is installed according to Synaptic, you should be able to run it. What's the output of 'locate google'?

---

### Post by jrgonzalez on 2010-10-03
> **mikewhatever said:**
> jrgonzalez, what version of Ubuntu do you have?
Generally, if GE is installed according to Synaptic, you should be able to run it. What's the output of 'locate google'?

I just run the 'locate google' from the terminal, right?

I think I have the 9.04 version, but I am not sure. How do I find out?

---

### Post by Hakunka-Matata on 2010-10-03
Do you have Medibuntu repository as a software source in:

From the Desktop:
System > Administration > Synaptic Package Manager > Settings > Repositories > Other Software

if you do, it should be easy to install straight away using synpatic package manager.

If you do not, this URL tells you all about it and how to add it.

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by beew on 2010-10-03
Can you just uninstall all the google earth packages you have installed and then reinstall google earth from the medibuntu repo? 

```
sudo apt-get purge googleearth*
```

To install from Medibuntu

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

I have done it many times on different computers and never had I have a problem. Don't know why you downloaded a bunch of packages from Google to begin with.

---

### Post by jrgonzalez on 2010-10-03
> **mikewhatever said:**
> jrgonzalez, what version of Ubuntu do you have?
Generally, if GE is installed according to Synaptic, you should be able to run it. What's the output of 'locate google'?

OK. Here is the 'locate google' report:

The google report is huge and the computer does not let me copy all of it. I used select all, and it does not include all of it.
```

/opt/google/picasa/3.0/wine/lib/wine/dispdib.dll16
/opt/google/picasa/3.0/wine/lib/wine/display.drv16
/opt/google/picasa/3.0/wine/lib/wine/dmband.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmcompos.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmime.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmloader.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmscript.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmstyle.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmsynth.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmusic.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmusic32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dnsapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dplay.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dplayx.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpnaddr.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpnet.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpnhpast.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpnlobby.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpwsockx.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dsound.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dssenh.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dswave.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dwmapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dxdiagn.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dxgi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/eject.exe.so
/opt/google/picasa/3.0/wine/lib/wine/expand.exe.so
/opt/google/picasa/3.0/wine/lib/wine/explorer.exe.so
/opt/google/picasa/3.0/wine/lib/wine/faultrep.dll.so
/opt/google/picasa/3.0/wine/lib/wine/fusion.dll.so
/opt/google/picasa/3.0/wine/lib/wine/gdi.exe16
/opt/google/picasa/3.0/wine/lib/wine/gdi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/gdiplus.dll.so
/opt/google/picasa/3.0/wine/lib/wine/glu32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/gphoto2.ds.so
/opt/google/picasa/3.0/wine/lib/wine/gpkcsp.dll.so
/opt/google/picasa/3.0/wine/lib/wine/hal.dll.so
/opt/google/picasa/3.0/wine/lib/wine/hh.exe.so
/opt/google/picasa/3.0/wine/lib/wine/hhctrl.ocx.so
/opt/google/picasa/3.0/wine/lib/wine/hid.dll.so
/opt/google/picasa/3.0/wine/lib/wine/hlink.dll.so
/opt/google/picasa/3.0/wine/lib/wine/hnetcfg.dll.so
/opt/google/picasa/3.0/wine/lib/wine/iccvid.dll.so
/opt/google/picasa/3.0/wine/lib/wine/icinfo.exe.so
/opt/google/picasa/3.0/wine/lib/wine/icmp.dll.so
/opt/google/picasa/3.0/wine/lib/wine/iexplore.exe.so
/opt/google/picasa/3.0/wine/lib/wine/ifsmgr.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/imaadp32.acm.so
/opt/google/picasa/3.0/wine/lib/wine/imagehlp.dll.so
/opt/google/picasa/3.0/wine/lib/wine/imm.dll16
/opt/google/picasa/3.0/wine/lib/wine/imm32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/inetcomm.dll.so
/opt/google/picasa/3.0/wine/lib/wine/inetmib1.dll.so
/opt/google/picasa/3.0/wine/lib/wine/infosoft.dll.so
/opt/google/picasa/3.0/wine/lib/wine/initpki.dll.so
/opt/google/picasa/3.0/wine/lib/wine/inkobj.dll.so
/opt/google/picasa/3.0/wine/lib/wine/inseng.dll.so
/opt/google/picasa/3.0/wine/lib/wine/iphlpapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/itircl.dll.so
/opt/google/picasa/3.0/wine/lib/wine/itss.dll.so
/opt/google/picasa/3.0/wine/lib/wine/jscript.dll.so
/opt/google/picasa/3.0/wine/lib/wine/kernel32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/keyboard.drv16
/opt/google/picasa/3.0/wine/lib/wine/krnl386.exe16
/opt/google/picasa/3.0/wine/lib/wine/license.exe.so
/opt/google/picasa/3.0/wine/lib/wine/localspl.dll.so
/opt/google/picasa/3.0/wine/lib/wine/localui.dll.so
/opt/google/picasa/3.0/wine/lib/wine/lz32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/lzexpand.dll16
/opt/google/picasa/3.0/wine/lib/wine/mapi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mciavi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mcicda.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mciseq.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mciwave.dll.so
/opt/google/picasa/3.0/wine/lib/wine/midimap.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mlang.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mmdevldr.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/mmsystem.dll16
/opt/google/picasa/3.0/wine/lib/wine/monodebg.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/mountmgr.sys.so
/opt/google/picasa/3.0/wine/lib/wine/mouse.drv16
/opt/google/picasa/3.0/wine/lib/wine/mpr.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mprapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msacm.dll16
/opt/google/picasa/3.0/wine/lib/wine/msacm32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msacm32.drv.so
/opt/google/picasa/3.0/wine/lib/wine/msadp32.acm.so
/opt/google/picasa/3.0/wine/lib/wine/mscat32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mscms.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mscoree.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msdmo.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msftedit.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msg711.acm.so
/opt/google/picasa/3.0/wine/lib/wine/mshtml.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mshtml.tlb.so
/opt/google/picasa/3.0/wine/lib/wine/msi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msiexec.exe.so
/opt/google/picasa/3.0/wine/lib/wine/msimg32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msimtf.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msisip.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msisys.ocx.so
/opt/google/picasa/3.0/wine/lib/wine/msnet32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msrle32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mssip32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mstask.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvcirt.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvcr71.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvcrt.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvcrt20.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvcrt40.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvcrtd.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvfw32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvidc32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvideo.dll16
/opt/google/picasa/3.0/wine/lib/wine/mswsock.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msxml3.dll.so
/opt/google/picasa/3.0/wine/lib/wine/nddeapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/net.exe.so
/opt/google/picasa/3.0/wine/lib/wine/netapi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/newdev.dll.so
/opt/google/picasa/3.0/wine/lib/wine/notepad.exe.so
/opt/google/picasa/3.0/wine/lib/wine/ntdll.dll.so
/opt/google/picasa/3.0/wine/lib/wine/ntdsapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/ntoskrnl.exe.so
/opt/google/picasa/3.0/wine/lib/wine/ntprint.dll.so
/opt/google/picasa/3.0/wine/lib/wine/objsel.dll.so
/opt/google/picasa/3.0/wine/lib/wine/odbc32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/odbccp32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/ole2.dll16
/opt/google/picasa/3.0/wine/lib/wine/ole2conv.dll16
/opt/google/picasa/3.0/wine/lib/wine/ole2disp.dll16
/opt/google/picasa/3.0/wine/lib/wine/ole2nls.dll16
/opt/google/picasa/3.0/wine/lib/wine/ole2prox.dll16
/opt/google/picasa/3.0/wine/lib/wine/ole2thk.dll16
/opt/google/picasa/3.0/wine/lib/wine/ole32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/oleacc.dll.so
/opt/google/picasa/3.0/wine/lib/wine/oleaut32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/olecli.dll16
/opt/google/picasa/3.0/wine/lib/wine/olecli32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/oledlg.dll.so
/opt/google/picasa/3.0/wine/lib/wine/olepro32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/olesvr.dll16
/opt/google/picasa/3.0/wine/lib/wine/olesvr32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/olethk32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/oleview.exe.so
/opt/google/picasa/3.0/wine/lib/wine/opengl32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/pdh.dll.so
/opt/google/picasa/3.0/wine/lib/wine/powrprof.dll.so
/opt/google/picasa/3.0/wine/lib/wine/printui.dll.so
/opt/google/picasa/3.0/wine/lib/wine/progman.exe.so
/opt/google/picasa/3.0/wine/lib/wine/propsys.dll.so
/opt/google/picasa/3.0/wine/lib/wine/psapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/pstorec.dll.so
/opt/google/picasa/3.0/wine/lib/wine/qcap.dll.so
/opt/google/picasa/3.0/wine/lib/wine/qedit.dll.so
/opt/google/picasa/3.0/wine/lib/wine/qmgr.dll.so
/opt/google/picasa/3.0/wine/lib/wine/qmgrprxy.dll.so
/opt/google/picasa/3.0/wine/lib/wine/quartz.dll.so
/opt/google/picasa/3.0/wine/lib/wine/query.dll.so
/opt/google/picasa/3.0/wine/lib/wine/rasapi16.dll16
/opt/google/picasa/3.0/wine/lib/wine/rasapi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/reg.exe.so
/opt/google/picasa/3.0/wine/lib/wine/regedit.exe.so
/opt/google/picasa/3.0/wine/lib/wine/regsvr32.exe.so
/opt/google/picasa/3.0/wine/lib/wine/resutils.dll.so
/opt/google/picasa/3.0/wine/lib/wine/riched20.dll.so
/opt/google/picasa/3.0/wine/lib/wine/riched32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/rpcrt4.dll.so
/opt/google/picasa/3.0/wine/lib/wine/rpcss.exe.so
/opt/google/picasa/3.0/wine/lib/wine/rsabase.dll.so
/opt/google/picasa/3.0/wine/lib/wine/rsaenh.dll.so
/opt/google/picasa/3.0/wine/lib/wine/rundll32.exe.so
/opt/google/picasa/3.0/wine/lib/wine/sane.ds.so
/opt/google/picasa/3.0/wine/lib/wine/sccbase.dll.so
/opt/google/picasa/3.0/wine/lib/wine/schannel.dll.so
/opt/google/picasa/3.0/wine/lib/wine/secedit.exe.so
/opt/google/picasa/3.0/wine/lib/wine/secur32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/security.dll.so
/opt/google/picasa/3.0/wine/lib/wine/sensapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/serialui.dll.so
/opt/google/picasa/3.0/wine/lib/wine/services.exe.so
/opt/google/picasa/3.0/wine/lib/wine/set_lang.exe.so
/opt/google/picasa/3.0/wine/lib/wine/setupapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/setupx.dll16
/opt/google/picasa/3.0/wine/lib/wine/sfc.dll.so
/opt/google/picasa/3.0/wine/lib/wine/sfc_os.dll.so
/opt/google/picasa/3.0/wine/lib/wine/shdoclc.dll.so
/opt/google/picasa/3.0/wine/lib/wine/shdocvw.dll.so
/opt/google/picasa/3.0/wine/lib/wine/shell.dll16
/opt/google/picasa/3.0/wine/lib/wine/shell32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/shfolder.dll.so
/opt/google/picasa/3.0/wine/lib/wine/shlwapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/slbcsp.dll.so
/opt/google/picasa/3.0/wine/lib/wine/slc.dll.so
/opt/google/picasa/3.0/wine/lib/wine/snmpapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/softpub.dll.so
/opt/google/picasa/3.0/wine/lib/wine/sound.drv16
/opt/google/picasa/3.0/wine/lib/wine/spoolss.dll.so
/opt/google/picasa/3.0/wine/lib/wine/spoolsv.exe.so
/opt/google/picasa/3.0/wine/lib/wine/start.exe.so
/opt/google/picasa/3.0/wine/lib/wine/stdole2.tlb.so
/opt/google/picasa/3.0/wine/lib/wine/stdole32.tlb.so
/opt/google/picasa/3.0/wine/lib/wine/sti.dll.so
/opt/google/picasa/3.0/wine/lib/wine/storage.dll16
/opt/google/picasa/3.0/wine/lib/wine/stress.dll16
/opt/google/picasa/3.0/wine/lib/wine/svchost.exe.so
/opt/google/picasa/3.0/wine/lib/wine/svrapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/sxs.dll.so
/opt/google/picasa/3.0/wine/lib/wine/system.drv16
/opt/google/picasa/3.0/wine/lib/wine/tapi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/taskmgr.exe.so
/opt/google/picasa/3.0/wine/lib/wine/toolhelp.dll16
/opt/google/picasa/3.0/wine/lib/wine/twain.dll16
/opt/google/picasa/3.0/wine/lib/wine/twain_32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/typelib.dll16
/opt/google/picasa/3.0/wine/lib/wine/unicows.dll.so
/opt/google/picasa/3.0/wine/lib/wine/uninstaller.exe.so
/opt/google/picasa/3.0/wine/lib/wine/url.dll.so
/opt/google/picasa/3.0/wine/lib/wine/urlmon.dll.so
/opt/google/picasa/3.0/wine/lib/wine/user.exe16
/opt/google/picasa/3.0/wine/lib/wine/user32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/userenv.dll.so
/opt/google/picasa/3.0/wine/lib/wine/usp10.dll.so
/opt/google/picasa/3.0/wine/lib/wine/uxtheme.dll.so
/opt/google/picasa/3.0/wine/lib/wine/vdhcp.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/vdmdbg.dll.so
/opt/google/picasa/3.0/wine/lib/wine/ver.dll16
/opt/google/picasa/3.0/wine/lib/wine/version.dll.so
/opt/google/picasa/3.0/wine/lib/wine/vmm.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/vnbt.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/vnetbios.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/vtdapi.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/vwin32.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/w32skrnl.dll.so
/opt/google/picasa/3.0/wine/lib/wine/w32sys.dll16
/opt/google/picasa/3.0/wine/lib/wine/wdi.exe.so
/opt/google/picasa/3.0/wine/lib/wine/win32s16.dll16
/opt/google/picasa/3.0/wine/lib/wine/win87em.dll16
/opt/google/picasa/3.0/wine/lib/wine/winaspi.dll16
/opt/google/picasa/3.0/wine/lib/wine/windebug.dll16
/opt/google/picasa/3.0/wine/lib/wine/winealsa.drv.so
/opt/google/picasa/3.0/wine/lib/wine/wineaudioio.drv.so
/opt/google/picasa/3.0/wine/lib/wine/wineboot.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winebrowser.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winecfg.exe.so
/opt/google/picasa/3.0/wine/lib/wine/wineconsole.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winecoreaudio.drv.so
/opt/google/picasa/3.0/wine/lib/wine/wined3d.dll.so
/opt/google/picasa/3.0/wine/lib/wine/winedbg.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winedevice.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winedos.dll.so
/opt/google/picasa/3.0/wine/lib/wine/winedumpfontver.exe.so
/opt/google/picasa/3.0/wine/lib/wine/wineesd.drv.so
/opt/google/picasa/3.0/wine/lib/wine/winefile.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winefontcfg.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winejack.drv.so
/opt/google/picasa/3.0/wine/lib/wine/winejoystick.drv.so
/opt/google/picasa/3.0/wine/lib/wine/winemenubuilder.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winemine.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winemp3.acm.so
/opt/google/picasa/3.0/wine/lib/wine/winenas.drv.so
/opt/google/picasa/3.0/wine/lib/wine/wineoss.drv.so
/opt/google/picasa/3.0/wine/lib/wine/winepath.exe.so
/opt/google/picasa/3.0/wine/lib/wine/wineps.drv.so
/opt/google/picasa/3.0/wine/lib/wine/wineps16.drv16
/opt/google/picasa/3.0/wine/lib/wine/winevdm.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winex11.drv.so
/opt/google/picasa/3.0/wine/lib/wine/wing.dll16
/opt/google/picasa/3.0/wine/lib/wine/wing32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/winhelp.exe16
/opt/google/picasa/3.0/wine/lib/wine/winhlp32.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winhttp.dll.so
/opt/google/picasa/3.0/wine/lib/wine/wininet.dll.so
/opt/google/picasa/3.0/wine/lib/wine/winmm.dll.so
/opt/google/picasa/3.0/wine/lib/wine/winnls.dll16
/opt/google/picasa/3.0/wine/lib/wine/winnls32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/winoldap.mod16
/opt/google/picasa/3.0/wine/lib/wine/winscard.dll.so
/opt/google/picasa/3.0/wine/lib/wine/winsock.dll16
/opt/google/picasa/3.0/wine/lib/wine/winspool.drv.so
/opt/google/picasa/3.0/wine/lib/wine/wintab.dll16
/opt/google/picasa/3.0/wine/lib/wine/wintab32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/wintrust.dll.so
/opt/google/picasa/3.0/wine/lib/wine/winver.exe.so
/opt/google/picasa/3.0/wine/lib/wine/wldap32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/wmi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/wnaspi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/wordpad.exe.so
/opt/google/picasa/3.0/wine/lib/wine/wow32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/wprocs.dll16
/opt/google/picasa/3.0/wine/lib/wine/write.exe.so
/opt/google/picasa/3.0/wine/lib/wine/ws2_32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/wsock32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/wtsapi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/xcopy.exe.so
/opt/google/picasa/3.0/wine/share/applications
/opt/google/picasa/3.0/wine/share/man
/opt/google/picasa/3.0/wine/share/wine
/opt/google/picasa/3.0/wine/share/applications/wine.desktop
/opt/google/picasa/3.0/wine/share/man/de.UTF-8
/opt/google/picasa/3.0/wine/share/man/fr.UTF-8
/opt/google/picasa/3.0/wine/share/man/man1
/opt/google/picasa/3.0/wine/share/man/de.UTF-8/man1
/opt/google/picasa/3.0/wine/share/man/de.UTF-8/man1/wine.1
/opt/google/picasa/3.0/wine/share/man/fr.UTF-8/man1
/opt/google/picasa/3.0/wine/share/man/fr.UTF-8/man1/wine.1
/opt/google/picasa/3.0/wine/share/man/fr.UTF-8/man1/wineserver.1
/opt/google/picasa/3.0/wine/share/man/man1/wine.1
/opt/google/picasa/3.0/wine/share/man/man1/winedbg.1
/opt/google/picasa/3.0/wine/share/man/man1/wineprefixcreate.1
/opt/google/picasa/3.0/wine/share/man/man1/wineserver.1
/opt/google/picasa/3.0/wine/share/wine/fonts
/opt/google/picasa/3.0/wine/share/wine/generic.ppd
/opt/google/picasa/3.0/wine/share/wine/wine.inf
/opt/google/picasa/3.0/wine/share/wine/fonts/coue1255.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/coue1256.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/coue1257.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/coure.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/couree.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/coureg.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/courer.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/couret.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/cvgasys.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/hvgasys.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/jsmalle.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/jvgasys.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/marlett.ttf
/opt/google/picasa/3.0/wine/share/wine/fonts/smae1255.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/smae1256.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/smae1257.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/smalle.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/smallee.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/smalleg.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/smaller.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/smallet.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/ssee1255.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/ssee1256.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/ssee1257.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/ssee874.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/sserife.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/sserifee.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/sserifeg.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/sserifer.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/sserifet.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/svgasys.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/tahoma.ttf
/opt/google/picasa/3.0/wine/share/wine/fonts/tahomabd.ttf
/opt/google/picasa/3.0/wine/share/wine/fonts/vgas1255.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/vgas1256.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/vgas1257.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/vgas874.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/vgasys.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/vgasyse.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/vgasysg.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/vgasysr.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/vgasyst.fon
/usr/lib/libgdata-google-1.2.so.1
/usr/lib/libgdata-google-1.2.so.1.0.0
/usr/lib/deskbar-applet/deskbar-applet/modules-2.20-compatible/googlecodesearch.py
/usr/lib/deskbar-applet/deskbar-applet/modules-2.20-compatible/googlecodesearch.pyc
/usr/lib/deskbar-applet/deskbar-applet/modules-2.20-compatible/googlesearch.py
/usr/lib/deskbar-applet/deskbar-applet/modules-2.20-compatible/googlesearch.pyc
/usr/lib/evolution/2.28/plugins/liborg-gnome-evolution-google.so
/usr/lib/evolution/2.28/plugins/org-gnome-evolution-google.eplug
/usr/lib/evolution-data-server-1.2/extensions/libebookbackendgoogle.so
/usr/lib/evolution-data-server-1.2/extensions/libecalbackendgoogle.so
/usr/lib/firefox-addons/searchplugins/en-US/google.xml
/usr/lib/pymodules/python2.5/google
/usr/lib/pymodules/python2.5/google/__init__.py
/usr/lib/pymodules/python2.5/google/__init__.pyc
/usr/lib/pymodules/python2.5/google/protobuf
/usr/lib/pymodules/python2.5/google/protobuf/__init__.py
/usr/lib/pymodules/python2.5/google/protobuf/__init__.pyc
/usr/lib/pymodules/python2.5/google/protobuf/descriptor.py
/usr/lib/pymodules/python2.5/google/protobuf/descriptor.pyc
/usr/lib/pymodules/python2.5/google/protobuf/descriptor_pb2.py
/usr/lib/pymodules/python2.5/google/protobuf/descriptor_pb2.pyc
/usr/lib/pymodules/python2.5/google/protobuf/internal
/usr/lib/pymodules/python2.5/google/protobuf/message.py
/usr/lib/pymodules/python2.5/google/protobuf/message.pyc
/usr/lib/pymodules/python2.5/google/protobuf/reflection.py
/usr/lib/pymodules/python2.5/google/protobuf/reflection.pyc
/usr/lib/pymodules/python2.5/google/protobuf/service.py
/usr/lib/pymodules/python2.5/google/protobuf/service.pyc
/usr/lib/pymodules/python2.5/google/protobuf/service_reflection.py
/usr/lib/pymodules/python2.5/google/protobuf/service_reflection.pyc
/usr/lib/pymodules/python2.5/google/protobuf/text_format.py
/usr/lib/pymodules/python2.5/google/protobuf/text_format.pyc
/usr/lib/pymodules/python2.5/google/protobuf/internal/__init__.py
/usr/lib/pymodules/python2.5/google/protobuf/internal/__init__.pyc
/usr/lib/pymodules/python2.5/google/protobuf/internal/containers.py
/usr/lib/pymodules/python2.5/google/protobuf/internal/containers.pyc
/usr/lib/pymodules/python2.5/google/protobuf/internal/decoder.py
/usr/lib/pymodules/python2.5/google/protobuf/internal/decoder.pyc
/usr/lib/pymodules/python2.5/google/protobuf/internal/encoder.py
/usr/lib/pymodules/python2.5/google/protobuf/internal/encoder.pyc
/usr/lib/pymodules/python2.5/google/protobuf/internal/input_stream.py
/usr/lib/pymodules/python2.5/google/protobuf/internal/input_stream.pyc
/usr/lib/pymodules/python2.5/google/protobuf/internal/message_listener.py
/usr/lib/pymodules/python2.5/google/protobuf/internal/message_listener.pyc
/usr/lib/pymodules/python2.5/google/protobuf/internal/output_stream.py
/usr/lib/pymodules/python2.5/google/protobuf/internal/output_stream.pyc
/usr/lib/pymodules/python2.5/google/protobuf/internal/type_checkers.py
/usr/lib/pymodules/python2.5/google/protobuf/internal/type_checkers.pyc
/usr/lib/pymodules/python2.5/google/protobuf/internal/wire_format.py
/usr/lib/pymodules/python2.5/google/protobuf/internal/wire_format.pyc
/usr/lib/pymodules/python2.6/google
/usr/lib/pymodules/python2.6/google/__init__.py
/usr/lib/pymodules/python2.6/google/__init__.pyc
/usr/lib/pymodules/python2.6/google/protobuf
/usr/lib/pymodules/python2.6/google/protobuf/__init__.py
/usr/lib/pymodules/python2.6/google/protobuf/__init__.pyc
/usr/lib/pymodules/python2.6/google/protobuf/descriptor.py
/usr/lib/pymodules/python2.6/google/protobuf/descriptor.pyc
/usr/lib/pymodules/python2.6/google/protobuf/descriptor_pb2.py
/usr/lib/pymodules/python2.6/google/protobuf/descriptor_pb2.pyc
/usr/lib/pymodules/python2.6/google/protobuf/internal
/usr/lib/pymodules/python2.6/google/protobuf/message.py
/usr/lib/pymodules/python2.6/google/protobuf/message.pyc
/usr/lib/pymodules/python2.6/google/protobuf/reflection.py
/usr/lib/pymodules/python2.6/google/protobuf/reflection.pyc
/usr/lib/pymodules/python2.6/google/protobuf/service.py
/usr/lib/pymodules/python2.6/google/protobuf/service.pyc
/usr/lib/pymodules/python2.6/google/protobuf/service_reflection.py
/usr/lib/pymodules/python2.6/google/protobuf/service_reflection.pyc
/usr/lib/pymodules/python2.6/google/protobuf/text_format.py
/usr/lib/pymodules/python2.6/google/protobuf/text_format.pyc
/usr/lib/pymodules/python2.6/google/protobuf/internal/__init__.py
/usr/lib/pymodules/python2.6/google/protobuf/internal/__init__.pyc
/usr/lib/pymodules/python2.6/google/protobuf/internal/containers.py
/usr/lib/pymodules/python2.6/google/protobuf/internal/containers.pyc
/usr/lib/pymodules/python2.6/google/protobuf/internal/decoder.py
/usr/lib/pymodules/python2.6/google/protobuf/internal/decoder.pyc
/usr/lib/pymodules/python2.6/google/protobuf/internal/encoder.py
/usr/lib/pymodules/python2.6/google/protobuf/internal/encoder.pyc
/usr/lib/pymodules/python2.6/google/protobuf/internal/input_stream.py
/usr/lib/pymodules/python2.6/google/protobuf/internal/input_stream.pyc
/usr/lib/pymodules/python2.6/google/protobuf/internal/message_listener.py
/usr/lib/pymodules/python2.6/google/protobuf/internal/message_listener.pyc
/usr/lib/pymodules/python2.6/google/protobuf/internal/output_stream.py
/usr/lib/pymodules/python2.6/google/protobuf/internal/output_stream.pyc
/usr/lib/pymodules/python2.6/google/protobuf/internal/type_checkers.py
/usr/lib/pymodules/python2.6/google/protobuf/internal/type_checkers.pyc
/usr/lib/pymodules/python2.6/google/protobuf/internal/wire_format.py
/usr/lib/pymodules/python2.6/google/protobuf/internal/wire_format.pyc
/usr/lib/python2.4/site-packages/twisted/web/google.py
/usr/lib/python2.4/site-packages/twisted/web/google.pyc
/usr/lib/python2.5/site-packages/twisted/web/google.py
/usr/lib/python2.5/site-packages/twisted/web/google.pyc
/usr/lib/python2.6/dist-packages/twisted/web/google.py
/usr/lib/python2.6/dist-packages/twisted/web/google.pyc
/usr/share/app-install/desktop/prism-google-analytics.desktop
/usr/share/app-install/desktop/prism-google-calendar.desktop
/usr/share/app-install/desktop/prism-google-docs.desktop
/usr/share/app-install/desktop/prism-google-groups.desktop
/usr/share/app-install/desktop/prism-google-mail.desktop
/usr/share/app-install/desktop/prism-google-reader.desktop
/usr/share/app-install/desktop/prism-google-talk.desktop
/usr/share/app-install/icons/prism-google-analytics.png
/usr/share/app-install/icons/prism-google-calendar.png
/usr/share/app-install/icons/prism-google-docs.png
/usr/share/app-install/icons/prism-google-groups.png
/usr/share/app-install/icons/prism-google-mail.png
/usr/share/app-install/icons/prism-google-reader.png
/usr/share/app-install/icons/prism-google-talk.png
/usr/share/deskbar-applet/art/google.png
/usr/share/doc/libgdata-google1.2-1
/usr/share/doc/libgdata-google1.2-1/NEWS.gz
/usr/share/doc/libgdata-google1.2-1/TODO
/usr/share/doc/libgdata-google1.2-1/changelog.Debian.gz
/usr/share/doc/libgdata-google1.2-1/copyright
/usr/share/doc/python-twisted-web/examples/google.py
/usr/share/empathy/icons/hicolor/16x16/apps/im-google-talk.png
/usr/share/empathy/icons/hicolor/22x22/apps/im-google-talk.png
/usr/share/empathy/icons/hicolor/24x24/apps/im-google-talk.png
/usr/share/empathy/icons/hicolor/32x32/apps/im-google-talk.png
/usr/share/empathy/icons/hicolor/48x48/apps/im-google-talk.png
/usr/share/empathy/icons/hicolor/scalable/apps/im-google-talk.svg
/usr/share/gnome/help/evolution/C/figures/google_cal_view.png
/usr/share/gnome/help/evolution/en_GB/figures/google_cal_view.png
/usr/share/lintian/overrides/libgdata-google1.2-1
/usr/share/mime/application/vnd.google-earth.kml+xml.xml
/usr/share/mime/application/vnd.google-earth.kmz.xml
/usr/share/mime/text/x-google-video-pointer.xml
/usr/share/pixmaps/pidgin/protocols/16/google-talk.png
/usr/share/pixmaps/pidgin/protocols/22/google-talk.png
/usr/share/pixmaps/pidgin/protocols/scalable/google-talk.svg
/usr/share/pyshared/google
/usr/share/pyshared/google/protobuf
/usr/share/pyshared/google/protobuf/descriptor.py
/usr/share/pyshared/google/protobuf/descriptor_pb2.py
/usr/share/pyshared/google/protobuf/internal
/usr/share/pyshared/google/protobuf/message.py
/usr/share/pyshared/google/protobuf/reflection.py
/usr/share/pyshared/google/protobuf/service.py
/usr/share/pyshared/google/protobuf/service_reflection.py
/usr/share/pyshared/google/protobuf/text_format.py
/usr/share/pyshared/google/protobuf/internal/containers.py
/usr/share/pyshared/google/protobuf/internal/decoder.py
/usr/share/pyshared/google/protobuf/internal/encoder.py
/usr/share/pyshared/google/protobuf/internal/input_stream.py
/usr/share/pyshared/google/protobuf/internal/message_listener.py
/usr/share/pyshared/google/protobuf/internal/output_stream.py
/usr/share/pyshared/google/protobuf/internal/type_checkers.py
/usr/share/pyshared/google/protobuf/internal/wire_format.py
/usr/share/pyshared/twisted/web/google.py
/var/lib/dpkg/info/libgdata-google1.2-1.list
/var/lib/dpkg/info/libgdata-google1.2-1.md5sums
/var/lib/dpkg/info/libgdata-google1.2-1.postinst
/var/lib/dpkg/info/libgdata-google1.2-1.postrm
/var/lib/dpkg/info/libgdata-google1.2-1.shlibs
jorge@ubuntu:~$ 
/opt/google/picasa/3.0/wine/lib/wine/dispdib.dll16
/opt/google/picasa/3.0/wine/lib/wine/display.drv16
/opt/google/picasa/3.0/wine/lib/wine/dmband.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmcompos.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmime.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmloader.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmscript.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmstyle.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmsynth.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmusic.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmusic32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dnsapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dplay.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dplayx.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpnaddr.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpnet.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpnhpast.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpnlobby.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpwsockx.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dsound.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dssenh.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dswave.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dwmapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dxdiagn.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dxgi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/eject.exe.so
/opt/google/picasa/3.0/wine/lib/wine/expand.exe.so
/opt/google/picasa/3.0/wine/lib/wine/explorer.exe.so
/opt/google/picasa/3.0/wine/lib/wine/faultrep.dll.so
/opt/google/picasa/3.0/wine/lib/wine/fusion.dll.so
/opt/google/picasa/3.0/wine/lib/wine/gdi.exe16
/opt/google/picasa/3.0/wine/lib/wine/gdi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/gdiplus.dll.so
/opt/google/picasa/3.0/wine/lib/wine/glu32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/gphoto2.ds.so
/opt/google/picasa/3.0/wine/lib/wine/gpkcsp.dll.so
/opt/google/picasa/3.0/wine/lib/wine/hal.dll.so
/opt/google/picasa/3.0/wine/lib/wine/hh.exe.so
/opt/google/picasa/3.0/wine/lib/wine/hhctrl.ocx.so
/opt/google/picasa/3.0/wine/lib/wine/hid.dll.so
/opt/google/picasa/3.0/wine/lib/wine/hlink.dll.so
/opt/google/picasa/3.0/wine/lib/wine/hnetcfg.dll.so
/opt/google/picasa/3.0/wine/lib/wine/iccvid.dll.so
/opt/google/picasa/3.0/wine/lib/wine/icinfo.exe.so
/opt/google/picasa/3.0/wine/lib/wine/icmp.dll.so
/opt/google/picasa/3.0/wine/lib/wine/iexplore.exe.so
/opt/google/picasa/3.0/wine/lib/wine/ifsmgr.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/imaadp32.acm.so
/opt/google/picasa/3.0/wine/lib/wine/dispdib.dll16
/opt/google/picasa/3.0/wine/lib/wine/display.drv16
/opt/google/picasa/3.0/wine/lib/wine/dmband.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmcompos.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmime.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmloader.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmscript.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmstyle.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmsynth.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmusic.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmusic32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dnsapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dplay.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dplayx.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpnaddr.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpnet.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpnhpast.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpnlobby.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpwsockx.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dsound.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dssenh.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dswave.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dwmapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dxdiagn.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dxgi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/eject.exe.so
/opt/google/picasa/3.0/wine/lib/wine/expand.exe.so
/opt/google/picasa/3.0/wine/lib/wine/explorer.exe.so
/opt/google/picasa/3.0/wine/lib/wine/faultrep.dll.so
/opt/google/picasa/3.0/wine/lib/wine/fusion.dll.so
/opt/google/picasa/3.0/wine/lib/wine/gdi.exe16
/opt/google/picasa/3.0/wine/lib/wine/gdi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/gdiplus.dll.so
/opt/google/picasa/3.0/wine/lib/wine/glu32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/gphoto2.ds.so
/opt/google/picasa/3.0/wine/lib/wine/gpkcsp.dll.so
/opt/google/picasa/3.0/wine/lib/wine/hal.dll.so
/opt/google/picasa/3.0/wine/lib/wine/hh.exe.so
/opt/google/picasa/3.0/wine/lib/wine/hhctrl.ocx.so
/opt/google/picasa/3.0/wine/lib/wine/hid.dll.so
/opt/google/picasa/3.0/wine/lib/wine/hlink.dll.so
/opt/google/picasa/3.0/wine/lib/wine/hnetcfg.dll.so
/opt/google/picasa/3.0/wine/lib/wine/iccvid.dll.so
/opt/google/picasa/3.0/wine/lib/wine/icinfo.exe.so
/opt/google/picasa/3.0/wine/lib/wine/icmp.dll.so
/opt/google/picasa/3.0/wine/lib/wine/iexplore.exe.so
/opt/google/picasa/3.0/wine/lib/wine/ifsmgr.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/imaadp32.acm.so

```

---

### Post by Hakunka-Matata on 2010-10-03
What version Ubuntu?  **System > About Ubuntu**

---

### Post by harrisonk on 2010-10-03
jrgonzalez I think you should just go with the medibuntu repo because of the install being 9.04 .

Harrison

---

### Post by jrgonzalez on 2010-10-03
> **beew said:**
> Can you just uninstall all the google earth packages you have installed and then reinstall google earth from the medibuntu repo? 

```
sudo apt-get purge googleearth*
```To install from Medibuntu

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I have done it many times on different computers and never had I have a problem. Don't know why you downloaded a bunch of packages from Google to begin with.

I used synaptic to install the google earth package. But then that did not appear to work and someone at Ubuntu Forum told me to do something else. 

If stuff is not automated, novices like me are bound to run into problems. 

How do I un-install all the google earth packages. By using the Synaptic package manager?

That I can try. I Will let you know what happens.

---

### Post by beew on 2010-10-03
Why do you want to install from wine in the first place? Go to /home click "show hidden files" and delete .wine.

BTW, there seems to be something wrong with the last message you post. I can't scroll to the end of it. Maybe you should delete the message somehow and post again:)

---

### Post by beew on 2010-10-03
> How do I un-install all the google earth packages. By using the Synaptic package manager?

Try this and see if it works. Type in the terminal

```
sudo apt-get purge googleearth*
```

Also, if as you said you see these packages in synaptic you can also open synaptic, find all the entries and remove them completely (click and choose "remove completely")

I think it would be easier if you did this in the begining. I have no idea why someone actually told you to use the make command on the packages you download, seeing that obviously a beginner (as I am), that get you into more troubles as you would be installing more things and face more dependencies problems.

---

### Post by jrgonzalez on 2010-10-03
OK guys, I have Karmic Koala 9.10

I have un-installed the old package.

Do I re-intall them again using the Synaptic Package Manager?

There are now three lines that show, in the Synaptic Package Manager, and now they are all unchecked,

Binary files, data and package. are the three lines.

Do I re-install those again? I am getting a little bit confused, but I want to thank all the people that are trying to help me.

All the various persons get together and give me the one and best answer.

Thank you for your support.

Jorge

---

### Post by beew on 2010-10-03
Add medibuntu's repo and reload synaptic and then click googleearth then install.

Can you delete message #33?? For some reason there is lot of white space in between and if you start at the beginning of the page you can never get to the end. Thanks

---

### Post by jrgonzalez on 2010-10-03
> **beew said:**
> Add medibuntu's repo and reload synaptic and then click googleearth then install.

Can you delete message #33?? For some reason there is lot of white space in between and if you start at the beginning of the page you can never get to the end. Thanks

OK. First thing: I have never deleted messages from the Forum. How do I do that?

What is medibuntu's repo and how do I get it into Synaptic.

I have used synaptic more often, so I feel better about using it, rather the cumbersome command line.

I will wait for your reply.

Thanks. 

Jorge

---

### Post by mikewhatever on 2010-10-03
> **jrgonzalez said:**
> OK guys, I have Karmic Koala 9.10

Karmic? OK, how do you know? The easiest way to find out is to look at System->Admin->System Monitor, the System tab. 

> I have un-installed the old package.

Do I re-intall them again using the Synaptic Package Manager?

There are now three lines that show, in the Synaptic Package Manager, and now they are all unchecked,

Binary files, data and package. are the three lines.

Do I re-install those again? I am getting a little bit confused, but I want to thank all the people that are trying to help me.

All the various persons get together and give me the one and best answer.

Thank you for your support.

Jorge

Wait, I thought packages from Synaptic didn't work for you. How exactly did you install it the very first time?
Here is a comprehensive installation howto -> [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by beew on 2010-10-03
> **jrgonzalez said:**
> OK. First thing: I have never deleted messages from the Forum. How do I do that?

What is medibuntu's repo and how do I get it into Synaptic.

I have used synaptic more often, so I feel better about using it, rather the cumbersome command line.

I will wait for your reply.

Thanks. 

Jorge


You can't really delete the message header but you can delete its content by edit.

I posted a link on  how to install from Medibuntu twice and another person has posted the same link too. Just go back up a few messages (it will be easier if you get rid of #33 first :)) Yes, you will be using Synaptic but in order for Synaptic to fetch the packages you have to add the Medibuntu to Synaptic's (actually apt's) source list and the link tells you how to.

---

### Post by Hakunka-Matata on 2010-10-03
Jorge I can understand how you'd be a little confused at this point, you've rxed lots of suggestions, good job hanging in there.  I agree with beew that it's time to clean things up and start over.  

Medibuntu repository is necessary. 

Synaptic Package Manager to search for and install googleearth.

When the dust settles you might want to read this [http://chrisjohnston.org/2009/how-to-setup-the-perfect-karmic-desktop]("http://chrisjohnston.org/2009/how-to-setup-the-perfect-karmic-desktop"), it's a good article on configuring (And cleaning up failed installs, etc.) on a Karmic Koala 9.10 system.  Short & Sweet -

Que Le vaya bien

---

### Post by jrgonzalez on 2010-10-03
> **mikewhatever said:**
> Karmic? OK, how do you know? The easiest way to find out is to look at System->Admin->System Monitor, the System tab. 

Wait, I thought packages from Synaptic didn't work for you. How exactly did you install it the very first time?
Here is a comprehensive installation howto -> [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

I used System > About Ubuntu, to find out what version I had.

The packages that are in synaptic (both the checked, installed and the unchecked, not installed came with my last version update, using the Update Manager, which I try to run every couple of weeks or so. 

Google Earth has never worked with my Karmic Koala version.

I will go to the comprehensive installation and read it. The only problem with Linux is that some of the instructions are not in an easy to understand language, and at times it is extremely confusing. Some times it is not very user friendly, but I understand that. I just have to get used to the jargon.

I will come back soon after I read the comprehensive installation instructions.

OK I am back. I am going to use the alternative installation.

I am not in a hurry. I will come back if it does not work.

I want to thank everyone that has helped me. MUCHAS GRACIAS!

JRG

---

### Post by jrgonzalez on 2010-10-03
VICTORY! VICTORY! VICTORY!

Whith the help of everyone, I finally got it installed and it is working.

I used the alternative installation, which I found less confusing, and IT WORKED LIKE A CHARM.

I do not know why the Synaptic installation blew up on me.

I have bookmarked the installation instructions.

Again, thanks to everyone involved for your patience in helping me.

JRG

P.S. I learned a lot from this experience.

---

### Post by mikewhatever on 2010-10-03
Well, congratulations.O:)

---

### Post by Hakunka-Matata on 2010-10-03
You're welcome Jorge, Well done, of course the command line 'CLI' is confusing at first, but it really is a great, fast way to get things done.  

CIAO

---

### Post by irpsit on 2010-12-24
[B]With this I hope to finish the problem for everyone.
[/B]
To Install Google Earth run these commands:

> sudo apt-get install googleearth-package
(this alone does not install the program!)

> sudo make-googleearth-package --force
(this step takes big time, but it's necessary)

> sudo dpkg -i ./googleearth_5.1.3535.3218+0.5.7-1_i386.deb
(the file name may be different, just browse in /home, or in the last line of the output of last command)

Go to Applications - Internet - Google Earth

If it does not launch, then do

> sudo apt-get install lsb-core

Or you might have to install the following packages:
> sudo aptitude install ttf-dejavu
sudo aptitude install ttf-bitstream-vera
sudo aptitude install msttcorefonts
sudo aptitude install lib32nss-mdns

After this, it should run. But sometimes start-up tips make the software crash
 
So, follow this fix, if Google Earth crashes: 
(applies to Maverick or Lucid)

> gedit ~/.config/Google/GoogleEarthPlus.conf

Now, search for "enableTips" inside the conf file and if it exists, change its value from "true" to "false". If it does not exist, you need to add the following under "[General]" category.

> enableTips=false

Save and Exit. Done. Now try launching Google Earth in Ubuntu, all's going to be fine.

---

