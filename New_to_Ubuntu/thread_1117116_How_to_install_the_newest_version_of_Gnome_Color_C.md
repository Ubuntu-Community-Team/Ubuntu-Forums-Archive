---
title: "How to install the newest version of Gnome Color Chooser?"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2009-04-05
How do you install a tar.gz?
I rearched the Web I was told it is as easy as:
1) ```
cd name-of-program
```
2) ```
./configure
make
sudo make install
```

But, when I tried...
```
cd gnome-color-chooser-0.2.5.tar.gz
bash: cd: gnome-color-chooser-0.2.5.tar.gz: No such file or directory
```

I cannot even get past step 1. I tried even using the address to make things easier for Ubuntu to see it.
```
cd file:///home/jutumang/Desktop/gnome-color-chooser-0.2.5.tar.gz 
bash: cd: file:///home/jutumang/Desktop/gnome-color-chooser-0.2.5.tar.gz: No such file or directory
```

Still, it can't be seen, even though I copy and pasted the name and address from the actual file.

I tried using "Kompile" to install it instead, but it fails in installation because it was "uable to start sources configuration."

These things happen each time I try to install a tar.gz file. WHy is this? I am sure there is something I still do not understand about this. How can I fix this misunderstanding for once and for all?

Thank you for your time.

Take care,
RedStarYellowSun

---

### Post by null.byte on 2009-04-05
.tar.gz is a archive.
You must first extract it, using:
```

tar -zxvf archive.tar.gz -C /path/to/extract

```

Then you must cd /path/to/extract and execute these commands.

---

### Post by squaregoldfish on 2009-04-05
A tar.gz is a compressed file (similar to a ZIP file), so you have to uncompress it. If you run

```
tar xzf gnome-color-chooser-0.2.5.tar.gz
```then you should end up with a directory called gnome-color-chooser-0.2.5. Then you can follow your instructions.

Steve.

EDIT: null.byte - so you can type faster than me, can you? Well, I don't care. :lolflag:

---

### Post by gandaran on 2009-04-05
you don't need to run the tar xzf command, just right click the package, choose extract here then cd to the extract folder to install.
read the readme file for installing instructions from the extracted contents.

---

### Post by 73ckn797 on 2009-04-05
Gnome-color-chooser is available via Synaptic Package Manager. If you do not see it there enable restricted sources which may make it available.

It will install itself.

---

### Post by Paqman on 2009-04-05
> **73ckn797 said:**
> Gnome-color-chooser is available via Synaptic Package Manager. If you do not see it there enable restricted sources which may make it available.

It will install itself.

^This^

You should always install things through Synaptic if it's available. Compiling packages manually is more difficult and less effective. There's almost never any situation where you'd actually need to do it.

---

### Post by RedStarYellowSun on 2009-04-05
Thanks for your replies. I highly appreciate it.

To null.byte: Thanks for the tip. But when do you use "-zxvf" and when do you use squarefoldfish's tip of simply "xzf"?

To squaregoldfish: Thanks for the specific instructions. But unfortunately, when I tried it, I got...
```
jutumang@jutumang-laptop:~$ tar xzf gnome-color-chooser-0.2.5.tar.gz
tar: gnome-color-chooser-0.2.5.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

To gandaran: Good point! That makes things easier.

To 73ckn797: Wow! That is right. But, my source seems a bit outdated, though. It still says that the latest version is 0.2.3-2 when they already came up with 0.2.5 . How do you updare the software source?

Thanks for your time, my friends.

Take care,
RedStarYellowSun

---

### Post by Paqman on 2009-04-05
> **RedStarYellowSun said:**
> It still says that the latest version is 0.2.3-2 when they already came up with 0.2.5 . How do you updare the software source?


You can't just yet. 0.2.3-2 is the latest version in the Intrepid repos. If you upgrade to Jaunty you'll get 0.2.4-1. If the 0.2.5 version gets into the Ubuntu repos then you'll be upgraded automatically. But unless the new version contains some feature that you just can't live without I wouldn't lose sleep about what version you have.

---

### Post by 73ckn797 on 2009-04-05
> **RedStarYellowSun said:**
> Thanks for your replies. I highly appreciate it.

To null.byte: Thanks for the tip. But when do you use "-zxvf" and when do you use squarefoldfish's tip of simply "xzf"?

To squaregoldfish: Thanks for the specific instructions. But unfortunately, when I tried it, I got...
```
jutumang@jutumang-laptop:~$ tar xzf gnome-color-chooser-0.2.5.tar.gz
tar: gnome-color-chooser-0.2.5.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```To gandaran: Good point! That makes things easier.

To 73ckn797: Wow! That is right. But, my source seems a bit outdated, though. It still says that the latest version is 0.2.3-2 when they already came up with 0.2.5 . How do you updare the software source?

Thanks for your time, my friends.

Take care,
RedStarYellowSun

What is in the repositories is the latest that Ubuntu offers. If you can download a "deb" version you can install it more easily than your "tz" file.

Go to System/Accessories/Preferences and select "Main Menu". Click on "System Tools" and enable the "gdebi package installer". That will then show up under Applications/System. It will install it for you.

---

### Post by oldos2er on 2009-04-05
If you downloaded the file gnome-color-chooser-0.2.5.tar.gz to your desktop, you would first need to run "cd Desktop"

---

### Post by RedStarYellowSun on 2009-04-05
To Paqman: Thanks for the advice. I actually might take that advice if the tar.gz isn't installed soon.

To 73ckn797: Unfortunately, they do not offer tar.gz . The only other alernative was a tar.gz2 .

To oldos2er: Thanks for the advice, man. I am now 1 step closer to the solution.

It worked.
```
jutumang@jutumang-laptop:~$ cd Desktop
jutumang@jutumang-laptop:~/Desktop$
```

Unfortunately, when I treid to put the file...
```
jutumang@jutumang-laptop:~/Desktop$ cd gnome-color-chooser-0.2.5.tar.gz
bash: cd: gnome-color-chooser-0.2.5.tar.gz: Not a directory
```

Do you know how I can fix this?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by null.byte on 2009-04-06
@RedStarYellowSun:
z is to handle files that were compressed using gzip.
x is to extract the files.
v is to be verbose about what is going on there.
f is to force overwriting if it was already extracted there.

Assuming that the archive is on desktop, open a Terminal and write:
```

