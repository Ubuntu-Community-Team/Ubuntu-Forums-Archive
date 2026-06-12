---
title: "can't play music or vids?"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by Paul T. on 2009-12-09
Both Totem Movie Player & Rhythm Box music player have suddenly stopped working, if I try and start them I just get the little circular mouse icon on screen for a few seconds, then back to mouse arrow. Neither will load, what have I done?
Have tried re-installing both, but no difference.

---

### Post by sandyd on 2009-12-09
whats the output when you run 
```

rythmbox

```
in the terminal

---

### Post by Paul T. on 2009-12-09
> **carlee said:**
> whats the output when you run 
```

rythmbox

```
in the terminal


paul@paul-desktop:~$ rythmbox
No command 'rythmbox' found, did you mean:
 Command 'rhythmbox' from package 'rhythmbox' (main)
rythmbox: command not found

---

### Post by ajgreeny on 2009-12-09
Whoops!  Carlee gave you a typo to try, so now try ```
rhythmbox
``` in terminal instead, and see what errors appear from that.

---

### Post by Paul T. on 2009-12-09
paul@paul-desktop:~$ rhythmbox
Error re-scanning registry , child terminated by signal
Run 'rhythmbox --help' to see a full list of available command line options.

What does 'child terminated by signal' mean?

---

### Post by SteveNorman on 2009-12-09
vlc works best IMHO


sudo apt-get install vlc

your problem could be conflicting software/libraries post upgrade.

