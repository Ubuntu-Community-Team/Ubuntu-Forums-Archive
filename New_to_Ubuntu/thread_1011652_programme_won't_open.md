---
title: "programme won't open"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Brian_Newbie on 2008-12-15
I recently installed a personal budget package called "buddi." It installed fine and I opened directly in the GUI applications>office>buddi on the first attempt. 

Since then I must have clicked on something with within the application and it no longer opens from the GUI. In terminal, it doesn't open either and I get the following output:

brian@brian-laptop:~$ buddi
The installed Java version does not appear to be a Sun JVM.  Please set the JAVA variable in this script to the correct location of the Sun JVM.
brian@brian-laptop:~$ 

How can I open the application like I did the first time?

---

### Post by Poyntz on 2008-12-15
what is your distribution?
ie, type: ```
lsb_release -r
```
in a terminal. 

It sounds like you're program is looking for the java virtual machine in the wrong location. This suggests that either you may have installed the program for the wrong distribution, or the program has flaws. A simple symlink may be able to fix this. But we probably need to know your distribution before we can go any further

---

### Post by uniqueumang on 2008-12-15
> **Brian_Newbie said:**
> I recently installed a personal budget package called "buddi." It installed fine and I opened directly in the GUI applications>office>buddi on the first attempt. 

Since then I must have clicked on something with within the application and it no longer opens from the GUI. In terminal, it doesn't open either and I get the following output:

brian@brian-laptop:~$ buddi
The installed Java version does not appear to be a Sun JVM.  Please set the JAVA variable in this script to the correct location of the Sun JVM.
brian@brian-laptop:~$ 

How can I open the application like I did the first time?

Hey,
It seems that something happened to your java. Either java is not installed , or somehow java.home path got changed. 

First thing try following in terminal.
```

java --version

```

It should say something like 
```
java version "1.5.0"

```

If it outputs like java command not found, then best thing to do is search for "Sun Java" in synaptic package manager , look for sun-java 6 JDK . Select it and install it

---

### Post by Brian_Newbie on 2008-12-15
brian@brian-laptop:~$ lsb_release -r
Release:	8.10

brian@brian-laptop:~$ java --version
Unrecognized option: --version
Could not create the Java virtual machine.
brian@brian-laptop:~$ 

It seems something happened with my Java?

---

### Post by uniqueumang on 2008-12-15
ccan you run following in your terminal :
```
 sudo update-alternatives --config java

```

It should show list of java installed. If there is no java installed if no java installed then install one as mentioned above.

BTW : output of above code looks like following : 
 ```
here are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
          3    /usr/bin/gij-4.3
 +        4    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```

---

### Post by Brian_Newbie on 2008-12-15
I did this then pressed enter

brian@brian-laptop:~$ sudo update-alternatives --config java
[sudo] password for brian: 

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 
brian@brian-laptop:~$

---

### Post by uniqueumang on 2008-12-15
> **Brian_Newbie said:**
> I did this then pressed enter

brian@brian-laptop:~$ sudo update-alternatives --config java
[sudo] password for brian: 

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 
brian@brian-laptop:~$

can you try 

```

java -version

```

previously I thought java 5 was installed . Java --version works with java 5 while java 6 uses this new code.

---

### Post by Brian_Newbie on 2008-12-15
This is the output:

brian@brian-laptop:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)
brian@brian-laptop:~$

---

### Post by uniqueumang on 2008-12-15
btw it does mean java is installed :)

---

### Post by uniqueumang on 2008-12-15
ummmm.....try running your program now

---

### Post by Brian_Newbie on 2008-12-15
Same response from the terminal as before and it won't open from the GUI either. This budget package that I downloaded from sourceforge is not too important. I'm just curious why the package initially opened right after it downloaded but has not opened since.  

brian@brian-laptop:~$ buddi
The installed Java version does not appear to be a Sun JVM.  Please set the JAVA variable in this script to the correct location of the Sun JVM.
brian@brian-laptop:~$ 