cd Desktop
tar -zxvf gnome-color-chooser-0.2.5.tar.gz

```

After that, you can go in the EXTRACTED folder.

---

### Post by gandaran on 2009-04-06
you can get all gnome-color-chooser .deb packages including the 0.2.5-1 [here]("http://ftp.gva.es/mirror/debian/pool/main/g/gnome-color-chooser/")

---

### Post by oldos2er on 2009-04-06
"jutumang@jutumang-laptop:~/Desktop$ cd gnome-color-chooser-0.2.5.tar.gz
bash: cd: gnome-color-chooser-0.2.5.tar.gz: Not a directory"

 You still haven't said if the file is on your desktop, or where exactly it is.

 Could you post the output of this command
```
ls -la ~/Desktop
```
?

---

### Post by arapa on 2009-04-06
> **null.byte said:**
> @RedStarYellowSun:
z is to handle files that were compressed using gzip.
x is to extract the files.
v is to be verbose about what is going on there.
f is to force overwriting if it was already extracted there.


Just wanted to clarify the **f** flag. It *does not* mean force overwrite. It lets the tar command know you are trying to extract from or compress to a **f**ile. It is not an optional flag if you are compressing/extracting a tar file.

---

### Post by null.byte on 2009-04-06
My bad, thanks. :)

---

### Post by RedStarYellowSun on 2009-04-06
To null.byte: Thanks for the info! I learned something. But the way, though, (out of curiosity) does it have to be in that specific order when written in Terminal?

To gandaran: Thanks for telling me. Unfortunately, I set this up in order to leanr how to install a tar.gz file. But if this gets too difficult, I will try it out. Thanks for the backup plan!

To oldos2er: Really? What is the difference, then of ```
 cd
