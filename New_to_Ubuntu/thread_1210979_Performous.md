---
title: "Performous"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Samuel Dias on 2009-07-12
hi, i'm from portugal. i have amilo m7440g and jaunty...

i receive from console this message when do performous:

Exception from recording callback: accessing 'front()' on empty container
Exception from recording callback: accessing 'front()' on empty container
Exception from recording callback: accessing 'front()' on empty container
Exception from recording callback: accessing 'front()' on empty container
Exception from recording callback: accessing 'front()' on empty container
Exception from recording callback: accessing 'front()' on empty container
Exception from recording callback: accessing 'front()' on empty container
Exception from recording callback: accessing 'front()' on empty container
Exception from recording callback: accessing 'front()' on empty container
Exception from recording callback: accessing 'front()' on empty container
Exception from recording callback: accessing 'front()' on empty container
Exception from recording callback: accessing 'front()' on empty container
Exception from recording callback: accessing 'front()' on empty container
Exception from recording callback: accessing 'front()' on empty container
Exception from recording callback: accessing 'front()' on empty container
Morto

Then i have to kill

also:
~$ performous --cdev arg
get fences failed: -1
param: 6, val: 0
>>> Using playback device alsa
>>> Using recording device arg
15 songs loaded
FATAL ERROR: Recording device arg not found

will someone help me ?

---

### Post by Gone fishing on 2009-07-12
Might be a bug have a look at:

[https://bugs.launchpad.net/ubuntu/+source/performous/+bug/367708/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/performous/+bug/367708/+viewstatus)

[https://answers.launchpad.net/ubuntu/+source/performous/+question/68767](https://answers.launchpad.net/ubuntu/+source/performous/+question/68767)

---

### Post by Samuel Dias on 2009-07-12
> **Gone fishing said:**
> Might be a bug have a look at:

[https://bugs.launchpad.net/ubuntu/+source/performous/+bug/367708/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/performous/+bug/367708/+viewstatus)

[https://answers.launchpad.net/ubuntu/+source/performous/+question/68767](https://answers.launchpad.net/ubuntu/+source/performous/+question/68767)


see my report (its last entry)


[http://sourceforge.net/forum/forum.php?thread_id=3243848&forum_id=871563](http://sourceforge.net/forum/forum.php?thread_id=3243848&forum_id=871563)


Now have this:

~$ performous
ALSA capture devices:
  alsa:hw:ICH6,0   Intel ICH6 (Intel ICH6)
  alsa:hw:ICH6,1   Intel ICH6 (Intel ICH6 - MIC ADC)
  alsa:hw:ICH6,2   Intel ICH6 (Intel ICH6 - MIC2 ADC)
  alsa:hw:ICH6,3   Intel ICH6 (Intel ICH6 - ADC2)
ALSA playback devices:
  alsa:hw:ICH6,0   Intel ICH6 (Intel ICH6)
  alsa:hw:ICH6,4   Intel ICH6 (Intel ICH6 - IEC958)

Testing config file "/usr/share/performous/config/performous.xml": NOT FOUND
Testing config file "/usr/share/games/performous/config/performous.xml": FOUND
Opening default configuration file "/usr/share/games/performous/config/performous.xml"
Found 20 default configuration items
Opening global configuration file "/etc/xdg/performous/performous.xml"
  Cannot open global configuration file
Opening user configuration file "/home/samuel/.config/performous.xml"
  Cannot open user configuration file (using defaults)

Generic options:
  -h [ --help ]         you are viewing it
  -v [ --version ]      display version number

Configuration options:
  -t [ --theme ] arg    set theme (name or absolute path)
  -f [ --fs ]           enable full screen mode
  --fps                 benchmark rendering speed
                          also disable 100 FPS limit
  --songlist arg        save a list of songs in the specified folder
  -W [ --width ] arg    set horizontal resolution
  -H [ --height ] arg   set vertical resolution
  --fs-width arg        set fullscreen horizontal resolution
  --fs-height arg       set fullscreen vertical resolution
  --michelp             detailed help for --mics and a list of available audio 
                        devices
  --mics arg            specify microphones to use
  --pdevhelp            detailed help for --pdev and a list of available audio 
                        devices
  --pdev arg            specify a playback device
  -c [ --clean ]        disable internal default song folders
  -s [ --songdir ] arg  additional song folders to scan
                          may be specified without -s or -songdir too

ERROR: unknown option cdev

---