similar issues here
[http://ubuntuforums.org/archive/index.php/t-1305619.html](http://ubuntuforums.org/archive/index.php/t-1305619.html)

---

### Post by Paul T. on 2009-12-09
> **SteveNorman said:**
> vlc works best IMHO


sudo apt-get install vlc

your problem could be conflicting software/libraries post upgrade.

similar issues here
[http://ubuntuforums.org/archive/index.php/t-1305619.html](http://ubuntuforums.org/archive/index.php/t-1305619.html)

Steve,

installed vlc which works with video & music files thx, though having got used to Totem & Rhythmbox feel annoyed at having to re-learn a new app all over.
Totem & Rhythmbox both worked fine a few hours ago but haven't done anything AFAIK to affect them since then.

Another peculiar thing is if I go to Applications > Ubuntu Software Centre the window opens then immediately shuts down.

---

### Post by SteveNorman on 2009-12-09
I understand, Its always best to solve a problem rather than just delete it or use something else. That link I posted has some success stories in it.

Be advised that if you are removing an ap, you have to go through and find every single trace of it by hand before reinstalling.

I would do this,

sudo apt-get purge rhythmbox
sudo apt-get purge totem
sudo apt-get purge gstreamer


then

sudo updatedb
locate *rhythembox*

remove everything you see, do the same for gstreamer and totem, using updatedb often

Then reinstall the lot.


good luck

---

### Post by Paul T. on 2009-12-09
Sorry to sound like a dunce, but how do I delete all these files without trawling through all them individually:

/home/paul/.cache/rhythmbox
/home/paul/.cache/rhythmbox/covers
/home/paul/.cache/rhythmbox/jamendo
/home/paul/.cache/rhythmbox/magnatune
/home/paul/.cache/rhythmbox/covers/Bryan Adams - So Far So Good.rb-blist
/home/paul/.cache/rhythmbox/jamendo/dbdump.xml.tmp
/home/paul/.cache/rhythmbox/magnatune/song_info.xml
/home/paul/.gconf/apps/rhythmbox
/home/paul/.gconf/apps/rhythmbox/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/player
/home/paul/.gconf/apps/rhythmbox/plugins
/home/paul/.gconf/apps/rhythmbox/state
/home/paul/.gconf/apps/rhythmbox/ui
/home/paul/.gconf/apps/rhythmbox/player/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/artdisplay
/home/paul/.gconf/apps/rhythmbox/plugins/audiocd
/home/paul/.gconf/apps/rhythmbox/plugins/audioscrobbler
/home/paul/.gconf/apps/rhythmbox/plugins/cd-recorder
/home/paul/.gconf/apps/rhythmbox/plugins/daap
/home/paul/.gconf/apps/rhythmbox/plugins/generic-player
/home/paul/.gconf/apps/rhythmbox/plugins/ipod
/home/paul/.gconf/apps/rhythmbox/plugins/iradio
/home/paul/.gconf/apps/rhythmbox/plugins/jamendo
/home/paul/.gconf/apps/rhythmbox/plugins/magnatune
/home/paul/.gconf/apps/rhythmbox/plugins/mmkeys
/home/paul/.gconf/apps/rhythmbox/plugins/status-icon
/home/paul/.gconf/apps/rhythmbox/plugins/visualizer
/home/paul/.gconf/apps/rhythmbox/plugins/artdisplay/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/audiocd/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/audioscrobbler/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/cd-recorder/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/daap/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/generic-player/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/ipod/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/iradio/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/jamendo/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/magnatune/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/mmkeys/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/status-icon/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/visualizer/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/state/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/state/iradio
/home/paul/.gconf/apps/rhythmbox/state/library
/home/paul/.gconf/apps/rhythmbox/state/podcast
/home/paul/.gconf/apps/rhythmbox/state/iradio/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/state/library/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/state/podcast/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/ui/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/ui/library
/home/paul/.gconf/apps/rhythmbox/ui/library/%gconf.xml
/home/paul/.gnome2/accels/rhythmbox
/home/paul/.local/share/rhythmbox
/home/paul/.local/share/Trash/files/rhythmbox.desktop
/home/paul/.local/share/Trash/info/rhythmbox.desktop.trashinfo
/home/paul/.local/share/rhythmbox/magnatune
/home/paul/.local/share/rhythmbox/playlists.xml
/home/paul/.local/share/rhythmbox/rhythmdb.xml
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/__init__.py
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/__init__.pyc
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/braille_generator.py
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/braille_generator.pyc
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/formatting.py
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/formatting.pyc
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/script.py
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/script.pyc
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/speech_generator.py
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/speech_generator.pyc
/usr/share/app-install/desktop/rhythmbox.desktop
/usr/share/app-install/icons/rhythmbox.png
/usr/share/icons/Humanity/actions/16/rhythmbox-set-star.svg
/usr/share/icons/Humanity/actions/24/rhythmbox-set-star.svg
/usr/share/icons/Humanity/actions/48/rhythmbox-set-star.svg
/usr/share/locale-langpack/en_AU/LC_MESSAGES/rhythmbox.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/rhythmbox.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/rhythmbox.mo
/usr/share/pyshared/orca/scripts/apps/rhythmbox
/usr/share/pyshared/orca/scripts/apps/rhythmbox/__init__.py
/usr/share/pyshared/orca/scripts/apps/rhythmbox/braille_generator.py
/usr/share/pyshared/orca/scripts/apps/rhythmbox/formatting.py
/usr/share/pyshared/orca/scripts/apps/rhythmbox/script.py
/usr/share/pyshared/orca/scripts/apps/rhythmbox/speech_generator.py
/var/cache/apt/archives/rhythmbox_0.12.5-0ubuntu5_i386.deb
/var/lib/dpkg/info/rhythmbox.list
/var/lib/dpkg/info/rhythmbox.postrm

---

### Post by sandyd on 2009-12-09
> **Paul T. said:**
> Sorry to sound like a dunce, but how do I delete all these files without trawling through all them individually:

/home/paul/.cache/rhythmbox
/home/paul/.cache/rhythmbox/covers
/home/paul/.cache/rhythmbox/jamendo
/home/paul/.cache/rhythmbox/magnatune
/home/paul/.cache/rhythmbox/covers/Bryan Adams - So Far So Good.rb-blist
/home/paul/.cache/rhythmbox/jamendo/dbdump.xml.tmp
/home/paul/.cache/rhythmbox/magnatune/song_info.xml
/home/paul/.gconf/apps/rhythmbox
/home/paul/.gconf/apps/rhythmbox/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/player
/home/paul/.gconf/apps/rhythmbox/plugins
/home/paul/.gconf/apps/rhythmbox/state
/home/paul/.gconf/apps/rhythmbox/ui
/home/paul/.gconf/apps/rhythmbox/player/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/artdisplay
/home/paul/.gconf/apps/rhythmbox/plugins/audiocd
/home/paul/.gconf/apps/rhythmbox/plugins/audioscrobbler
/home/paul/.gconf/apps/rhythmbox/plugins/cd-recorder
/home/paul/.gconf/apps/rhythmbox/plugins/daap
/home/paul/.gconf/apps/rhythmbox/plugins/generic-player
/home/paul/.gconf/apps/rhythmbox/plugins/ipod
/home/paul/.gconf/apps/rhythmbox/plugins/iradio
/home/paul/.gconf/apps/rhythmbox/plugins/jamendo
/home/paul/.gconf/apps/rhythmbox/plugins/magnatune
/home/paul/.gconf/apps/rhythmbox/plugins/mmkeys
/home/paul/.gconf/apps/rhythmbox/plugins/status-icon
/home/paul/.gconf/apps/rhythmbox/plugins/visualizer
/home/paul/.gconf/apps/rhythmbox/plugins/artdisplay/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/audiocd/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/audioscrobbler/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/cd-recorder/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/daap/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/generic-player/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/ipod/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/iradio/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/jamendo/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/magnatune/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/mmkeys/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/status-icon/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/plugins/visualizer/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/state/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/state/iradio
/home/paul/.gconf/apps/rhythmbox/state/library
/home/paul/.gconf/apps/rhythmbox/state/podcast
/home/paul/.gconf/apps/rhythmbox/state/iradio/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/state/library/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/state/podcast/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/ui/%gconf.xml
/home/paul/.gconf/apps/rhythmbox/ui/library
/home/paul/.gconf/apps/rhythmbox/ui/library/%gconf.xml
/home/paul/.gnome2/accels/rhythmbox
/home/paul/.local/share/rhythmbox
/home/paul/.local/share/Trash/files/rhythmbox.desktop
/home/paul/.local/share/Trash/info/rhythmbox.desktop.trashinfo
/home/paul/.local/share/rhythmbox/magnatune
/home/paul/.local/share/rhythmbox/playlists.xml
/home/paul/.local/share/rhythmbox/rhythmdb.xml
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/__init__.py
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/__init__.pyc
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/braille_generator.py
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/braille_generator.pyc
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/formatting.py
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/formatting.pyc
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/script.py
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/script.pyc
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/speech_generator.py
/usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox/speech_generator.pyc
/usr/share/app-install/desktop/rhythmbox.desktop
/usr/share/app-install/icons/rhythmbox.png
/usr/share/icons/Humanity/actions/16/rhythmbox-set-star.svg
/usr/share/icons/Humanity/actions/24/rhythmbox-set-star.svg
/usr/share/icons/Humanity/actions/48/rhythmbox-set-star.svg
/usr/share/locale-langpack/en_AU/LC_MESSAGES/rhythmbox.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/rhythmbox.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/rhythmbox.mo
/usr/share/pyshared/orca/scripts/apps/rhythmbox
/usr/share/pyshared/orca/scripts/apps/rhythmbox/__init__.py
/usr/share/pyshared/orca/scripts/apps/rhythmbox/braille_generator.py
/usr/share/pyshared/orca/scripts/apps/rhythmbox/formatting.py
/usr/share/pyshared/orca/scripts/apps/rhythmbox/script.py
/usr/share/pyshared/orca/scripts/apps/rhythmbox/speech_generator.py
/var/cache/apt/archives/rhythmbox_0.12.5-0ubuntu5_i386.deb
/var/lib/dpkg/info/rhythmbox.list
/var/lib/dpkg/info/rhythmbox.postrm```

sudo rm /var/lib/dpkg/info/rythmbox*
sudo apt-get clean
sudo rm -rf /usr/suare/pyshared/orca/scripts/apps/rhythmbox
sudo rm /usr/share/locale-langpack/en_AU/LC_MESSAGES/rhythmbox.mo
sudo rm /usr/share/locale-langpack/en_CA/LC_MESSAGES/rhythmbox.mo
sudo rm/usr/share/locale-langpack/en_GB/LC_MESSAGES/rhythmbox.mo
sudo rm /usr/share/icons/Humanity/actions/16/rhythmbox-set-star.svg
sudo rm /usr/share/icons/Humanity/actions/24/rhythmbox-set-star.svg
sudo rm /usr/share/icons/Humanity/actions/48/rhythmbox-set-star.svg
sudo rm /usr/share/app-install/desktop/rhythmbox.desktop
sudo rm /usr/share/app-install/icons/rhythmbox.png
sudo rm -rf /usr/lib/pymodules/python2.6/orca/scripts/apps/rhythmbox
sudo rm -rf /home/paul/.local/share/rhythmbox
sudo rm -rf /home/paul/.gnome2/accels/rhythmbox
sudo rm -rf /home/paul/.gconf/apps/rhythmbox
sudo rm -rf /home/paul/.cache/rhythmbox

```
note to mods: you guys are gonna pay for my carpal tunnel syndrome treatment when it comes up ;) jks

---

### Post by Paul T. on 2009-12-10
Carlee,

thx to going to all that trouble writing the commands out for me, I was able to just copy & paste them, saved me from carpel tunnel syndrome....):P

