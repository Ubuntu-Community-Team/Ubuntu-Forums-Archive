---
title: "gedit crashes"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by oboedad55 on 2010-10-24
I'm running Meerkat with a new install, no upgrade. When I go to open a text file with gedit it crashes with this error: Gtk:ERROR:/build/buildd/gtk+2.0-2.22.0/gtk/gtkrecentmanager.c:1942:get_icon_fallback: assertion failed: (retval != NULL)
Aborted


Any ideas?

---

### Post by ArgusVision on 2010-10-24
Hmm. It might not be the best answer but, I would likely go to synaptic and completely remove gedit including config's. Then re-install.

---

### Post by garvinrick4 on 2010-10-24
```
I think I would toss gedit out and replace with new one from repositories not your own cache of packages. Seems to have oodles of dependencys
rick@rick-HP-G71-Notebook-PC:~$ aptitude show gedit
Package: gedit                    
State: installed
Automatically installed: no
Version: 2.30.3-1ubuntu1
Priority: optional
Section: gnome
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 2,044k
Depends: gconf2 (>= 2.28.1-2), python (>= 2.5), python-support (>= 0.90.0),
         libatk1.0-0 (>= 1.29.3), libc6 (>= 2.4), libcairo2 (>= 1.2.4),
         libenchant1c2a (>= 1.6), libfontconfig1 (>= 2.8.0), libfreetype6 (>=
         2.2.1), libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.21.6),
         libglib2.0-0 (>= 2.24.0), libgtk2.0-0 (>= 2.20.0),
         libgtksourceview2.0-0 (>= 2.10.0), libice6 (>= 1:1.0.0),
         liblaunchpad-integration1 (>= 0.1.17), libpango1.0-0 (>= 1.14.0),
         libpython2.6 (>= 2.6), libsm6, libx11-6, libxml2 (>= 2.7.4), zlib1g (>=
         1:1.1.4), gedit-common (>= 2.30), gedit-common (< 2.31),
         python-gtksourceview2 (>= 2.9.2), python-gobject (>= 2.15.4),
         python-gtk2 (>= 2.12.0), iso-codes
Recommends: zenity, python-gnome2
Conflicts: gedit-common (<= 2.10.5-1)
Breaks: seahorse (< 2.24), seahorse-plugins (< 2.26)
Replaces: gedit-common (< 2.16.2-3)
Description: official text editor of the GNOME desktop environment
 gedit is a text editor which supports most standard editor features, extending
 this basic functionality with other features not usually found in simple text
 editors. gedit is a graphical application which supports editing multiple text
 files in one window (known sometimes as tabs or MDI). 
 
 gedit fully supports international text through its use of the Unicode UTF-8
 encoding in edited files. Its core feature set includes syntax highlighting of
 source code, auto indentation and printing and print preview support. 
 
 gedit is also extensible through its plugin system, which currently includes
 support for spell checking, comparing files, viewing CVS ChangeLogs, and
 adjusting indentation levels.
Homepage: http://www.gnome.org/projects/gedit/

[CODE]sudo apt-get remove gedit
``````
sudo apt-get clean
``````
sudo apt-get install gedit
``````
sudo apt-get install -f
``````
dpkg --configure -a
```Removed it:
Cleaned your cache do not want same one again.
Installed it
dependency check
dependency check
Worth a try to get a fresh one out of repo's.[/code]

---

### Post by notty on 2010-10-24
I have this same problem with Mint 10 on my Desktop. Although my laptop is fine. It just started happening two days ago.  Changing themes fixed it for me. I switched to Elementary there are still errors but gedit starts again.
When I switch back to the offending theme "mint-x" in this case, it doesn't start happening right away.  I also noticed when gedit starts kicking out those errors and I click the gnome-menu, gnome-panels seem to crash are start again. I did reinstall out of boredom didn't apply any updates and the same thing happened.

---

### Post by oboedad55 on 2010-10-24
Thanks for both of the above replies. I too am running Mint 10 as regular Ubuntu Meerkat has some strange sound issues for me. For reasons unclear gedit fixed itself. I did, however, install a couple of other text editors just to have around. Medit looks decent. I try to stay away from Kate and other KDE stuff as I prefer to keep a straight Gnome system.  I use UltraEdit  on my Windslow box and like it a lot. It's a shame that although it's in the repos it costs $40.

---

