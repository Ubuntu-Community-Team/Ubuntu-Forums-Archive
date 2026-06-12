---
title: "Tried everything on google earth maverick"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-12-18
I have tried every trick on google earth I can find in forums and searches with no luck. Either nothing happens when I click icon or with some fixes the splash screen comes up then disappears. Worked fine in Lucid. Have tried synaptic, google download, software center, and many command like attempts with different posts.

---

### Post by davidmohammed on 2010-12-18
should be [straightforward]("http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/").

are any errors displayed if you launch google-earth from the command line...

googleearth

---

### Post by iosuna86 on 2010-12-18
That link should do the work.

Just keep in mind that in Maverick, unlike in the previous versions, once you install Google Earth, you need to open a terminal and install:

```
sudo apt-get install lsb-core
```[FONT=monospace]

[/FONT]Now you should be able to open it properly.

---

### Post by cmcanulty on 2010-12-18
I've tried that routine several times and get lots of errors probably too long to even post. Still I get splash screen for a couple of seconds then nothing.The erros will keep going forever until I close terminal.Oh I forgot this is if I try to launch from terminal
```
cmcanulty@Gateway:~$ googleearth
googleearth: command not found
cmcanulty@Gateway:~$ 
```



```
cmcanulty@Gateway:~$ sudo make-googleearth-package --force
[sudo] password for cmcanulty: 
cat: /etc/mailname: No such file or directory
--2010-12-18 12:32:53--  http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
Resolving dl.google.com... 209.85.225.93, 209.85.225.136, 209.85.225.91, ...
Connecting to dl.google.com|209.85.225.93|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 33589497 (32M) [application/octet-stream]
Saving to: `GoogleEarthLinux.bin'

100%[==================================================================================================>] 33,589,497   882K/s   in 27s     