All the remains of rhythmbox was deleted, but on re-installation same problem :-(

---

### Post by SteveNorman on 2009-12-10
You need to do the same thing for gstreamer. Also be very very very very very careful with the sudo rm -rf command. Stop and look before you hit enter to make sure the spaces are correct. I have deleted my home folder a few times before, and its not that hard to delete your root system, by accidentally having a space after a / you could sink the ship.

I bet your problems have to do with the gstreamer plugin. 

Also read through that link, one of the posts is from someone with your issue, and he lists how he solved it.

---

### Post by sandyd on 2009-12-10
run
```

locate *gstreamer*
```

---

### Post by Paul T. on 2009-12-10
Thx for the info, at moment I'm having to use Windows as problems with Ubuntu are escalating....
Nautilus is acting up now, clicking on some files and Nautilus shuts itself down taking desktop icons with it.
Tried to do a backup with 'Simple Backup' (anticipating a full re-install) but after a few minutes graphics go to pot & system freezes, even keyboard won't work
Pidgin won't load; tried KDE desktop, same probs plus keyboard didn't work.....

There must be something that the above faults have in common?

Been getting real p****d off with Ubuntu today, will sleep on it tonight and hopefully feel in better frame of mind tomorrow.

---

### Post by SteveNorman on 2009-12-10
They could be related.

---

### Post by Paul T. on 2009-12-14
*Update*

Since my last post I've done a complete re-installation of Ubuntu and sorted all probs :P

However, today I installed Kdenlive, the Linux equivalent of Windows Movie Maker, lo and behold can't play music or vids again!
I've completely uninstalled Kdenlive but still Movie player & Rhythmbox won't work, again :(

Any ideas how I can undo whatever changes Kdenlive has done to my system?

ps, Pidgin has stopped working too....

---