``` and ```
ls -la ~/
```? When do I use one and when do I use the other?

To arapa: Thanks for the correction. It is much appreciated.

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by RedStarYellowSun on 2009-04-06
So, putting it all together according to my limited understanding ofthe topic, here is what happened:
```
jutumang@jutumang-laptop:~$ cd Desktop
jutumang@jutumang-laptop:~/Desktop$ tar -zxvf gnome-color-chooser-0.2.5.tar.gz
gnome-color-chooser-0.2.5/
gnome-color-chooser-0.2.5/m4/
gnome-color-chooser-0.2.5/m4/lf_cxx.m4
gnome-color-chooser-0.2.5/m4/lf_host_type.m4
gnome-color-chooser-0.2.5/m4/lf_warnings.m4
gnome-color-chooser-0.2.5/m4/link_as_needed.m4
gnome-color-chooser-0.2.5/m4/Makefile.am
gnome-color-chooser-0.2.5/m4/Makefile.in
gnome-color-chooser-0.2.5/README
gnome-color-chooser-0.2.5/configure.ac
gnome-color-chooser-0.2.5/aclocal.m4
gnome-color-chooser-0.2.5/Makefile.am
gnome-color-chooser-0.2.5/Makefile.in
gnome-color-chooser-0.2.5/config.h.in
gnome-color-chooser-0.2.5/configure
gnome-color-chooser-0.2.5/AUTHORS
gnome-color-chooser-0.2.5/COPYING
gnome-color-chooser-0.2.5/ChangeLog
gnome-color-chooser-0.2.5/INSTALL
gnome-color-chooser-0.2.5/NEWS
gnome-color-chooser-0.2.5/THANKS
gnome-color-chooser-0.2.5/config.guess
gnome-color-chooser-0.2.5/config.sub
gnome-color-chooser-0.2.5/depcomp
gnome-color-chooser-0.2.5/install-sh
gnome-color-chooser-0.2.5/missing
gnome-color-chooser-0.2.5/mkinstalldirs
gnome-color-chooser-0.2.5/autogen.sh
gnome-color-chooser-0.2.5/intltool-extract.in
gnome-color-chooser-0.2.5/intltool-merge.in
gnome-color-chooser-0.2.5/intltool-update.in
gnome-color-chooser-0.2.5/po/
gnome-color-chooser-0.2.5/po/Makefile.in.in
gnome-color-chooser-0.2.5/po/POTFILES.in
gnome-color-chooser-0.2.5/po/ar.po
gnome-color-chooser-0.2.5/po/bg.po
gnome-color-chooser-0.2.5/po/cs.po
gnome-color-chooser-0.2.5/po/de.po
gnome-color-chooser-0.2.5/po/en_CA.po
gnome-color-chooser-0.2.5/po/es.po
gnome-color-chooser-0.2.5/po/fi.po
gnome-color-chooser-0.2.5/po/fr.po
gnome-color-chooser-0.2.5/po/he.po
gnome-color-chooser-0.2.5/po/hu.po
gnome-color-chooser-0.2.5/po/id.po
gnome-color-chooser-0.2.5/po/it.po
gnome-color-chooser-0.2.5/po/nb.po
gnome-color-chooser-0.2.5/po/nl.po
gnome-color-chooser-0.2.5/po/oc.po
gnome-color-chooser-0.2.5/po/pl.po
gnome-color-chooser-0.2.5/po/pt.po
gnome-color-chooser-0.2.5/po/pt_BR.po
gnome-color-chooser-0.2.5/po/ru.po
gnome-color-chooser-0.2.5/po/sv.po
gnome-color-chooser-0.2.5/po/th.po
gnome-color-chooser-0.2.5/po/tr.po
gnome-color-chooser-0.2.5/po/zh_CN.po
gnome-color-chooser-0.2.5/po/ChangeLog
gnome-color-chooser-0.2.5/po/LINGUAS
gnome-color-chooser-0.2.5/src/
gnome-color-chooser-0.2.5/src/Makefile.am
gnome-color-chooser-0.2.5/src/Makefile.in
gnome-color-chooser-0.2.5/src/main.cc
gnome-color-chooser-0.2.5/src/utils.cc
gnome-color-chooser-0.2.5/src/configloader.cc
gnome-color-chooser-0.2.5/src/ioexception.cc
gnome-color-chooser-0.2.5/src/exporter.cc
gnome-color-chooser-0.2.5/src/gtpexporter.cc
gnome-color-chooser-0.2.5/src/gtkrcexporter.cc
gnome-color-chooser-0.2.5/src/mainwindow.cc
gnome-color-chooser-0.2.5/src/enginewindow.cc
gnome-color-chooser-0.2.5/src/infowindow.cc
gnome-color-chooser-0.2.5/src/validatorwindow.cc
gnome-color-chooser-0.2.5/src/modwidget.cc
gnome-color-chooser-0.2.5/src/treehandler.cc
gnome-color-chooser-0.2.5/src/checkbutton.cc
gnome-color-chooser-0.2.5/src/colorbutton.cc
gnome-color-chooser-0.2.5/src/spinbutton.cc
gnome-color-chooser-0.2.5/src/fontbutton.cc
gnome-color-chooser-0.2.5/src/filechooserbutton.cc
gnome-color-chooser-0.2.5/src/slider.cc
gnome-color-chooser-0.2.5/src/combobox.cc
gnome-color-chooser-0.2.5/src/utils.h
gnome-color-chooser-0.2.5/src/configloader.h
gnome-color-chooser-0.2.5/src/exception.h
gnome-color-chooser-0.2.5/src/ioexception.h
gnome-color-chooser-0.2.5/src/exporter.h
gnome-color-chooser-0.2.5/src/gtpexporter.h
gnome-color-chooser-0.2.5/src/gtkrcexporter.h
gnome-color-chooser-0.2.5/src/mainwindow.h
gnome-color-chooser-0.2.5/src/enginewindow.h
gnome-color-chooser-0.2.5/src/infowindow.h
gnome-color-chooser-0.2.5/src/validatorwindow.h
gnome-color-chooser-0.2.5/src/modwidget.h
gnome-color-chooser-0.2.5/src/treehandler.h
gnome-color-chooser-0.2.5/src/checkbutton.h
gnome-color-chooser-0.2.5/src/colorbutton.h
gnome-color-chooser-0.2.5/src/spinbutton.h
gnome-color-chooser-0.2.5/src/fontbutton.h
gnome-color-chooser-0.2.5/src/filechooserbutton.h
gnome-color-chooser-0.2.5/src/slider.h
gnome-color-chooser-0.2.5/src/combobox.h
gnome-color-chooser-0.2.5/src/gnome-color-chooser.glade
gnome-color-chooser-0.2.5/src/gnome-color-chooser.xml.in
gnome-color-chooser-0.2.5/src/gnome-color-chooser.svg
gnome-color-chooser-0.2.5/src/gnome-color-chooser.desktop.in
gnome-color-chooser-0.2.5/src/gnome-color-chooser.1
gnome-color-chooser-0.2.5/profiles/
gnome-color-chooser-0.2.5/profiles/Makefile.am
gnome-color-chooser-0.2.5/profiles/Makefile.in
gnome-color-chooser-0.2.5/profiles/compact.xml.in
gnome-color-chooser-0.2.5/doc/
gnome-color-chooser-0.2.5/doc/Makefile.am
gnome-color-chooser-0.2.5/doc/Makefile.in
jutumang@jutumang-laptop:~/Desktop$ ls -la ~/Desktop
total 1248
drwxr-xr-x  5 jutumang jutumang   4096 2009-04-06 20:02 .
drwxr-xr-x 59 jutumang jutumang   4096 2009-04-06 19:35 ..
drwxr-xr-x  7 jutumang jutumang   4096 2009-03-23 20:34 gnome-color-chooser-0.2.5
-rw-r--r--  1 jutumang jutumang 276906 2009-04-06 19:46 gnome-color-chooser-0.2.5.tar.gz
-rw-r--r--  1 jutumang jutumang    766 2009-01-12 21:20 gnome-color-chooser.desktop
drwxr-xr-x 19 jutumang jutumang  12288 2009-02-09 22:49 hplip-2.8.12
drwxr-xr-x  2 jutumang jutumang   4096 2009-01-13 20:02 Screenlets
-r--------  1 jutumang jutumang 955930 2009-03-19 21:36 The Great Falling Away.pdf
jutumang@jutumang-laptop:~/Desktop$ ls -la ~/gnome-color-chooser-0.2.5
ls: cannot access /home/jutumang/gnome-color-chooser-0.2.5: No such file or directory
jutumang@jutumang-laptop:~/Desktop$ cd gnome-color-chooser-0.2.5
jutumang@jutumang-laptop:~/Desktop/gnome-color-chooser-0.2.5$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (gtkmm-2.4 >= 2.8.0 libglademm-2.4 >= 2.6.0 libgnome-2.0 >= 2.16.0  libgnomeui-2.0 >= 2.14.0 libxml-2.0 >= 2.6.0 ) were not met:

