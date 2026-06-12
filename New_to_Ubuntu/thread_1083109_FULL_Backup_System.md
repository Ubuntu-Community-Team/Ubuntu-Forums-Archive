---
title: "FULL Backup System"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by reg4c on 2009-02-28
Hey, 

does anyone know a full backup programme that contains backing up of:

- Installed packages, at least a list of the installed ones
- User settings for all the installed programmes
- User data

Cheers

---

### Post by N4zgu1 on 2009-02-28
you can try with APToncd you can make an iso with all the programs that you want but I dont think that you can save the settings too

---

### Post by _sAm_ on 2009-02-28
> - Installed packages, at least a list of the installed ones
In Synaptic go to File > Save Markings

> - User settings for all the installed programmes
Just copy your home folder(included the hidden ones). 

> - User data
There is lots of programs that can make backup for you, both gui and cli versions. Here is a list of some: [http://linuxappfinder.com/backupandrecovery](http://linuxappfinder.com/backupandrecovery)

"Simple Backup" is easy to use(I use rsync and its excellent).

---

### Post by reg4c on 2009-03-01
> **_sAm_ said:**
> In Synaptic go to File > Save Markings

This was exactly what I was looking for.
Thanks so much.

Cheers

---

### Post by HavocXphere on 2009-03-01
The fastest way to make a everything-including-kitchen-sink backup is hard-drive cloning. Something like Clonezilla.

---

### Post by handy on 2009-03-01
There is a lot of good info' on this site, including that for backing up Ubuntu:

*_[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)_*

---

### Post by philinux on 2009-03-01
There is also this option.

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by MrWES on 2009-03-01
to get a list of install packages, which you can then use to restore with:

[http://ubuntuforums.org/showthread.php?t=261366]("http://ubuntuforums.org/showthread.php?t=261366")

Bill

---

### Post by j_zhill on 2009-03-02
I just tried the "save markings" feature of synaptic then took a look at the output. It seems to contain a simple list of all installed packages, but not the sources they come from. Should I also make a simultaneous backup of sources.list? Is there a better way of ensuring that the package list corresponds to the sources list if I were to try and restore my system?

---

### Post by asmoore82 on 2009-03-02
[http://clonezilla.org/](http://clonezilla.org/) is quite excellent for Linux or Windows or Dual Boot setups.

it can capture and restore sparse images to and from an external hard drive
it can capture and restore sparse images to and from a network file server
it can clone the whole OS layout of one PC to another over "ad-hoc" networking

---

