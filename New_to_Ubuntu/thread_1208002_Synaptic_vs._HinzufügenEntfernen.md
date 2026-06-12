---
title: "Synaptic vs. Hinzufügen/Entfernen"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by atmega on 2009-07-08
Hab mich gerade gefragt ob es unterschiede beim Entfernen von Applikationen gibt?

Werden geladene files von Synaptic tatsächlich vom System entfernt (=gelöscht) oder werden diese falls installiert nur "weggeräumt".

Wo genau ist der Unterschied zwischen Hinzufügen/Entfernen und dem Synaptic-Paketmanager?

mfG

---

### Post by overdrank on 2009-07-08
> **atmega said:**
> Hab mich gerade gefragt ob es unterschiede beim Entfernen von Applikationen gibt?

Werden geladene files von Synaptic tatsächlich vom System entfernt (=gelöscht) oder werden diese falls installiert nur "weggeräumt".

Wo genau ist der Unterschied zwischen Hinzufügen/Entfernen und dem Synaptic-Paketmanager?

mfG
Did I just wondered whether there are variations in the removal of applications, there?

Are files downloaded from Synaptic actually removed from the system (= deleted) or if these are installed only "away".

Where exactly is the difference between Add / Remove and Synaptic Package Manager? 


Hi and welcome, English please on the forums. :)

---

### Post by atmega on 2009-07-08
i asked myself if there is any difference between the add/remove tool (in the menu) and the synaptik packetmanager.

do they both delete packets from harddisk if I select remove or do they only "uninstall" them and store them packed or something else.

Another problem I have is using vi in the terminal.
After entering the edit mode by pressing "i" I can only write a few characters some like the cursors or "d" act like control-keys as if I weren't in edit mode.

with kind regards

---

### Post by rbc on 2009-07-08
From what I have noticed, when installing packages via Add/Remove, one only sees the application that he is installing. Synaptic will list the application, as well as any extra packages that the application needs. For removing packages, have a look at the man pages for apt-get, specifically -remove and -purge. I have noticed that even after removing an application, the installer remains in /var/apt/cache/archives

---

### Post by credobyte on 2009-07-08
Removing application ( installed from Add/Remove ) does not remove it's dependencies ( .debs from /var/cache/apt/archive/ ). Not 100% sure about Synaptic ( haven't used it for a while ), so .. enjoy :)

---

### Post by QIII on 2009-07-08
Config files can be left behind by both Synaptic and Add/Remove

sudo apt-get remove --purge somepackage

gets rid of the config files along with the package.

---

