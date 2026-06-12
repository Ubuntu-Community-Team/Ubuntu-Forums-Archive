---
title: "linux-image-2.6.28-13-generic"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by MasterOfVDL on 2009-07-09
Upon automatic updates today I got the following error message:
```

E: /var/cache/apt/archives/linux-image-2.6.28-13-generic_2.6.28-13.45_i386.deb: nicht ganz gelesen in buffer_copy (Backend dpkg-deb während »./lib/modules/2.6.28-13-generic/kernel/drivers/net/tulip/xircom_cb.ko«)

```I'm using Ubuntu 9.04 (Jaunty) on a Samsung R50 Notebook where the CD drive is broken (I've installed Ubuntu via USB-Key).

apt-get tells me to run apt-get -f install. When I do this I get the following output:
```

Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Abhängigkeiten werden korrigiert... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  linux-image-2.6.28-13-generic
Vorgeschlagene Pakete:
  fdutils linux-doc-2.6.28 linux-source-2.6.28
Die folgenden NEUEN Pakete werden installiert:
  linux-image-2.6.28-13-generic
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
4 nicht vollständig installiert oder entfernt.
Es müssen noch 0B von 24,6MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 95,7MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? 
(Lese Datenbank ... 244226 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke linux-image-2.6.28-13-generic (aus .../linux-image-2.6.28-13-generic_2.6.28-13.45_i386.deb) ...
Done.
dpkg-deb: Unterprozess paste mit Signal (Broken pipe) getötet
dpkg: Fehler beim Bearbeiten von /var/cache/apt/archives/linux-image-2.6.28-13-generic_2.6.28-13.45_i386.deb (--unpack):
 nicht ganz gelesen in buffer_copy (Backend dpkg-deb während »./lib/modules/2.6.28-13-generic/kernel/drivers/net/tulip/xircom_cb.ko«)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Fehler traten auf beim Bearbeiten von:
 /var/cache/apt/archives/linux-image-2.6.28-13-generic_2.6.28-13.45_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I now fear my computer wan't startup again since linux-image seems to be needed at startup (grub data is being updated on installation).

I hope someone knows how the problem can be solved.

---

### Post by Elfy on 2009-07-09
Can you open aterminal and do

```
export LANG=
```

That should make it carry on in English - so we can see what it is saying.

Now run

```
sudo apt-get install linux-image-2.6.28-13-generic
```

Post the errors here please.

---

