---
title: "lucid gdm help"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by jeslinmx on 2010-08-30
bleh. ubuntu 10.04 has removed the login screen theming thing. does anyone have any ideas how to install a gdm theme thats in the form of a tar.gz?

---

### Post by kwacka on 2010-08-30
System --> Preference --> Appearance --> Theme  for gnome themes

[http://ubuntuforums.org/showthread.php?t=1358026&highlight=gdm+themes](http://ubuntuforums.org/showthread.php?t=1358026&highlight=gdm+themes)  is one of several threads for gdm themes.

---

### Post by jeslinmx on 2010-09-01
hmm. i was hoping for something of a facility that allows installation from tar.gz archives. the appearance>install way doesnt seem to support login screens.

---

### Post by wirate on 2010-09-01
logout of Ubuntu
press ctrl+f1
enter password
type
```
export DISPLAY=:0.0
sudo -u gdm gnome-control-center
```
press alt+f7 or alt+f8 in some cases

---

### Post by jeslinmx on 2010-09-01
erm, ctrl f1, alt f6 or f7 don't do anything. what was that intended to do?

---

### Post by tad1073 on 2010-09-01
Follow this tutorial if just want to use gtk themes

[http://ubuntuforums.org/showthread.php?t=1333683](http://ubuntuforums.org/showthread.php?t=1333683)

or you could try this

[https://launchpad.net/gdm2setup](https://launchpad.net/gdm2setup)

---