2010-12-18 12:33:20 (1.18 MB/s) - `GoogleEarthLinux.bin' saved [33589497/33589497]

Google Earth for GNU/Linux 6.0.1.2032
Unrecognized Google Earth version; using anyway (because of --force).
Guessed Google Earth version: 6.0.1.2032
./
./setup.sh
./desktop_icons/
./desktop_icons/ec/
./desktop_icons/ec/product_logo_24.png
./desktop_icons/ec/product_logo_16.png
./desktop_icons/ec/product_logo_32.png
./desktop_icons/ec/product_logo_48.png
./desktop_icons/ec/product_logo_22.png
./desktop_icons/ec/product_logo_128.png
./desktop_icons/ec/product_logo_64.png
./desktop_icons/ec/product_logo_256.png
./desktop_icons/ec/product_logo_32.xpm
./desktop_icons/consumer/
./desktop_icons/consumer/product_logo_24.png
./desktop_icons/consumer/product_logo_16.png
./desktop_icons/consumer/product_logo_32.png
./desktop_icons/consumer/product_logo_48.png
./desktop_icons/consumer/product_logo_22.png
./desktop_icons/consumer/product_logo_128.png
./desktop_icons/consumer/product_logo_64.png
./desktop_icons/consumer/product_logo_256.png
./desktop_icons/consumer/product_logo_32.xpm
./desktop_icons/pro/
./desktop_icons/pro/product_logo_24.png
./desktop_icons/pro/product_logo_16.png
./desktop_icons/pro/product_logo_32.png
./desktop_icons/pro/product_logo_48.png
./desktop_icons/pro/product_logo_22.png
./desktop_icons/pro/product_logo_128.png
./desktop_icons/pro/product_logo_64.png
./desktop_icons/pro/product_logo_256.png
./desktop_icons/pro/product_logo_32.xpm
./README.linux
./postinstall.sh
./googleearth-data.tar
./googleearth.xpm
./googleearth-icon.png
./linux/
./linux/xdg/
./linux/xdg/xdg-desktop-menu
./linux/xdg/xdg-desktop-icon
./linux/xdg/xdg-mime
./setup.data/
./setup.data/setup.xml
./setup.data/locale/
./setup.data/locale/nl/
./setup.data/locale/nl/LC_MESSAGES/
./setup.data/locale/nl/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/nl/LC_MESSAGES/setup.mo
./setup.data/locale/es/
./setup.data/locale/es/LC_MESSAGES/
./setup.data/locale/es/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/es/LC_MESSAGES/setup.mo
./setup.data/locale/sv/
./setup.data/locale/sv/LC_MESSAGES/
./setup.data/locale/sv/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/sv/LC_MESSAGES/setup.mo
./setup.data/locale/fr/
./setup.data/locale/fr/LC_MESSAGES/
./setup.data/locale/fr/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/fr/LC_MESSAGES/setup.mo
./setup.data/locale/de/
./setup.data/locale/de/LC_MESSAGES/
./setup.data/locale/de/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/de/LC_MESSAGES/setup.mo
./setup.data/locale/it/
./setup.data/locale/it/LC_MESSAGES/
./setup.data/locale/it/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/it/LC_MESSAGES/setup.mo
./setup.data/locale/ru/
./setup.data/locale/ru/LC_MESSAGES/
./setup.data/locale/ru/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/ru/LC_MESSAGES/setup.mo
./setup.data/splash.xpm
./setup.data/config.sh
./setup.data/bin/
./setup.data/bin/Linux/
./setup.data/bin/Linux/x86_64
./setup.data/bin/Linux/amd64
./setup.data/bin/Linux/x86/
./setup.data/bin/Linux/x86/setup.gtk
./setup.data/bin/Linux/x86/setup.gtk2
./setup.data/bin/Linux/x86/uninstall
./setup.data/bin/NetBSD
./setup.data/bin/OpenBSD
./setup.data/bin/FreeBSD
./setup.data/setup.gtk2.glade
./setup.data/setup.glade
./googleearth-linux-x86.tar
./bin/
./bin/googleearth
./preuninstall.sh
mv: cannot stat `libssl.so.0.9.8': No such file or directory
Checking shlib deps: libport.so
Checking shlib deps: libviewsync.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libsgutil.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libspatial.so'
Checking shlib deps: libgps.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
Checking shlib deps: libIGSg.so
Checking shlib deps: libwmsbase.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Checking shlib deps: libgooglesearch.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libspatial.so'
Checking shlib deps: libIGOpt.so
Checking shlib deps: liblayer.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_webbrowser.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `librender.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libauth.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libwebbrowser.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libwmsbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_gui.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libspatial.so'
Checking shlib deps: libcommon_platform.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
Checking shlib deps: libmoduleframework.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
Checking shlib deps: libGLU.so.1
Checking shlib deps: libapiloader.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGMath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
Checking shlib deps: libIGCore.so
Checking shlib deps: libspatial.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Checking shlib deps: libcollada.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGExportCommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGOpt.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGAttrs.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libalchemyext.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGSg.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGMath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGGfx.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Checking shlib deps: libgoogleearth_free.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_platform.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_webbrowser.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `librender.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libauth.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libsgutil.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libreporting.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_gui.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libspatial.so'
Checking shlib deps: libsgutil.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGAttrs.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGSg.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGMath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGGfx.so'
Checking shlib deps: libQtCore.so.4
Checking shlib deps: libbasicingest.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobaseutils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libfusioncommon.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
Checking shlib deps: libicudata.so.38
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
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcommon_gui.so'
Checking shlib deps: libge_net.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libport.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libfusioncommon.so'
Checking shlib deps: liblayout.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libgeobase.so'
Checking shlib deps: libalchemyext.so
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGAttrs.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGUtils.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGMath.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGCore.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libIGGfx.so'
Checking shlib deps: libqgif.so
```

---

### Post by iosuna86 on 2010-12-18
Have you tried downloading the .deb package from the web and running it?

[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

Get the .deb package, and install it that way. 

I am running out of ideas.

---

### Post by cmcanulty on 2010-12-18
Same result very frustrating

---

### Post by davidmohammed on 2010-12-18
in your trace the first error is

mv: cannot stat `libssl.so.0.9.8': No such file or directory

to solve that try

cd googleearth
mv ./libcrypto.so.0.9.8 ./libcrypto.so.0.9.8.bak

n.b. cd <where ever it is being extracted to in your home directory>

you can try (I think) either googleearth or googleearth/googleearth-bin

to run google earth

---

### Post by sandyd on 2010-12-18
p.s. on some computers, you may have to do
```

sudo ln -s /lib/*ld*-linux.so.2 /lib/*ld*-lsb.so.3

```

---

### Post by cmcanulty on 2010-12-18
OK I think I am closer but still an error. I tries the method below
> Ok here goes, slightly convoluted but it worked for me.

1. install googleearth-package in synaptic
2. open a terminal window and run "sudo make-googleearth-package --force" (without the quotation marks).

3. This will take approx 10 mins to complete and will generate many errors, don't worry about these just now.

4. When step 3 has completed run the following command in terminal "sudo dpkg -i googleearth_5.2.1.1588+0.5.7-1_i386.deb"

