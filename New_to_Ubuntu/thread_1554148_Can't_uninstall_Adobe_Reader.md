---
title: "Can't uninstall Adobe Reader"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by puntigamer on 2010-08-16
Hi all,

I've a problem with my adobe reader (german version)
It writes, that anything is missing, and the uninstallation can not be countinoued.
The console writes:

daniel@daniel-laptop:~$ sudo dpkg -r adobereader-deu
(Lese Datenbank ... 338633 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne adobereader-deu ...
/var/lib/dpkg/info/adobereader-deu.prerm: 193: nspluginwrapper: not found
dpkg: Fehler beim Bearbeiten von adobereader-deu (--remove):
 Unterprozess installiertes pre-removal-Skript gab den Fehlerwert 127 zurück
Fehler traten auf beim Bearbeiten von:
 adobereader-deu

(error by the removal of the adobereader-deu packpage - /var/lib/dpkg/info/adobereader-deu.prerm: 193: nspluginwrapper: not  found. Error N° 127)

Please help!

---

### Post by martin_legion on 2010-08-23
> **puntigamer said:**
> Hi all,

I've a problem with my adobe reader (german version)
It writes, that anything is missing, and the uninstallation can not be countinoued.
The console writes:

daniel@daniel-laptop:~$ sudo dpkg -r adobereader-deu
(Lese Datenbank ... 338633 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne adobereader-deu ...
/var/lib/dpkg/info/adobereader-deu.prerm: 193: nspluginwrapper: not found
dpkg: Fehler beim Bearbeiten von adobereader-deu (--remove):
 Unterprozess installiertes pre-removal-Skript gab den Fehlerwert 127 zurück
Fehler traten auf beim Bearbeiten von:
 adobereader-deu

(error by the removal of the adobereader-deu packpage - /var/lib/dpkg/info/adobereader-deu.prerm: 193: nspluginwrapper: not  found. Error N° 127)

Please help!

try:

```
sudo aptitude purge acroread adobereader-deu
```

---

