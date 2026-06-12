---
title: "file or dir."
date: 2011-04-09
forum: New to Ubuntu
---

### Post by bj218 on 2011-04-09
Could someone please explain what constitutes a file or dir. see the
following? 
 bill@bill-desktop:~$ sudo rm -R  /media/homeubu
rm: cannot remove `/media/homeubu': No such file or directory
bill@bill-desktop:~$ rm /media/homeubu
rm: cannot remove `/media/homeubu': Is a directory

---

### Post by Old *ix Geek on 2011-04-09
Right now, I'm guessing it's a directory, but we'll be sure after you post the output of **ls -l**.

---

### Post by bj218 on 2011-04-09
> **Old *ix Geek said:**
> Right now, I'm guessing it's a directory, but we'll be sure after you post the output of **ls -l**.
/media/homeubu is a hard disk partition.

bill@bill-desktop:~$ sudo ls -l
[sudo] password for bill: 
total 28232
-rw------- 1 bill bill   272446 2011-03-12 14:55 bookmarks 31211.html
drwxr-xr-x 3 bill bill     4096 2011-04-09 14:37 Desktop
drwxr-xr-x 2 bill bill     4096 2011-04-09 14:38 Documents
drwxr-xr-x 2 bill bill     4096 2011-04-06 17:28 Downloads
-rw-r--r-- 1 bill bill      167 2010-12-31 14:28 examples.desktop
-rw-r--r-- 1 bill bill    13932 2011-04-09 11:54 House Heater Inst..odt
drwxr-xr-x 2 bill bill     4096 2010-12-31 14:33 Music
-rw-r--r-- 1 bill bill 28558478 2011-01-21 15:30 NVIDIA-Linux-x86-260.19.36.run
drwxr-xr-x 2 bill bill     4096 2010-12-31 14:33 Pictures
drwxr-xr-x 2 bill bill     4096 2010-12-31 14:33 Public
drwxr-xr-x 2 bill bill     4096 2010-12-31 14:33 Templates
-rw-r--r-- 1 bill bill    18369 2011-03-29 13:53 testdisk.log
drwxr-xr-x 2 bill bill     4096 2010-12-31 14:33 Videos
bill@bill-desktop:~$

---

### Post by Old *ix Geek on 2011-04-09
Sorry, I'm a bit distracted right now--my mom's not doing well--I should have said to post the output of ls -al while in /media.

---

### Post by AlphaLexman on 2011-04-09
> **bj218 said:**
> /media/homeubu is a hard disk partition.

You cannot remove/delete a disk partition from the command line with 'rm' !!

---

### Post by bj218 on 2011-04-09
> **Old *ix Geek said:**
> Sorry, I'm a bit distracted right now--my mom's not doing well--I should have said to post the output of ls -al while in /media.

/media/homeubu is a partition on my A drive & ubuntu is on my C drive!!

bill@bill-desktop:~$ sudo ls -al
[sudo] password for bill: 
ls: cannot access .gvfs: Permission denied
total 28572
drwxr-xr-x 43 bill bill     4096 2011-04-09 14:38 .
drwxr-xr-x  3 root root     4096 2010-12-31 14:28 ..
drwx------  4 bill bill     4096 2011-02-15 11:31 .adobe
-rw-------  1 bill bill     8755 2011-04-08 16:51 .bash_history
-rw-r--r--  1 bill bill      220 2010-12-31 14:28 .bash_logout
-rw-r--r--  1 bill bill     3180 2010-12-31 14:28 .bashrc
-rw-------  1 bill bill   272446 2011-03-12 14:55 bookmarks 31211.html
drwx------  4 bill bill     4096 2011-04-02 10:38 .cache
drwx------  3 bill bill     4096 2011-01-21 15:49 .compiz
drwxr-xr-x 10 bill bill     4096 2011-03-29 10:47 .config
drwx------  2 bill bill     4096 2011-01-07 11:39 .cups
drwx------  3 bill bill     4096 2010-12-31 14:33 .dbus
drwxr-xr-x  3 bill bill     4096 2011-04-09 14:37 Desktop
drwxr-xr-x  2 bill bill     4096 2011-04-09 14:38 Documents
drwxr-xr-x  2 bill bill     4096 2011-04-06 17:28 Downloads
-rw-------  1 bill bill       16 2010-12-31 14:33 .esd_auth
-rw-r--r--  1 bill bill      167 2010-12-31 14:28 examples.desktop
drwxr-xr-x  2 bill bill     4096 2011-04-05 17:35 .fontconfig
drwx------  4 bill bill     4096 2011-04-09 11:44 .gconf
drwx------  2 bill bill     4096 2011-04-09 14:53 .gconfd
drwx------  4 bill bill     4096 2011-03-29 10:46 .gegl-0.0
drwxr-xr-x 22 bill bill     4096 2011-03-29 10:46 .gimp-2.6
-rw-r-----  1 bill bill        0 2011-04-05 17:21 .gksu.lock
drwx------ 10 bill bill     4096 2011-04-08 16:51 .gnome2
drwx------  2 bill bill     4096 2010-12-31 14:33 .gnome2_private
drwx------  2 bill bill     4096 2011-04-09 11:39 .gnupg
drwxr-xr-x  2 bill bill     4096 2011-01-02 10:03 .gstreamer-0.10
-rw-r--r--  1 bill bill      132 2011-04-09 11:39 .gtk-bookmarks
d?????????  ? ?    ?           ?                ? .gvfs
-rw-r--r--  1 bill bill    13932 2011-04-09 11:54 House Heater Inst..odt
drwxr-----  2 bill bill     4096 2010-12-31 15:35 .hplip
-rw-------  1 bill bill    34200 2011-04-09 11:39 .ICEauthority
drwxr-xr-x  2 bill bill     4096 2011-03-12 15:34 .icons
drwx------  3 bill bill     4096 2011-04-06 13:38 .kde
drwx------  3 bill bill     4096 2010-12-31 14:34 .local
drwx------  3 bill bill     4096 2011-02-15 11:31 .macromedia
drwx------  3 bill bill     4096 2011-01-04 15:23 .mission-control
drwx------  4 bill bill     4096 2010-12-31 15:47 .mozilla
drwxr-xr-x  2 bill bill     4096 2010-12-31 14:33 Music
drwxr-xr-x  2 bill bill     4096 2010-12-31 14:33 .nautilus
-rw-r--r--  1 bill bill 28558478 2011-01-21 15:30 NVIDIA-Linux-x86-260.19.36.run
-rw-r--r--  1 bill bill     1205 2011-01-21 15:40 .nvidia-settings-rc
drwxr-xr-x  3 bill bill     4096 2010-12-31 14:35 .openoffice.org
drwxr-xr-x  2 bill bill     4096 2010-12-31 14:33 Pictures
-rw-r--r--  1 bill bill       37 2010-12-31 15:35 .printer-groups.xml
-rw-r--r--  1 bill bill      675 2010-12-31 14:28 .profile
drwxr-xr-x  2 bill bill     4096 2010-12-31 14:33 Public
drwx------  2 bill bill     4096 2011-04-09 11:39 .pulse
-rw-------  1 bill bill      256 2010-12-31 14:33 .pulse-cookie
-rw-------  1 bill bill    21624 2011-04-09 14:38 .recently-used
-rw-------  1 bill bill    80792 2011-04-09 14:38 .recently-used.xbel
drwxrwx---  3 bill bill     4096 2011-01-07 10:13 .sane
drwx------  2 bill bill     4096 2010-12-31 14:33 .ssh
-rw-r--r--  1 bill bill        0 2010-12-31 14:52 .sudo_as_admin_successful
drwxr-xr-x  2 bill bill     4096 2010-12-31 14:33 Templates
-rw-r--r--  1 bill bill    18369 2011-03-29 13:53 testdisk.log
drwxr-xr-x  2 bill bill     4096 2011-03-12 15:34 .themes
drwx------  4 bill bill     4096 2010-12-31 14:34 .thumbnails
drwxr-xr-x  2 bill bill     4096 2010-12-31 14:53 .update-manager-core
drwx------  2 bill bill     4096 2010-12-31 14:33 .update-notifier
drwxr-xr-x  2 bill bill     4096 2010-12-31 14:33 Videos
drwxr-xr-x  2 bill bill     4096 2011-04-06 14:02 .xine
-rw-------  1 bill bill     5200 2011-04-09 14:53 .xsession-errors
-rw-------  1 bill bill     4882 2011-04-09 11:38 .xsession-errors.old
bill@bill-desktop:~$

