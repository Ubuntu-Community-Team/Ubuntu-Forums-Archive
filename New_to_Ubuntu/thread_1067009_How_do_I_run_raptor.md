---
title: "How do I run raptor?"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Gotaro on 2009-02-11
I installed raptor, following all of the instructions on the site.  Everything was successful, but when I try to type "raptor-menu", nothing happens.  How do I run it?

---

### Post by Gotaro on 2009-02-11
Bump..  :(

---

### Post by LowSky on 2009-02-11
[http://www.bioinformaticssolutions.com/support/manuals/rap40.php#lr](http://www.bioinformaticssolutions.com/support/manuals/rap40.php#lr)

in terminal, go to place you installed this application to

```
cd */path/to/file* 
```

then run command

```
raptor_gui
```


if you cant find it search your files oand folders for RAPTOR_GUI.sh

---

### Post by Gotaro on 2009-02-11
Doing a search in / for "raptor*" didn't return a RAPTOR_GUI.sh.  I can't find anything that will run..  :(
These are the folders I have: raptorplugins, raptorapp, raptor-menu, and raptor-utils.  The link you gave says there should be a RAPTOR/ folder.
Wait lol..  the site you linked to isn't the same Raptor!  Lol!  This Raptor is a replacement for the Kicker menu.
These are the instructions I followed:
[http://raptor-menu.org/download](http://raptor-menu.org/download)

---

### Post by sunexplodes on 2009-02-11
Could you open a terminal and type "raptor-menu" there? Then let us know what it says.

---

### Post by Gotaro on 2009-02-11
> **sunexplodes said:**
> Could you open a terminal and type "raptor-menu" there? Then let us know what it says.
```
gotaro@gotaro-linux:~$ raptor-menu
bash: raptor-menu: command not found
```
And that is what it said when I got to it on the install instructions as well.

Also, this is what the search turned up:
```
file:///home/gotaro/Downloads/raptormenu
file:///home/gotaro/Downloads/raptormenu/build/lib/raptormenu_automoc.cpp
file:///home/gotaro/Downloads/raptormenu/build/lib/raptormenu_automoc.cpp.files
file:///home/gotaro/Downloads/raptormenu/build/lib/raptormenu_classic.so
file:///home/gotaro/Downloads/raptormenu/build/lib/raptormenu_nuno.so
file:///home/gotaro/Downloads/raptormenu/build/lib/CMakeFiles/raptormenu.dir
file:///home/gotaro/Downloads/raptormenu/build/lib/CMakeFiles/raptormenu.dir/raptormenu_automoc.o
file:///home/gotaro/Downloads/raptormenu/build/plugins/bg/classic/raptormenu_classic_automoc.cpp
file:///home/gotaro/Downloads/raptormenu/build/plugins/bg/classic/raptormenu_classic_automoc.cpp.files
file:///home/gotaro/Downloads/raptormenu/build/plugins/bg/classic/CMakeFiles/raptormenu_classic.dir
file:///home/gotaro/Downloads/raptormenu/build/plugins/bg/classic/CMakeFiles/raptormenu_classic.dir/raptormenu_classic_automoc.o
file:///home/gotaro/Downloads/raptormenu/build/plugins/bg/fancy/raptorfancybackground_automoc.cpp
file:///home/gotaro/Downloads/raptormenu/build/plugins/bg/fancy/raptorfancybackground_automoc.cpp.files
file:///home/gotaro/Downloads/raptormenu/build/plugins/bg/fancy/CMakeFiles/raptorfancybackground.dir
file:///home/gotaro/Downloads/raptormenu/build/plugins/bg/fancy/CMakeFiles/raptorfancybackground.dir/raptorfancybackground_automoc.o
file:///home/gotaro/Downloads/raptormenu/build/plugins/ui/nuno/raptormenu_nuno_automoc.cpp
file:///home/gotaro/Downloads/raptormenu/build/plugins/ui/nuno/raptormenu_nuno_automoc.cpp.files
file:///home/gotaro/Downloads/raptormenu/build/plugins/ui/nuno/CMakeFiles/raptormenu_nuno.dir
file:///home/gotaro/Downloads/raptormenu/build/plugins/ui/nuno/CMakeFiles/raptormenu_nuno.dir/raptormenu_nuno_automoc.o
file:///home/gotaro/Downloads/raptormenu/build/util/raptorhelper_automoc.cpp
file:///home/gotaro/Downloads/raptormenu/build/util/raptorhelper_automoc.cpp.files
file:///home/gotaro/Downloads/raptormenu/build/util/CMakeFiles/raptorhelper.dir
file:///home/gotaro/Downloads/raptormenu/build/util/CMakeFiles/raptorhelper.dir/raptorhelper_automoc.o
file:///home/gotaro/Downloads/raptormenu/lib/raptor_exports.h
file:///home/gotaro/Downloads/raptormenu/lib/raptormenu_export.h
file:///home/gotaro/Downloads/raptormenu/lib/raptor-uiplugin.desktop
file:///home/gotaro/Downloads/raptormenu/lib/servicetype/raptor-backdropplugin.desktop
file:///home/gotaro/Downloads/raptormenu/lib/servicetype/raptor-dataplugin.desktop
file:///home/gotaro/Downloads/raptormenu/lib/servicetype/raptor-ui.desktop
file:///home/gotaro/Downloads/raptormenu/lib/servicetype/.svn/prop-base/raptor-backdropplugin.desktop.svn-base
file:///home/gotaro/Downloads/raptormenu/lib/servicetype/.svn/prop-base/raptor-dataplugin.desktop.svn-base
file:///home/gotaro/Downloads/raptormenu/lib/servicetype/.svn/prop-base/raptor-ui.desktop.svn-base
file:///home/gotaro/Downloads/raptormenu/lib/servicetype/.svn/text-base/raptor-backdropplugin.desktop.svn-base
file:///home/gotaro/Downloads/raptormenu/lib/servicetype/.svn/text-base/raptor-dataplugin.desktop.svn-base
file:///home/gotaro/Downloads/raptormenu/lib/servicetype/.svn/text-base/raptor-ui.desktop.svn-base
file:///home/gotaro/Downloads/raptormenu/lib/.svn/text-base/raptor_exports.h.svn-base
file:///home/gotaro/Downloads/raptormenu/lib/.svn/text-base/raptormenu_export.h.svn-base
file:///home/gotaro/Downloads/raptormenu/lib/.svn/text-base/raptor-uiplugin.desktop.svn-base
file:///home/gotaro/Downloads/raptormenu/libtom/RaptorTom
file:///home/gotaro/Downloads/raptormenu/libtom/.svn/text-base/RaptorTom.svn-base
file:///home/gotaro/Downloads/raptormenu/plugins/ui/nuno/raptormenu-nuno.desktop
file:///home/gotaro/Downloads/raptormenu/plugins/ui/nuno/.svn/text-base/raptormenu-nuno.desktop.svn-base
file:///usr/local/lib/raptorplugins
file:///usr/local/lib/kde4/raptormenu_classic.so
file:///usr/local/lib/kde4/raptormenu_nuno.so
file:///usr/local/share/apps/raptorapp
file:///usr/local/share/apps/desktoptheme/default/raptor-menu
file:///usr/local/share/kde4/services/raptormenu-nuno.desktop
file:///usr/local/share/kde4/servicetypes/raptor-backdropplugin.desktop
file:///usr/local/share/kde4/servicetypes/raptor-dataplugin.desktop
file:///usr/local/share/kde4/servicetypes/raptor-ui.desktop
file:///usr/share/doc/raptor-utils
file:///usr/share/soprano/plugins/raptorparser.desktop
file:///usr/share/soprano/plugins/raptorserializer.desktop
file:///usr/share/thunderbird/res/samples/raptor.jpg
file:///var/cache/e17_src/MISC/gevas2/demo/raptor2.jpg
file:///var/cache/e17_src/MISC/gevas2/demo/raptor.png
file:///var/cache/e17_src/MISC/gevas2/demo/.svn/prop-base/raptor2.jpg.svn-base
file:///var/cache/e17_src/MISC/gevas2/demo/.svn/prop-base/raptor.png.svn-base
file:///var/cache/e17_src/MISC/gevas2/demo/.svn/text-base/raptor2.jpg.svn-base
file:///var/cache/e17_src/MISC/gevas2/demo/.svn/text-base/raptor.png.svn-base
file:///var/lib/dpkg/info/raptor-utils.list
file:///var/lib/dpkg/info/raptor-utils.md5sums
```

---

### Post by sunexplodes on 2009-02-11
Now, I haven't been using KDE much lately, but it seems to me that Raptor is the kind of thing that would be a Plasmoid to be added to the panel, not a stand-alone app. Have you checked the plasmoid list to see if it's in there?

---

### Post by Gotaro on 2009-02-11
> **sunexplodes said:**
> Now, I haven't been using KDE much lately, but it seems to me that Raptor is the kind of thing that would be a Plasmoid to be added to the panel, not a stand-alone app. Have you checked the plasmoid list to see if it's in there?
Yeah, I thought of that, too.  But no, it's not there, either.  Right now I'm going through all of the folders to see if there's a file in one that I can add manually to the list..

Edit--
Here's a difference in the INSTALL text file that came with the download and what was on the site.  The last line in the text file is:
raptormenubin

..but running that in a terminal doesn't do anything, either.  I'm not sure which folder to be in..  but I was in the make directory.

---

### Post by Gotaro on 2009-02-11
Okay..  I'm not *exactly* sure this is even a working project.  There are no youtube vids of it, and I've seen a couple posts from google that make it sound like it's just recently been picked up after being abandoned.  But then there are also plenty of random google posts that make it sound like people have it working, so..  I don't know..

---