What is the easiest way to uninstall then reinstall the package?

---

### Post by uniqueumang on 2008-12-15
I guess u used GDebi installer , or used some thing like sudo dpkg -i buddi , right?

---

### Post by Brian_Newbie on 2008-12-15
That's exactly what I used. Is there another way to install...or just forget about it?

---

### Post by uniqueumang on 2008-12-15
Try following code to uninstall :
```

sudo dpkg -r buddi


```

---

### Post by Brian_Newbie on 2008-12-15
Gdebi installer

---

### Post by uniqueumang on 2008-12-15
Reinstall now, and see how it goes.

---

### Post by Brian_Newbie on 2008-12-15
Output of that command:

brian@brian-laptop:~$ sudo dpkg -r buddi
[sudo] password for brian: 
(Reading database ... 147383 files and directories currently installed.)
Removing buddi ...
Removing `diversion of /usr/bin/buddi to /usr/bin/buddi.distrib by buddi'
Removing `diversion of /usr/bin/Buddi.jar to /usr/bin/Buddi.jar.distrib by buddi'
Removing `diversion of /usr/share/applications/buddi.desktop to /usr/share/applications/buddi.desktop.distrib by buddi'
Removing `diversion of /usr/share/icons/hicolor/16x16/apps/buddi.png to /usr/share/icons/hicolor/16x16/apps/buddi.png.distrib by buddi'
Removing `diversion of /usr/share/icons/hicolor/22x22/apps/buddi.png to /usr/share/icons/hicolor/22x22/apps/buddi.png.distrib by buddi'
Removing `diversion of /usr/share/icons/hicolor/24x24/apps/buddi.png to /usr/share/icons/hicolor/24x24/apps/buddi.png.distrib by buddi'
Removing `diversion of /usr/share/icons/hicolor/32x32/apps/buddi.png to /usr/share/icons/hicolor/32x32/apps/buddi.png.distrib by buddi'
Removing `diversion of /usr/share/icons/hicolor/36x36/apps/buddi.png to /usr/share/icons/hicolor/36x36/apps/buddi.png.distrib by buddi'
Removing `diversion of /usr/share/icons/hicolor/48x48/apps/buddi.png to /usr/share/icons/hicolor/48x48/apps/buddi.png.distrib by buddi'
Removing `diversion of /usr/share/icons/hicolor/64x64/apps/buddi.png to /usr/share/icons/hicolor/64x64/apps/buddi.png.distrib by buddi'
Removing `diversion of /usr/share/icons/hicolor/72x72/apps/buddi.png to /usr/share/icons/hicolor/72x72/apps/buddi.png.distrib by buddi'
Removing `diversion of /usr/share/icons/hicolor/96x96/apps/buddi.png to /usr/share/icons/hicolor/96x96/apps/buddi.png.distrib by buddi'
Removing `diversion of /usr/share/icons/hicolor/128x128/apps/buddi.png to /usr/share/icons/hicolor/128x128/apps/buddi.png.distrib by buddi'
Removing `diversion of /usr/share/icons/hicolor/192x192/apps/buddi.png to /usr/share/icons/hicolor/192x192/apps/buddi.png.distrib by buddi'
Removing `diversion of /usr/share/pixmaps/buddi.png to /usr/share/pixmaps/buddi.png.distrib by buddi'
Removing `diversion of /usr/share/doc/buddi/README to /usr/share/doc/buddi/README.distrib by buddi'
Removing `diversion of /usr/share/mime/packages/buddi.xml to /usr/share/mime/packages/buddi.xml.distrib by buddi'
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

brian@brian-laptop:~$ 

Package no longer shows up in the GUI under applications>office

---

### Post by uniqueumang on 2008-12-15
Yep that is what it was suppose to do. Try reinstalling now

---

### Post by Brian_Newbie on 2008-12-15
I installed it again and opened the package with Gdebi installer after it downloaded to my desktop. It appears in my office applications menu but won't open as before and I also get the same output from the terminal as before:

brian@brian-laptop:~$ buddi
The installed Java version does not appear to be a Sun JVM. Please set the JAVA variable in this script to the correct location of the Sun JVM.
brian@brian-laptop:~$

It's not a very important programme like GNU Cash. However maybe the package folders sitting on my desktop may have something to do with it? I even pressed the "reinstall" button but it just gave me the message that the same version of the package is already installed.

---

### Post by Brian_Newbie on 2008-12-15
When I used the pressed the reinstall button on the Buddi package I got this output in terminal. What does "lacks MimeType Key mean? 

(Reading database ... 147384 files and directories currently installed.)
Preparing to replace buddi 3.2.2.5 (using .../Desktop/Buddi-3.2.2.5.deb) ...
Unpacking replacement buddi ...
Setting up buddi (3.2.2.5) ...
Adding MIME information for Buddi files...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Search path is now: [/usr/share/applications]
File '/usr/share/applications/yelp.desktop' lacks MimeType key
File '/usr/share/applications/gnome-appearance-properties.desktop' lacks MimeType key
File '/usr/share/applications/gnome-volume-control.desktop' lacks MimeType key
File '/usr/share/applications/session-properties.desktop' lacks MimeType key
File '/usr/share/applications/nautilus-file-management-properties.desktop' lacks MimeType key
File '/usr/share/applications/display-properties.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/busyspheres.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/moebius.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/lockward.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/pulsar.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/antspotlight.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/matrixview.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/cosmos-slideshow.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/ubuntu_theme.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/blinkbox.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/euphoria.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/endgame.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/jigglypuff.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/swirl.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/metaballs.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/gflux.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/superquadrics.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/colorfire.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/galaxy.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/flipflop.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/flipscreen3d.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/shadebobs.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/penrose.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/gears.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/flocks.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/personal-slideshow.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/bubble3d.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/slidescreen.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/hyperspace.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/circuit.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/morph3d.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/polytopes.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/flux.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/sonar.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/spheremonics.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/molecule.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/distort.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/helios.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/lattice.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/antinspect.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/ripples.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/polyhedra.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/deco.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/moebiusgears.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/atunnel.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/glsnake.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/topblock.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/sierpinski3d.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/voronoi.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/f-spot-screensaver.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/mirrorblob.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/fuzzyflakes.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/cubestorm.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/footlogo-floaters.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/fieldlines.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/flurry.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/hufo_tunnel.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/queens.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/cyclone.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/fiberlamp.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/xlyap.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/skyrocket.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/hypertorus.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/flyingtoasters.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/lavalite.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/glslideshow.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/solarwinds.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/glblur.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/pipes.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/stonerview.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/gltext.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/hufo_smoke.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/gleidescope.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/plasma.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/glcells.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/engine.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/biof.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/glknots.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/sundancer2.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/spirographx.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/glmatrix.desktop' lacks MimeType key
File '/usr/share/applications/screensavers/glschool.desktop' lacks MimeType key
File '/usr/share/applications/pytube.desktop' lacks MimeType key
File '/usr/share/applications/vino-preferences.desktop' lacks MimeType key
File '/usr/share/applications/gnome-terminal.desktop' lacks MimeType key
File '/usr/share/applications/ndisgtk.desktop' lacks MimeType key
File '/usr/share/applications/tsclient.desktop' lacks MimeType key
File '/usr/share/applications/nautilus-home.desktop' lacks MimeType key
File '/usr/share/applications/qt4config.desktop' lacks MimeType key
File '/usr/share/applications/mahjongg.desktop' lacks MimeType key
File '/usr/share/applications/blackjack.desktop' lacks MimeType key
File '/usr/share/applications/evolution.desktop' lacks MimeType key
File '/usr/share/applications/evolution-2.2.desktop' lacks MimeType key
File '/usr/share/applications/gnome-dictionary.desktop' lacks MimeType key
File '/usr/share/applications/kde4/knetattach.desktop' lacks MimeType key
File '/usr/share/applications/kde4/Help.desktop' lacks MimeType key
File '/usr/share/applications/gnome-settings-mouse.desktop' lacks MimeType key
File '/usr/share/applications/gdmsetup.desktop' lacks MimeType key
File '/usr/share/applications/gksu.desktop' lacks MimeType key
File '/usr/share/applications/xsane.desktop' lacks MimeType key
File '/usr/share/applications/pidgin.desktop' lacks MimeType key
File '/usr/share/applications/scim-setup.desktop' lacks MimeType key
File '/usr/share/applications/nm-connection-editor.desktop' lacks MimeType key
File '/usr/share/applications/language-selector.desktop' lacks MimeType key
File '/usr/share/applications/sun-java6-policytool.desktop' lacks MimeType key
File '/usr/share/applications/songbird.desktop' lacks MimeType key
File '/usr/share/applications/gnibbles.desktop' lacks MimeType key
File '/usr/share/applications/services.desktop' lacks MimeType key
File '/usr/share/applications/gnomine.desktop' lacks MimeType key
File '/usr/share/applications/bluetooth-properties.desktop' lacks MimeType key
File '/usr/share/applications/gnome-system-log.desktop' lacks MimeType key
File '/usr/share/applications/gnometris.desktop' lacks MimeType key
File '/usr/share/applications/gnomecc.desktop' lacks MimeType key
File '/usr/share/applications/redhat-manage-print-jobs.desktop' lacks MimeType key
File '/usr/share/applications/at-properties.desktop' lacks MimeType key
File '/usr/share/applications/gcalctool.desktop' lacks MimeType key
File '/usr/share/applications/gnome-network-preferences.desktop' lacks MimeType key
File '/usr/share/applications/bug-buddy.desktop' lacks MimeType key
File '/usr/share/applications/baobab.desktop' lacks MimeType key
File '/usr/share/applications/redhat-system-config-printer.desktop' lacks MimeType key
File '/usr/share/applications/tomboy.desktop' lacks MimeType key
File '/usr/share/applications/metacity.desktop' lacks MimeType key
File '/usr/share/applications/gnect.desktop' lacks MimeType key
File '/usr/share/applications/window-properties.desktop' lacks MimeType key
File '/usr/share/applications/ubuntu-about.desktop' lacks MimeType key
File '/usr/share/applications/f-spot.desktop' lacks MimeType key
File '/usr/share/applications/polkit-gnome-authorization.desktop' lacks MimeType key
File '/usr/share/applications/gnome-panel.desktop' lacks MimeType key
File '/usr/share/applications/synaptic-kde.desktop' lacks MimeType key
File '/usr/share/applications/alacarte.desktop' lacks MimeType key
File '/usr/share/applications/redhat-my-default-printer.desktop' lacks MimeType key
File '/usr/share/applications/gnome-sound-recorder.desktop' lacks MimeType key
File '/usr/share/applications/tracker-preferences.desktop' lacks MimeType key
File '/usr/share/applications/gnome-system-monitor.desktop' lacks MimeType key
File '/usr/share/applications/asoundconf-gtk.desktop' lacks MimeType key
File '/usr/share/applications/synaptic.desktop' lacks MimeType key
File '/usr/share/applications/gnome-screenshot.desktop' lacks MimeType key
File '/usr/share/applications/nautilus.desktop' lacks MimeType key
File '/usr/share/applications/freecell.desktop' lacks MimeType key
File '/usr/share/applications/totem-gstreamer.desktop' lacks MimeType key
File '/usr/share/applications/gnome-power-preferences.desktop' lacks MimeType key
File '/usr/share/applications/jockey-gtk.desktop' lacks MimeType key
File '/usr/share/applications/seahorse.desktop' lacks MimeType key
File '/usr/share/applications/gnome-app-install-xfce.desktop' lacks MimeType key
File '/usr/share/applications/gnobots2.desktop' lacks MimeType key
File '/usr/share/applications/ooo-template.desktop' lacks MimeType key
File '/usr/share/applications/glines.desktop' lacks MimeType key
File '/usr/share/applications/keybinding.desktop' lacks MimeType key
File '/usr/share/applications/update-manager.desktop' lacks MimeType key
File '/usr/share/applications/orca.desktop' lacks MimeType key
File '/usr/share/applications/gnome-volume-properties.desktop' lacks MimeType key
File '/usr/share/applications/gnotski.desktop' lacks MimeType key
File '/usr/share/applications/iagno.desktop' lacks MimeType key
File '/usr/share/applications/gnotravex.desktop' lacks MimeType key
File '/usr/share/applications/compiz.desktop' lacks MimeType key
File '/usr/share/applications/gtali.desktop' lacks MimeType key
File '/usr/share/applications/ndisgtk-kde.desktop' lacks MimeType key
File '/usr/share/applications/gmenu-simple-editor.desktop' lacks MimeType key
File '/usr/share/applications/kde/kresources.desktop' lacks MimeType key
File '/usr/share/applications/gnome-screensaver-preferences.desktop' lacks MimeType key
File '/usr/share/applications/sol.desktop' lacks MimeType key
File '/usr/share/applications/gnome-about-me.desktop' lacks MimeType key
File '/usr/share/applications/gdmphotosetup.desktop' lacks MimeType key
File '/usr/share/applications/gnome-about.desktop' lacks MimeType key
File '/usr/share/applications/openjdk-6-policytool.desktop' lacks MimeType key
File '/usr/share/applications/network-scheme.desktop' lacks MimeType key
File '/usr/share/applications/seahorse-pgp-preferences.desktop' lacks MimeType key
File '/usr/share/applications/shares.desktop' lacks MimeType key
File '/usr/share/applications/gnome-search-tool.desktop' lacks MimeType key
File '/usr/share/applications/gtkpod.desktop' lacks MimeType key
File '/usr/share/applications/users.desktop' lacks MimeType key
File '/usr/share/applications/gdmflexiserver-xnest.desktop' lacks MimeType key
File '/usr/share/applications/gstreamer-properties.desktop' lacks MimeType key
File '/usr/share/applications/gdmflexiserver.desktop' lacks MimeType key
File '/usr/share/applications/gconf-editor.desktop' lacks MimeType key
File '/usr/share/applications/ekiga.desktop' lacks MimeType key
File '/usr/share/applications/python2.5.desktop' lacks MimeType key
File '/usr/share/applications/same-gnome.desktop' lacks MimeType key
File '/usr/share/applications/gnome-settings-sound.desktop' lacks MimeType key
File '/usr/share/applications/grip.desktop' lacks MimeType key
File '/usr/share/applications/winff.desktop' lacks MimeType key
File '/usr/share/applications/hwtest-gtk.desktop' lacks MimeType key
File '/usr/share/applications/keyboard.desktop' lacks MimeType key
File '/usr/share/applications/time.desktop' lacks MimeType key
File '/usr/share/applications/gnome-nettool.desktop' lacks MimeType key
File '/usr/share/applications/nautilus-computer.desktop' lacks MimeType key
File '/usr/share/applications/gucharmap.desktop' lacks MimeType key
File '/usr/share/applications/gnome-app-install.desktop' lacks MimeType key
File '/usr/share/applications/usb-creator.desktop' lacks MimeType key
File '/usr/share/applications/tracker-search-tool.desktop' lacks MimeType key
File '/usr/share/applications/gpilotd-control-applet.desktop' lacks MimeType key
File '/usr/share/applications/default-applications.desktop' lacks MimeType key
File '/usr/share/applications/evolution-mail.desktop' lacks MimeType key
File '/usr/share/applications/gnome-sudoku.desktop' lacks MimeType key
File '/usr/share/applications/firestarter.desktop' lacks MimeType

---

### Post by Brian_Newbie on 2008-12-15
I installed the newer version buddi 3.3.0.0 but instead downloaded the .jar rather than the .deb. I found I could open it with openjdk simply by right clicking the file name. Thanks for all your help.

---