5. All being well you should now have google earth in application-internet.

6. If it crashes on opening, in terminal run "gedit ~/.config/Google/GoogleEarthPlus.conf" and if the line enableTips=true exists change it to enableTips=false, if it does not exist add the line enableTips=false under the[General] heading and save the file.

Hopefully everything will then work.
From this thread
[http://ubuntuforums.org/showthread.php?t=1595339](http://ubuntuforums.org/showthread.php?t=1595339)
So i got further but still some problem I am pasting the relevant parts of the terminal output
```
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Package: googleearth
Version: 6.0.1.2032+0.5.7-1
Section: non-free/science
Priority: optional
Maintainer:  <root@Gateway>
Architecture: i386
Depends: ttf-dejavu | ttf-bitstream-vera | msttcorefonts, libc6 (>= 2.0), libc6 (>= 2.1.3), libc6 (>= 2.2), libc6 (>= 2.3), libc6 (>= 2.3.2), libc6 (>= 2.3.6-6~), libc6 (>= 2.4), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libice6 (>= 1:1.0.0), libsm6, libstdc++6 (>= 4.1.1), libx11-6, libxext6, libxrender1, nvidia-current, zlib1g (>= 1:1.1.4) 
Description: Google Earth, a 3D map/planet viewer
 Package built with googleearth-package.
dpkg-deb: building package `googleearth' in `./googleearth_6.0.1.2032+0.5.7-1_i386.deb'.
Success!
You can now install the package with e.g. sudo dpkg -i <package>.deb
cmcanulty@Gateway:~$ sudo dpkg -igoogleearth_6.0.1.2032+0.5.7-1_i386.deb
dpkg: unknown option -g

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
cmcanulty@Gateway:~$ 
```
Thanks I hope this can fix it but I must be making a mistake in step 4 above. I did change the version # to correspond with what seemed correct

---

### Post by sandyd on 2010-12-18
> **cmcanulty said:**
> OK I think I am closer but still an error. I tries the method below

From this thread
[http://ubuntuforums.org/showthread.php?t=1595339](http://ubuntuforums.org/showthread.php?t=1595339)
So i got further but still some problem I am pasting the relevant parts of the terminal output
```
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Package: googleearth
Version: 6.0.1.2032+0.5.7-1
Section: non-free/science
Priority: optional
Maintainer:  <root@Gateway>
Architecture: i386
Depends: ttf-dejavu | ttf-bitstream-vera | msttcorefonts, libc6 (>= 2.0), libc6 (>= 2.1.3), libc6 (>= 2.2), libc6 (>= 2.3), libc6 (>= 2.3.2), libc6 (>= 2.3.6-6~), libc6 (>= 2.4), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libice6 (>= 1:1.0.0), libsm6, libstdc++6 (>= 4.1.1), libx11-6, libxext6, libxrender1, nvidia-current, zlib1g (>= 1:1.1.4) 
Description: Google Earth, a 3D map/planet viewer
 Package built with googleearth-package.
dpkg-deb: building package `googleearth' in `./googleearth_6.0.1.2032+0.5.7-1_i386.deb'.
Success!
You can now install the package with e.g. sudo dpkg -i <package>.deb
cmcanulty@Gateway:~$ sudo dpkg -igoogleearth_6.0.1.2032+0.5.7-1_i386.deb
dpkg: unknown option -g

Type dpkg --help for help about installing and deinstalling packages
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked
[*] produce a lot of output - pipe it through `less' or `more' !
cmcanulty@Gateway:~$ 
```Thanks I hope this can fix it but I must be making a mistake in step 4 above. I did change the version # to correspond with what seemed correct
sudo dpkg -i googleearth_6.0.1.2032+0.5.7-1_i386.deb

---

### Post by cmcanulty on 2010-12-18
Same behavior when clicking icon or using terminal, see splash screen then nothing here is the output
```
cmcanulty@Gateway:~$ googleearth
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/cmcanulty/.googleearth/crashlogs/crashlog-4d0d49f2.txt

Please include this file if you submit a bug report to Google.
cmcanulty@Gateway:~$ 

```

---

### Post by wilee-nilee on 2010-12-18
SD has it pretty much correct, here is how I got mine to work.
[http://ubuntuforums.org/showthread.php?t=1634659](http://ubuntuforums.org/showthread.php?t=1634659)

---

### Post by cmcanulty on 2010-12-18
Just a note Google Earth worked fine until upgrade to Maverick

---

### Post by albert s on 2010-12-18
I dont think its simply the upgrade to maverick.
I had to re-install mine and Im still in 10.04
I had similar issues, the splash screen for a second or 2 then nothing.

---

### Post by cmcanulty on 2010-12-18
```
cmcanulty@Gateway:~$ sudo apt-get install lsb-core
[sudo] password for cmcanulty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lsb-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cmcanulty@Gateway:~$ ^C
cmcanulty@Gateway:~$ 

```

---

### Post by sandyd on 2010-12-18
> **cmcanulty said:**
> Same behavior when clicking icon or using terminal, see splash screen then nothing here is the output
```
cmcanulty@Gateway:~$ googleearth
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/cmcanulty/.googleearth/crashlogs/crashlog-4d0d49f2.txt

Please include this file if you submit a bug report to Google.
cmcanulty@Gateway:~$ 

```
try generating a xorg.conf and load glx as a module from there.

---

### Post by Mark_Lester on 2010-12-19
thanks for the various helpers to at least get it to attempt to start

I am now at this stage, 
> 
Xlib:  extension "GLX" missing on display ":0.0".
Google Earth has caught signal 11.
which at least is what cmcanulty is getting.

/etc/X11/xorg.conf looks like this
> 
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Option  "Audio"  "on"
    Option  "HDMI"  "all"
#    Driver    "fglrx"
EndSection


edit
and yes I've got lsb-core installed, and started the whole procedure form the top again after I got it. but to no avail.

It's such a killer app too, I really want it back [sob]

---

### Post by Yumi on 2010-12-27
No solution, just to say I have the same problem. Reinstalled 10.10 yesterday and now this trouble. Was working before with 10.10 after upgrades. Mentions in Synaptics that there is a dependency issue but does not say which one.

Michael

---

### Post by rburkartjo on 2010-12-30
the link that david posted is the one i used to install google earth on 10.10 and it worked great. pay attention to the last line- what to do if earth will note launch after intsalling. i had to do this and then it worked fine

---

### Post by cmcanulty on 2010-12-30
I did it all carefully several times but no luck splash screen comes up the crashes immediately

---

### Post by davidmohammed on 2010-12-30
try forcing google earth to start in safe graphics

in a terminal

gedit ~/.config/Google/GoogleEarthPlus.conf

search for 

DisableAdvancedFeatures=false

replace with

DisableAdvancedFeatures=true

save

googleearth

---

### Post by cmcanulty on 2010-12-30
Here is the file I see no advanced features can I just add that line? PS I tried adding line same result splash screen then nothing and yes I did add the other package suggested
(sudo apt-get install lsb-core)

```
[General]
currentVersion=6.0.1.2032
osName=Linux
KMLPath=/home/cmcanulty/.googleearth
CachePath=/home/cmcanulty/.googleearth/Cache
LogoutClean=false
SMode=true
UID="khEA2bv4hju/0BPby+Zczw=="
Key="iMtTORtinx4="
VID="AAAACjYuMC4xLjIwMzI="
defaultBrowser=true
lastTip=3
renderWarning-OGLsoftwareEmulated=false
mouseWheelSpeed=1
InvertMouseWheel=false
SwoopEnabled=true
ThrownDragEnabled=false
FlySpeed=0.171000003814697
ControllerMode=2
ReverseControls=false
ControllerEnabled=false
enableTips=false
visibleWindows-4_3=RenderWindow, ServerWindow
hiddenWindows-4_3=@Invalid()
wasFullScreen=false
lastTop=30
lastLeft=15
lastWidth=960
lastHeight=640
wasMaximized=false
shown_RenderFrame=true
shown_Ruler=false
shown_GPS=false
shown_LeftPanel=true
searchOpen=true
placesOpen=true
layersOpen=true
PolyEditXPos=69
PolyEditYPos=74
NavigatorShow=2
TimeAnimSpeed=0
TimeLoopAnim=false
TimeZoneMode=0
TimeZoneHours=0
TimeZoneMinutes=0
TimeZoneName=
numRuns=41
numRunsThisVersion=14
AlwaysUseExternalBrowser=false

[autoupdate]
InstalledVersion=6.0.1.2032

[Layer]
tourFlyTime=10
tourBalloonShow=false
tourWaitTime=3
drivingDirectionsSpeed=150
drivingDirectionsTilt=45
drivingDirectionsRange=1000
tourFlysAlongsLines=false
tourRecordingAccuracy=75

[Search]
input0-4_3=60 57 50.40n 100 51 36.01e, "lake cheko, siberia, russia", "lake cheko, siberia, rusiia"

[UsageStatistics]
firstRun\year=2010
firstRun\month=4
firstRun\day=18
firstRun\hour=16
firstRun\minute=6
firstRun\second=26
prevRun\year=2010
prevRun\month=9
prevRun\day=18
prevRun\hour=18
prevRun\minute=49
prevRun\second=33
numRuns=2
numRunsThisVersion=2
loginHistory=0
```

---

### Post by cmcanulty on 2010-12-30
I would like to try this fix from the thread but don't understand what to do I did try running googleearth from terminal no luck
> mv: cannot stat `libssl.so.0.9.8': No such file or directory

to solve that try

cd googleearth
mv ./libcrypto.so.0.9.8 ./libcrypto.so.0.9.8.bak

n.b. cd <where ever it is being extracted to in your home directory>

you can try (I think) either googleearth or googleearth/googleearth-bin

to run google earth

---

### Post by davidmohammed on 2010-12-30
interesting - I'm running version 5.1.3533.1731  

that value is in a section called [Render] which you dont have.

I enclose my .conf file for your information.  I havent tried google earth v6.

Have you tried removing google earth v6 and installing version 5?

I dont know if v6 uses a similar .conf file structure as v5.  I suppose you could copy and paste the [Render] section of mine into yours - I've no idea if this will work though.

```
[General]
currentVersion=5.1.3533.1731
osName=Linux
KMLPath=/home/dad/.googleearth
CachePath=/home/dad/.googleearth/Cache
LogoutClean=true
SMode=true
UID="pn5YvBiMqaeZP7Mgt6RDsw=="
Key="bSCIiMW3Tho="
VID="AAAADTUuMS4zNTMzLjE3MzE="
defaultBrowser=true
lastTip=3
renderWarning-OGLsoftwareEmulated=false
mouseWheelSpeed=1
InvertMouseWheel=false
SwoopEnabled=true
ThrownDragEnabled=false
FlySpeed=0.171000003814697
ControllerMode=2
ReverseControls=false
ControllerEnabled=false
enableTips=false
visibleWindows-4_3=RenderWindow, ServerWindow
hiddenWindows-4_3=@Invalid()
wasFullScreen=false
lastTop=123
lastLeft=63
lastWidth=960
lastHeight=640
wasMaximized=false
shown_RenderFrame=true
shown_Ruler=false
shown_GPS=false
shown_LeftPanel=true
searchOpen=true
placesOpen=true
layersOpen=true
PolyEditXPos=66
PolyEditYPos=77
NavigatorShow=2
TimeAnimSpeed=0
TimeLoopAnim=false
TimeZoneMode=0
TimeZoneHours=0
TimeZoneMinutes=0
TimeZoneName=
adsDisabled=false
UsageStats=false
buildingHighlight=true
allowUnsafeBalloons=false
kmlErrorHandling=0
tooltips=true
emailProvider=0

[autoupdate]
InstalledVersion=5.1.3533.1731

[Layer]
tourFlyTime=10
tourBalloonShow=false
tourWaitTime=3
drivingDirectionsSpeed=150
drivingDirectionsTilt=45
drivingDirectionsRange=1000
tourFlysAlongsLines=false
tourRecordingAccuracy=75

[Render]
FeetMiles=false
Atmosphere=false
WaterSurface=false
TextureColors=0
TextureCompressionDXTC=false
AnisotropicFiltering=0
IconSize=1
GridReference=0
ElevationExaggeration=1
TerrainQuality=-1
RenderingApi=1
DisableAdvancedFeatures=true
Antialiasing=0
PrimaryFontVersion2Family=Arial
PrimaryFontVersion2Size=12
PrimaryFontVersion2Style=0
PrimaryFontVersion2Weight=75
SecondaryFontVersion2Family=Fixed
SecondaryFontVersion2Size=12
SecondaryFontVersion2Style=0
SecondaryFontVersion2Weight=75
OverviewZoom=99
OverviewSize=34

[UsageStatistics]
firstRun\year=2010
firstRun\month=3
firstRun\day=16
firstRun\hour=21
firstRun\minute=40
firstRun\second=47
prevRun\year=2010
prevRun\month=12
prevRun\day=30
prevRun\hour=15
prevRun\minute=51
prevRun\second=3
numRuns=8
numRunsThisVersion=8
loginHistory=0

[Cache]
MemoryCacheSize=192
DiskCacheSize=2000
```

---