---

### Post by hakermania on 2011-04-09
You can use
```
sudo rm -r /media/homeubu/*
``` or even better format it!

---

### Post by jerome1232 on 2011-04-09
What is it exactly your trying to achieve here?

---

### Post by AlphaLexman on 2011-04-09
> **hakermania said:**
> You can use
```
sudo rm -r /media/homeubu/*
``` or even better format it!
The above will not remove the partition, only delete the files on the partition.
> **AlphaLexman said:**
> You cannot remove/delete a disk partition from the command line with 'rm' !!
What is your quest?

---

### Post by AlphaLexman on 2011-04-09
> **bj218 said:**
> Could someone please explain what constitutes a file or dir.
Or maybe, the answer to the original question is,

See,
```
find . -type f
```
and,
```
find . -type d
```

---

### Post by bj218 on 2011-04-09
> **AlphaLexman said:**
> The above will not remove the partition, only delete the files on the partition.

What is your quest?

I am trying to get my partition back that nautilus fouled up see below.

You have a directory in media named homeubu
so when you mount homeubu in nautilus it shows up as homeubu_
delete the /media/homeubu directory and when you mount
that partition it will then be /media/homeubu and not /media/homeubu_

So unmount /media/homeubu_ and then remove that sub-directory /media/homeubu
sudo chown rick: /media/homeubu (rick = your user name) just showing how to put directory in your name in permissions. Can remove from root or sudo below either way.
sudo rm -r -v /media/homeubu

---

### Post by bj218 on 2011-04-09
> **AlphaLexman said:**
> Or maybe, the answer to the original question is,

See,
```
find . -type f
```
and,
```
find . -type d
```

Will these commands tell me what the difference is between a fie or dir.

---