No package 'gtkmm-2.4' found
No package 'libglademm-2.4' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

jutumang@jutumang-laptop:~/Desktop/gnome-color-chooser-0.2.5$ make
make: *** No targets specified and no makefile found.  Stop.
jutumang@jutumang-laptop:~/Desktop/gnome-color-chooser-0.2.5$ sudo make install
```

It seems that I failed in installing it becasue it was not able find all the necessary files. I can imagine that I made a mistake in my commands. Due to my igorance, though, I cannot tell what. What went wrong? How can I fix the commands?

Thanks for your time and patience.

Take care,
RedStarYellowSun

---

### Post by squaregoldfish on 2009-04-06
The programs you compile will generally depend on other code libraries, and it's these that you're missing, so you'll need to install them.

Libraries usually come in two parts - the main library itself (which is normally installed), and an extra package that contains information for compiling programs to use those libraries. These are known as dev packages.

So, in your case you're missing (amongst other things) the gtkmm package. If you look in Synaptic, you should be able to find and install the gtkmm library and its dev package from there. If you search for gtkmm, you'll probably find a package named libgtkmm or similar, and a libgtkmm-dev package to go with it. Install both of those, and do the same for the other libraries that are missing, and you should find things start to work!

Steve.

---

### Post by oldos2er on 2009-04-06
It's telling you the errors:

checking for DEPS... configure: error: Package requirements (gtkmm-2.4 >= 2.8.0 libglademm-2.4 >= 2.6.0 libgnome-2.0 >= 2.16.0  libgnomeui-2.0 >= 2.14.0 libxml-2.0 >= 2.6.0 ) were not met:

No package 'gtkmm-2.4' found
No package 'libglademm-2.4' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libxml-2.0' found

 DEPS=dependencies. You need to install the -dev packages for each of those deps listed as not found.

---

### Post by RedStarYellowSun on 2009-04-07
Wow, it worked!

Thanks for your help!
I certainly learned a lot in this intallation.

Thank you all for your time and patience.

Take care,
RedStarYellowSun

---