### Post by jerome1232 on 2011-04-09
[http://wiki.answers.com/Q/What_is_the_difference_between_a_file_and_a_directory](http://wiki.answers.com/Q/What_is_the_difference_between_a_file_and_a_directory)


files are actual data, executables, pictures, documents etc... You could think of them as reports in a file cabinet

directories are "storage cabinets" for files. They don't actually hold any data themselves. You could think of them as drawers or folders inside a file cabinet.

---

### Post by AlphaLexman on 2011-04-09
What I **think** is happening, is you have a directory /media/homeubu/ that is the default mount point for a mount point, and mount points need to be mounted to an **empty** directory.

The previous requests asked for the 'ls -la' of your /media directory. We have not seen the results of that output yet.

Post the results of
```
cd /media; ls-la
```

By default, ubuntu removes any mount-point directories in '/media' after they are unmounted, however, if static files exist, the directory will not be deleted, and the next option is to add an underscore to the directory name, as in 'homeubu_', because 'homeubu' has files that should not be removed, so the system shifts to an additional underscore. If 'homeubu_' somehow develops static files, then the next mount will be 'homeubu__' (double underscore)

---

### Post by AlphaLexman on 2011-04-09
> **bj218 said:**
> Will these commands tell me what the difference is between a fie or dir.
Yeah, test and run them!!

---

### Post by bj218 on 2011-04-09
> **jerome1232 said:**
> [http://wiki.answers.com/Q/What_is_the_difference_between_a_file_and_a_directory](http://wiki.answers.com/Q/What_is_the_difference_between_a_file_and_a_directory)


files are actual data, executables, pictures, documents etc... You could think of them as reports in a file cabinet

directories are "storage cabinets" for files. They don't actually hold any data themselves. You could think of them as drawers or folders inside a file cabinet.

Thank you I really appreciate your comments I now have a much better under standing of what a file or dir. is.

---

### Post by JKyleOKC on 2011-04-09
Just to add a point that may at first appear to create more confusion, but is intended to help you visualize what's behind the scenes. Almost everything in Linux is a "file" but not all files are the same. That is, your keyboard is a file so far as the system is concerned, and so is your display. This "everything is a file" mantra is what makes it possible to stack commands end to end, and to write scripts to automate repetitive processes.

Now for the confusing point: even a directory is a file, but it's a special kind of file that only contains the names of other directories or files. Thus it forms a container, like a file folder or a drawer, to hold "normal" files that contain data.

The "file or directory" part of the error message just means that either a file or a directory that was named in the erring command can't be found in the system.

As for partitions, they are physical areas on the disk drive, and must be mounted into a directory for the system to find them. Be **very** careful about deleting such directories when a file is mounted there, because it will erase **all** of the data from the mounted partition!

---

### Post by bj218 on 2011-04-09
> **AlphaLexman said:**
> Yeah, test and run them!!

bill@bill-desktop:~$ find . -f
find: unknown predicate `-f'
bill@bill-desktop:~$ find . -d
now I am going to run the second command

./.gconf
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/americanexpress.com/myca/shared/summary/swf/pmfso.swf/PassMark.sol
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/americanexpress.com/myca/shared/summary/swf/pmfso.swf
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/americanexpress.com/myca/shared/summary/swf
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/americanexpress.com/myca/shared/summary
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/americanexpress.com/myca/shared
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/americanexpress.com/myca
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/americanexpress.com
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/s.ytimg.com/soundData.sol
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/s.ytimg.com
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/vizu.com
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/resources.infolinks.com/flash/ic.swf/infolinksData.sol
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/resources.infolinks.com/flash/ic.swf
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/resources.infolinks.com/flash
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/resources.infolinks.com
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/doug1izaerwt3.cloudfront.net/88b205b8b1139#/94d3700d2f6ebfc8f89fbff4570.sol
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/doug1izaerwt3.cloudfront.net/88b205b8b1139#
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/doug1izaerwt3.cloudfront.net
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/www.frontsight.com
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/ezs3.s3.amazonaws.com/com.jeroenwijering.sol
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/ezs3.s3.amazonaws.com/analytics.sol
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/ezs3.s3.amazonaws.com
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/chase.com/DataStore.sol
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV/chase.com
./.macromedia/Flash_Player/#SharedObjects/4PRPYGAV
./.macromedia/Flash_Player/#SharedObjects
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#vizu.com/settings.sol
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#vizu.com
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#chase.com/settings.sol
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#chase.com
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#resources.infolinks.com/settings.sol
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#resources.infolinks.com
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/settings.sol
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.frontsight.com/settings.sol](www.frontsight.com/settings.sol)
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.frontsight.com](www.frontsight.com)
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#ezs3.s3.amazonaws.com/settings.sol
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#ezs3.s3.amazonaws.com
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#americanexpress.com/settings.sol
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#americanexpress.com
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#doug1izaerwt3.cloudfront.net/settings.sol
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#doug1izaerwt3.cloudfront.net
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#s.ytimg.com/settings.sol
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#s.ytimg.com
./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys
./.macromedia/Flash_Player/macromedia.com/support/flashplayer
./.macromedia/Flash_Player/macromedia.com/support
./.macromedia/Flash_Player/macromedia.com
./.macromedia/Flash_Player
./.macromedia
./.gnome2_private
./.profile
./.bash_history
./.nvidia-settings-rc
./.nautilus
./.gnome2/eog
./.gnome2/accels/aisleriot
./.gnome2/accels/eog
./.gnome2/accels/nautilus
./.gnome2/accels/gedit
./.gnome2/accels/evince
./.gnome2/accels
./.gnome2/panel2.d/default/launchers
./.gnome2/panel2.d/default
./.gnome2/panel2.d
./.gnome2/file-roller
./.gnome2/gedit/gedit-2
./.gnome2/gedit
./.gnome2/yelp
./.gnome2/nautilus-scripts
./.gnome2/evince/ev-metadata.xml
./.gnome2/evince
./.gnome2/keyrings
./.gnome2/backgrounds.xml
./.gnome2
./.update-manager-core/meta-release
./.update-manager-core
./.gstreamer-0.10/registry.i486.bin
./.gstreamer-0.10
./.bash_logout
./House Heater Inst..odt
./Pictures
./.fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
./.fontconfig/66c4e81dab2854d1515144e2070527d6-x86.cache-2
./.fontconfig
./.gimp-2.6/fonts
./.gimp-2.6/brushes
./.gimp-2.6/palettes
./.gimp-2.6/toolrc
./.gimp-2.6/plug-ins
./.gimp-2.6/environ
./.gimp-2.6/colorrc
./.gimp-2.6/themerc
./.gimp-2.6/fractalexplorer
./.gimp-2.6/interpreters
./.gimp-2.6/curves
./.gimp-2.6/sessionrc
./.gimp-2.6/parasiterc
./.gimp-2.6/gfig
./.gimp-2.6/scripts
./.gimp-2.6/gradients
./.gimp-2.6/tool-options
./.gimp-2.6/templates
./.gimp-2.6/unitrc
./.gimp-2.6/dockrc
./.gimp-2.6/gtkrc
./.gimp-2.6/modules
./.gimp-2.6/levels
./.gimp-2.6/gimpressionist
./.gimp-2.6/pluginrc
./.gimp-2.6/templaterc
./.gimp-2.6/menurc
./.gimp-2.6/themes
./.gimp-2.6/controllerrc
./.gimp-2.6/gflare
./.gimp-2.6/tmp
./.gimp-2.6/patterns
./.gimp-2.6
./.config/gnome-session/saved-session
./.config/gnome-session
./.config/brasero/brasero.session
./.config/brasero
./.config/user-dirs.dirs
./.config/Trolltech.conf
./.config/keepassx/config.ini
./.config/keepassx
./.config/user-dirs.locale
./.config/compiz/compizconfig/config
./.config/compiz/compizconfig
./.config/compiz
./.config/gnome-disk-utility/ata-smart-ignore
./.config/gnome-disk-utility
./.config/gtk-2.0/gtkfilechooser.ini
./.config/gtk-2.0
./.config/menus/applications.menu
./.config/menus/settings.menu
./.config/menus
./.config/enchant
./.config
./Music
./.adobe/Flash_Player/AssetCache/T7CN453E
./.adobe/Flash_Player/AssetCache
./.adobe/Flash_Player
./.adobe/Acrobat/9.0/Security/addressbook.acrodata
./.adobe/Acrobat/9.0/Security/CRLCache
./.adobe/Acrobat/9.0/Security
./.adobe/Acrobat/9.0/UserCache.bin
./.adobe/Acrobat/9.0/Forms
./.adobe/Acrobat/9.0/Collab/Temp
./.adobe/Acrobat/9.0/Collab
./.adobe/Acrobat/9.0/AdobeIDataSync
./.adobe/Acrobat/9.0/Cache/UnixFnt09.lst
./.adobe/Acrobat/9.0/Cache/cookies.txt
./.adobe/Acrobat/9.0/Cache
./.adobe/Acrobat/9.0/Synchronizer/sync_prefs
./.adobe/Acrobat/9.0/Synchronizer
./.adobe/Acrobat/9.0/JavaScripts/glob.settings.js
./.adobe/Acrobat/9.0/JavaScripts/glob.js
./.adobe/Acrobat/9.0/JavaScripts
./.adobe/Acrobat/9.0/TMDocs.sav
./.adobe/Acrobat/9.0/Preferences/acrogre.conf
./.adobe/Acrobat/9.0/Preferences/mozilla/prefs.js
./.adobe/Acrobat/9.0/Preferences/mozilla
./.adobe/Acrobat/9.0/Preferences/reader_prefs
./.adobe/Acrobat/9.0/Preferences
./.adobe/Acrobat/9.0/SharedDataEvents
./.adobe/Acrobat/9.0/TMGrpPrm.sav
./.adobe/Acrobat/9.0/Cert/curl-ca-bundle.crt
./.adobe/Acrobat/9.0/Cert
./.adobe/Acrobat/9.0/AdobeCMapFnt09.lst
./.adobe/Acrobat/9.0
./.adobe/Acrobat
./.adobe
./bookmarks 31211.html
./.mozilla/firefox/625x13a8.default/webappsstore.sqlite
./.mozilla/firefox/625x13a8.default/prefs.js
./.mozilla/firefox/625x13a8.default/.parentlock
./.mozilla/firefox/625x13a8.default/localstore.rdf
./.mozilla/firefox/625x13a8.default/search.sqlite
./.mozilla/firefox/625x13a8.default/bookmarkbackups/bookmarks-2011-04-05.json
./.mozilla/firefox/625x13a8.default/bookmarkbackups/bookmarks-2011-04-08.json
./.mozilla/firefox/625x13a8.default/bookmarkbackups/bookmarks-2011-04-04.json
./.mozilla/firefox/625x13a8.default/bookmarkbackups/bookmarks-2011-04-03.json
./.mozilla/firefox/625x13a8.default/bookmarkbackups/bookmarks-2011-04-02.json
./.mozilla/firefox/625x13a8.default/bookmarkbackups/bookmarks-2011-04-07.json
./.mozilla/firefox/625x13a8.default/bookmarkbackups
./.mozilla/firefox/625x13a8.default/sessionstore.js
./.mozilla/firefox/625x13a8.default/urlclassifierkey3.txt
./.mozilla/firefox/625x13a8.default/mimeTypes.rdf
./.mozilla/firefox/625x13a8.default/blocklist.xml
./.mozilla/firefox/625x13a8.default/extensions
./.mozilla/firefox/625x13a8.default/chrome/userContent-example.css
./.mozilla/firefox/625x13a8.default/chrome/userChrome-example.css
./.mozilla/firefox/625x13a8.default/chrome
./.mozilla/firefox/625x13a8.default/signons.sqlite
./.mozilla/firefox/625x13a8.default/places.sqlite
./.mozilla/firefox/625x13a8.default/extensions.ini
./.mozilla/firefox/625x13a8.default/OfflineCache/index.sqlite
./.mozilla/firefox/625x13a8.default/OfflineCache
./.mozilla/firefox/625x13a8.default/Cache/301D4827d01
./.mozilla/firefox/625x13a8.default/Cache/_CACHE_002_
./.mozilla/firefox/625x13a8.default/Cache/7114A4CCd01
./.mozilla/firefox/625x13a8.default/Cache/0F503A47d01
./.mozilla/firefox/625x13a8.default/Cache/DACB946Bd01
./.mozilla/firefox/625x13a8.default/Cache/068BA96Bd01
./.mozilla/firefox/625x13a8.default/Cache/F3470786d01
./.mozilla/firefox/625x13a8.default/Cache/CBCE9F69d01
./.mozilla/firefox/625x13a8.default/Cache/695CD674d01
./.mozilla/firefox/625x13a8.default/Cache/4C2DF026d01
./.mozilla/firefox/625x13a8.default/Cache/B9987012d01
./.mozilla/firefox/625x13a8.default/Cache/008C6605d01
./.mozilla/firefox/625x13a8.default/Cache/4E66D1BAd01
./.mozilla/firefox/625x13a8.default/Cache/40A207EEd01
./.mozilla/firefox/625x13a8.default/Cache/6DA48A23d01
./.mozilla/firefox/625x13a8.default/Cache/89903351d01
./.mozilla/firefox/625x13a8.default/Cache/_CACHE_MAP_
./.mozilla/firefox/625x13a8.default/Cache/96372530d01
./.mozilla/firefox/625x13a8.default/Cache/A6BD3F48d01
./.mozilla/firefox/625x13a8.default/Cache/238F879Fd01
./.mozilla/firefox/625x13a8.default/Cache/FC10FBD1d01
./.mozilla/firefox/625x13a8.default/Cache/8C48E91Dd01
./.mozilla/firefox/625x13a8.default/Cache/74F3C4A4d01
./.mozilla/firefox/625x13a8.default/Cache/354CCC4Cd01
./.mozilla/firefox/625x13a8.default/Cache/69212029d01
./.mozilla/firefox/625x13a8.default/Cache/EC373FBFd01
./.mozilla/firefox/625x13a8.default/Cache/077F031Ad01
./.mozilla/firefox/625x13a8.default/Cache/2D49BFECd01
./.mozilla/firefox/625x13a8.default/Cache/93C47CC7d01
./.mozilla/firefox/625x13a8.default/Cache/0D0A3AC1d01
./.mozilla/firefox/625x13a8.default/Cache/2F8D3FA1d01
./.mozilla/firefox/625x13a8.default/Cache/B82B8D91d01
./.mozilla/firefox/625x13a8.default/Cache/CE48E5C8d01
./.mozilla/firefox/625x13a8.default/Cache/CC8AA087d01
./.mozilla/firefox/625x13a8.default/Cache/BAC26F92d01
./.mozilla/firefox/625x13a8.default/Cache/3FA97C4Ad01
./.mozilla/firefox/625x13a8.default/Cache/3F5370ECd01
./.mozilla/firefox/625x13a8.default/Cache/C49BCB69d01
./.mozilla/firefox/625x13a8.default/Cache/B381CA54d01
./.mozilla/firefox/625x13a8.default/Cache/2B8C6920d01
./.mozilla/firefox/625x13a8.default/Cache/BBF18058d01
./.mozilla/firefox/625x13a8.default/Cache/E843C5DCd01
./.mozilla/firefox/625x13a8.default/Cache/0D9E24EBd01
./.mozilla/firefox/625x13a8.default/Cache/EB83D6BEd01
./.mozilla/firefox/625x13a8.default/Cache/26FA7C0Bd01
./.mozilla/firefox/625x13a8.default/Cache/4CBBF33Cd01
./.mozilla/firefox/625x13a8.default/Cache/E8BBE229d01
./.mozilla/firefox/625x13a8.default/Cache/3D1B8108d01
./.mozilla/firefox/625x13a8.default/Cache/00E3FB6Dd01
./.mozilla/firefox/625x13a8.default/Cache/072D77E0d01
./.mozilla/firefox/625x13a8.default/Cache/E5EB570Bd01
./.mozilla/firefox/625x13a8.default/Cache/C6717998d01
./.mozilla/firefox/625x13a8.default/Cache/9260910Cd01
./.mozilla/firefox/625x13a8.default/Cache/D710031Fd01
./.mozilla/firefox/625x13a8.default/Cache/6750C279d01
./.mozilla/firefox/625x13a8.default/Cache/4979465Ad01
./.mozilla/firefox/625x13a8.default/Cache/E2A6DCE7d01
./.mozilla/firefox/625x13a8.default/Cache/04768E01d01
./.mozilla/firefox/625x13a8.default/Cache/0C743F35d01
./.mozilla/firefox/625x13a8.default/Cache/92341B23d01
./.mozilla/firefox/625x13a8.default/Cache/EDA8BFF1d01
./.mozilla/firefox/625x13a8.default/Cache/CF672CF4d01
./.mozilla/firefox/625x13a8.default/Cache/AFE85FDBd01
./.mozilla/firefox/625x13a8.default/Cache/6DCC6B6Ed01
./.mozilla/firefox/625x13a8.default/Cache/C97F4386d01
./.mozilla/firefox/625x13a8.default/Cache/DD5D35D2d01
./.mozilla/firefox/625x13a8.default/Cache/60BF03A2d01
./.mozilla/firefox/625x13a8.default/Cache/EEBF52A2d01
./.mozilla/firefox/625x13a8.default/Cache/F34CD6D5d01
./.mozilla/firefox/625x13a8.default/Cache/713986C0d01
./.mozilla/firefox/625x13a8.default/Cache/BED2B85Cd01
./.mozilla/firefox/625x13a8.default/Cache/3E4E6B37d01
./.mozilla/firefox/625x13a8.default/Cache/57F8C027d01
./.mozilla/firefox/625x13a8.default/Cache/5CD1FF2Bd01
./.mozilla/firefox/625x13a8.default/Cache/2E18BC63d01
./.mozilla/firefox/625x13a8.default/Cache/4AF7BAAAd01
./.mozilla/firefox/625x13a8.default/Cache/F349EA53d01
./.mozilla/firefox/625x13a8.default/Cache/45AC302Ed01
./.mozilla/firefox/625x13a8.default/Cache/4D683DAFd01
./.mozilla/firefox/625x13a8.default/Cache/7A6CB896d01
./.mozilla/firefox/625x13a8.default/Cache/EB9B7099d01
./.mozilla/firefox/625x13a8.default/Cache/4AD96D61d01
./.mozilla/firefox/625x13a8.default/Cache/9802BDF1d01
./.mozilla/firefox/625x13a8.default/Cache/A11581F8d01
./.mozilla/firefox/625x13a8.default/Cache/625B90D5d01
./.mozilla/firefox/625x13a8.default/Cache/D2742988d01
./.mozilla/firefox/625x13a8.default/Cache/935B4A68d01
./.mozilla/firefox/625x13a8.default/Cache/B3A3EC81d01
./.mozilla/firefox/625x13a8.default/Cache/CFA6E312d01
./.mozilla/firefox/625x13a8.default/Cache/F896FECFd01
./.mozilla/firefox/625x13a8.default/Cache/2ED61ED4d01
./.mozilla/firefox/625x13a8.default/Cache/54068D85d01
./.mozilla/firefox/625x13a8.default/Cache/B19AD1A1d01
./.mozilla/firefox/625x13a8.default/Cache/9199C234d01
./.mozilla/firefox/625x13a8.default/Cache/F1537A50d01
./.mozilla/firefox/625x13a8.default/Cache/373F21DFd01
./.mozilla/firefox/625x13a8.default/Cache/B2EA2277d01
./.mozilla/firefox/625x13a8.default/Cache/AE6042F2d01
./.mozilla/firefox/625x13a8.default/Cache/C4F4EE0Ed01
./.mozilla/firefox/625x13a8.default/Cache/9CD2D251d01
./.mozilla/firefox/625x13a8.default/Cache/CB8D7A52d01
./.mozilla/firefox/625x13a8.default/Cache/B9DDBEECd01
./.mozilla/firefox/625x13a8.default/Cache/6ECF926Fd01
./.mozilla/firefox/625x13a8.default/Cache/B9B13C1Dd01
./.mozilla/firefox/625x13a8.default/Cache/B1F5B434d01
./.mozilla/firefox/625x13a8.default/Cache/7B2192BFd01
./.mozilla/firefox/625x13a8.default/Cache/F4209AC9d01
./.mozilla/firefox/625x13a8.default/Cache/D5FBE9CAd01
./.mozilla/firefox/625x13a8.default/Cache/1E23B2EBd01
./.mozilla/firefox/625x13a8.default/Cache/4FF92D0Ad01
./.mozilla/firefox/625x13a8.default/Cache/45DD3DA7d01
./.mozilla/firefox/625x13a8.default/Cache/8D3DFE0Fd01
./.mozilla/firefox/625x13a8.default/Cache/62ADCA0Dd01
./.mozilla/firefox/625x13a8.default/Cache/2C053AD7d01
./.mozilla/firefox/625x13a8.default/Cache/2D7E830Cd01
./.mozilla/firefox/625x13a8.default/Cache/CBA65616d01
./.mozilla/firefox/625x13a8.default/Cache/65D4DE1Fd01
./.mozilla/firefox/625x13a8.default/Cache/B994AE49d01
./.mozilla/firefox/625x13a8.default/Cache/E6F608EBd01
./.mozilla/firefox/625x13a8.default/Cache/C458D322d01
./.mozilla/firefox/625x13a8.default/Cache/D64AB4CDd01
./.mozilla/firefox/625x13a8.default/Cache/4ECAEF6Ed01
./.mozilla/firefox/625x13a8.default/Cache/7A154C11d01
./.mozilla/firefox/625x13a8.default/Cache/CAEFBB63d01
./.mozilla/firefox/625x13a8.default/Cache/157F0249d01
./.mozilla/firefox/625x13a8.default/Cache/5F085E33d01
./.mozilla/firefox/625x13a8.default/Cache/153B5FC1d01
./.mozilla/firefox/625x13a8.default/Cache/31016992d01
./.mozilla/firefox/625x13a8.default/Cache/5484DE90d01
./.mozilla/firefox/625x13a8.default/Cache/908853BFd01
./.mozilla/firefox/625x13a8.default/Cache/4CEB94F6d01
./.mozilla/firefox/625x13a8.default/Cache/12145806d01
./.mozilla/firefox/625x13a8.default/Cache/58137A43d01
./.mozilla/firefox/625x13a8.default/Cache/1ED3D01Cd01
./.mozilla/firefox/625x13a8.default/Cache/A688E59Dd01
./.mozilla/firefox/625x13a8.default/Cache/5E45FDD0d01
./.mozilla/firefox/625x13a8.default/Cache/675D9ED4d01
./.mozilla/firefox/625x13a8.default/Cache/B3D79015d01
./.mozilla/firefox/625x13a8.default/Cache/80C3C209d01
./.mozilla/firefox/625x13a8.default/Cache/C81A00C4d01
./.mozilla/firefox/625x13a8.default/Cache/805A7A95d01
./.mozilla/firefox/625x13a8.default/Cache/718101FCd01
./.mozilla/firefox/625x13a8.default/Cache/CA0FDCD4d01
./.mozilla/firefox/625x13a8.default/Cache/7E170BD3d01
./.mozilla/firefox/625x13a8.default/Cache/1B40444Dd01
./.mozilla/firefox/625x13a8.default/Cache/BA9183DAd01
./.mozilla/firefox/625x13a8.default/Cache/9AEF4A1Bd01
./.mozilla/firefox/625x13a8.default/Cache/93024C6Cd01
./.mozilla/firefox/625x13a8.default/Cache/6FDDD2F7d01
./.mozilla/firefox/625x13a8.default/Cache/94862D8Ed01
./.mozilla/firefox/625x13a8.default/Cache/41DD02C1d01
./.mozilla/firefox/625x13a8.default/Cache/_CACHE_003_
./.mozilla/firefox/625x13a8.default/Cache/B3C57C17d01
./.mozilla/firefox/625x13a8.default/Cache/86265C93d01
./.mozilla/firefox/625x13a8.default/Cache/E3B4E2D3d01
./.mozilla/firefox/625x13a8.default/Cache/5515B99Ed01
./.mozilla/firefox/625x13a8.default/Cache/DAEFF8B2d01
./.mozilla/firefox/625x13a8.default/Cache/B00606F7d01
./.mozilla/firefox/625x13a8.default/Cache/CE6E2E3Ad01
./.mozilla/firefox/625x13a8.default/Cache/79E4BF04d01
./.mozilla/firefox/625x13a8.default/Cache/ABB957F5d01
./.mozilla/firefox/625x13a8.default/Cache/F76AD723d01
./.mozilla/firefox/625x13a8.default/Cache/A908B911d01
./.mozilla/firefox/625x13a8.default/Cache/C48BCB47d01
./.mozilla/firefox/625x13a8.default/Cache/C7636D77d01
./.mozilla/firefox/625x13a8.default/Cache/10F940DBd01
./.mozilla/firefox/625x13a8.default/Cache/A7E4B2D3d01
./.mozilla/firefox/625x13a8.default/Cache/F29E5DE6d01
./.mozilla/firefox/625x13a8.default/Cache/1D091B6Bd01
./.mozilla/firefox/625x13a8.default/Cache/3239A6C4d01
./.mozilla/firefox/625x13a8.default/Cache/2DB0F12Bd01
./.mozilla/firefox/625x13a8.default/Cache/B4A459CDd01
./.mozilla/firefox/625x13a8.default/Cache/DE28EBF6d01
./.mozilla/firefox/625x13a8.default/Cache/8BAE706Dd01
./.mozilla/firefox/625x13a8.default/Cache/C681F13Cd01
./.mozilla/firefox/625x13a8.default/Cache/B211955Dd01
./.mozilla/firefox/625x13a8.default/Cache/CAF48E68d01
./.mozilla/firefox/625x13a8.default/Cache/0DC163F7d01
./.mozilla/firefox/625x13a8.default/Cache/3DBD9EA3d01
./.mozilla/firefox/625x13a8.default/Cache/8C0B4C6Fd01
./.mozilla/firefox/625x13a8.default/Cache/094D570Bd01
./.mozilla/firefox/625x13a8.default/Cache/E169C7B3d01
./.mozilla/firefox/625x13a8.default/Cache/4899096Bd01
./.mozilla/firefox/625x13a8.default/Cache/4463E47Ad01
./.mozilla/firefox/625x13a8.default/Cache/1592B123d01
./.mozilla/firefox/625x13a8.default/Cache/FC6DDC29d01
./.mozilla/firefox/625x13a8.default/Cache/F0EF3C17d01
./.mozilla/firefox/625x13a8.default/Cache/457F047Ed01
./.mozilla/firefox/625x13a8.default/Cache/5A769B46d01
./.mozilla/firefox/625x13a8.default/Cache/E6856757d01
./.mozilla/firefox/625x13a8.default/Cache/AF422D51d01
./.mozilla/firefox/625x13a8.default/Cache/AF84D2ACd01
./.mozilla/firefox/625x13a8.default/Cache/FE481DACd01
./.mozilla/firefox/625x13a8.default/Cache/86ED18CFd01
./.mozilla/firefox/625x13a8.default/Cache/6BB2ADE7d01
./.mozilla/firefox/625x13a8.default/Cache/5E1E06CAd01
./.mozilla/firefox/625x13a8.default/Cache/A7531EE3d01
./.mozilla/firefox/625x13a8.default/Cache/2703F489d01
./.mozilla/firefox/625x13a8.default/Cache/1C4DA7B3d01
./.mozilla/firefox/625x13a8.default/Cache/7B3C263Dd01
./.mozilla/firefox/625x13a8.default/Cache/04E5C5E6d01
./.mozilla/firefox/625x13a8.default/Cache/63FD10E1d01
./.mozilla/firefox/625x13a8.default/Cache/1035B38Cd01
./.mozilla/firefox/625x13a8.default/Cache/ACD65128d01
./.mozilla/firefox/625x13a8.default/Cache/60F487CBd01
./.mozilla/firefox/625x13a8.default/Cache/9ABD1D9Fd01
./.mozilla/firefox/625x13a8.default/Cache/002C44FCd01
./.mozilla/firefox/625x13a8.default/Cache/F1AD569Fd01
./.mozilla/firefox/625x13a8.default/Cache/780B5313d01
./.mozilla/firefox/625x13a8.default/Cache/773D1732d01
./.mozilla/firefox/625x13a8.default/Cache/E80696A2d01
./.mozilla/firefox/625x13a8.default/Cache/949C23B5d01
./.mozilla/firefox/625x13a8.default/Cache/239C180Dd01
./.mozilla/firefox/625x13a8.default/Cache/_CACHE_001_
./.mozilla/firefox/625x13a8.default/Cache/592CE84Dd01
./.mozilla/firefox/625x13a8.default/Cache/74C68CE3d01
./.mozilla/firefox/625x13a8.default/Cache/BFCB4FAAd01
./.mozilla/firefox/625x13a8.default/Cache/70DD35AAd01
./.mozilla/firefox/625x13a8.default/Cache/E7F78A47d01
./.mozilla/firefox/625x13a8.default/Cache/B6251A16d01
./.mozilla/firefox/625x13a8.default/Cache/64BDE441d01
./.mozilla/firefox/625x13a8.default/Cache/5FF76E4Ad01
./.mozilla/firefox/625x13a8.default/Cache/7CFAF0CAd01
./.mozilla/firefox/625x13a8.default/Cache/C886E3D4d01
./.mozilla/firefox/625x13a8.default/Cache/8EB51AB2d01
./.mozilla/firefox/625x13a8.default/Cache/F3996BDCd01
./.mozilla/firefox/625x13a8.default/Cache/9C135BA7d01
./.mozilla/firefox/625x13a8.default/Cache/9CDE045Dd01
./.mozilla/firefox/625x13a8.default/Cache/FE6D2BE9d01
./.mozilla/firefox/625x13a8.default/Cache/722DDFF7d01
./.mozilla/firefox/625x13a8.default/Cache/7AD48149d01
./.mozilla/firefox/625x13a8.default/Cache/F163A30Ed01
./.mozilla/firefox/625x13a8.default/Cache/7E841E07d01
./.mozilla/firefox/625x13a8.default/Cache/A68E8ABEd01
./.mozilla/firefox/625x13a8.default/Cache/9D897DA2d01
./.mozilla/firefox/625x13a8.default/Cache/85004BF0d01
./.mozilla/firefox/625x13a8.default/Cache/53895610d01
./.mozilla/firefox/625x13a8.default/Cache/1E5395BCd01
./.mozilla/firefox/625x13a8.default/Cache/C526CF2Ad01
./.mozilla/firefox/625x13a8.default/Cache/C0AE39CFd01
./.mozilla/firefox/625x13a8.default/Cache/DD26CC9Cd01
./.mozilla/firefox/625x13a8.default/Cache/CCD47C28d01
./.mozilla/firefox/625x13a8.default/Cache/4BE2BE57d01
./.mozilla/firefox/625x13a8.default/Cache/65CBC69Ed01
./.mozilla/firefox/625x13a8.default/Cache/83C9DC0Bd01
./.mozilla/firefox/625x13a8.default/Cache/CAD4BDBBd01
./.mozilla/firefox/625x13a8.default/Cache/E0980B8Ad01
./.mozilla/firefox/625x13a8.default/Cache/CCA7A956d01
./.mozilla/firefox/625x13a8.default/Cache/E5F09619d01
./.mozilla/firefox/625x13a8.default/Cache/FF5FA426d01
./.mozilla/firefox/625x13a8.default/Cache/1072CF09d01
./.mozilla/firefox/625x13a8.default/Cache/372292E5d01
./.mozilla/firefox/625x13a8.default/Cache/842168AEd01
./.mozilla/firefox/625x13a8.default/Cache/9DD916C3d01
./.mozilla/firefox/625x13a8.default/Cache/9CD4AFE2d01
./.mozilla/firefox/625x13a8.default/Cache/7EFD4745d01
./.mozilla/firefox/625x13a8.default/Cache
./.mozilla/firefox/625x13a8.default/lock
./.mozilla/firefox/625x13a8.default/compreg.dat
./.mozilla/firefox/625x13a8.default/extensions.cache
./.mozilla/firefox/625x13a8.default/cookies.sqlite
./.mozilla/firefox/625x13a8.default/xpti.dat
./.mozilla/firefox/625x13a8.default/places.sqlite-journal
./.mozilla/firefox/625x13a8.default/bookmarks.html
./.mozilla/firefox/625x13a8.default/extensions.rdf
./.mozilla/firefox/625x13a8.default/XUL.mfasl
./.mozilla/firefox/625x13a8.default/permissions.sqlite
./.mozilla/firefox/625x13a8.default/search.json
./.mozilla/firefox/625x13a8.default/pluginreg.dat
./.mozilla/firefox/625x13a8.default/cert8.db
./.mozilla/firefox/625x13a8.default/urlclassifier3.sqlite
./.mozilla/firefox/625x13a8.default/key3.db
./.mozilla/firefox/625x13a8.default/formhistory.sqlite
./.mozilla/firefox/625x13a8.default/XPC.mfasl
./.mozilla/firefox/625x13a8.default/cookies.sqlite-journal
./.mozilla/firefox/625x13a8.default/compatibility.ini
./.mozilla/firefox/625x13a8.default/content-prefs.sqlite
./.mozilla/firefox/625x13a8.default/downloads.sqlite
./.mozilla/firefox/625x13a8.default/secmod.db
./.mozilla/firefox/625x13a8.default
./.mozilla/firefox/profiles.ini
./.mozilla/firefox
./.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}
./.mozilla/extensions
./.mozilla
./.xine/catalog.cache
./.xine
./.themes
.
bill@bill-desktop:~$

---

### Post by bj218 on 2011-04-09
> **AlphaLexman said:**
> What I **think** is happening, is you have a directory /media/homeubu/ that is the default mount point for a mount point, and mount points need to be mounted to an **empty** directory.

The previous requests asked for the 'ls -la' of your /media directory. We have not seen the results of that output yet.

Post the results of
```
cd /media; ls-la
```

By default, ubuntu removes any mount-point directories in '/media' after they are unmounted, however, if static files exist, the directory will not be deleted, and the next option is to add an underscore to the directory name, as in 'homeubu_', because 'homeubu' has files that should not be removed, so the system shifts to an additional underscore. If 'homeubu_' somehow develops static files, then the next mount will be 'homeubu__' (double underscore)

bill@bill-desktop:~$ cd /media/homeubu: ls -la
bash: cd: /media/homeubu:: No such file or directory
bill@bill-desktop:~$ cd /media: ls-la
bash: cd: /media:: No such file or directory
bill@bill-desktop:~$

---

### Post by AlphaLexman on 2011-04-09
> **bj218 said:**
> bill@bill-desktop:~$ find . -f
find: unknown predicate `-f'
You missed the '-type' parameter !!

---

### Post by AlphaLexman on 2011-04-09
Instead of:
> **bj218 said:**
> bill@bill-desktop:~$ find . -f
It should be:
```
find . -[COLOR="Red"]type[/COLOR] f
```

---

### Post by d3v1150m471c on 2011-04-09
directories house files

---

