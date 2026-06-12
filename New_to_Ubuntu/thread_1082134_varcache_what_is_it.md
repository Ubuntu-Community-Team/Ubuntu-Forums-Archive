---
title: "/var/cache what is it?"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by capnthommo on 2009-02-27
hi everybody
just a quickie here.  can anybody confirm that /var/cache is an archive of all the additional applications and updates and so on that have been added since the original installation?
and that this archive will be complete as long as i have not run the app that deletes the archives contents (is it sudo auto clean or something? can't remember).
i want this so i can just keep backups of this archive and if i need to i can reinstall from live cd and presto - i have all my changes! cos i will never remember them otherwise.
thanks 
nigel

---

### Post by wolfen69 on 2009-02-27
it is /var/cache/apt/archive where the .deb files are kept. you will still have to reinstall them, but they will not have to be downloaded.

sudo apt-get clean would remove them.

---

### Post by capnthommo on 2009-02-27
thanks wolfen.  
that's what i thought, i knew i'd seen it somewhere but just couldn't find the reference i sought.  
so i can be happier now knowing that if the worst happens it will mean i don't have to work my way through everything to figure out all the little additions and updates i have made. its easier to have them in a backed up archive than to have to start at square one again.
fortunately i haven't run [sudo apt-get clean] so pretty much everything should be there.
one day i will figure out how to take a complete image/mirror of my system and just re-install it if i have to.  but till then a backup of changes will do fine.
thanks v much
nigel
:guitar:

---

### Post by obaid on 2009-02-27
capnthommo: yes it is always a good idea to copy contents of /var/cache/apt/archive somewhere else, and make backup of it.

the time you reinstall your system, copy back the archive to /var/cache/apt/archive.
since it will have all applications you previously installed and all the updates.

once u have your backup files in place, it will save you alot of time and bandwidth.
----

i will give you another idea, when installing ubuntu, do manual partitioning, and keep your /home on saperate partition, so anytime you reinstall your system partition in / you will have your settings, mails, themes ..etc all preserved.

i just did reinstall before an hour. it took less than 1 hour to make everything as it was. + with updates.

thanks ubuntu team.

---

### Post by geirha on 2009-02-27
APTonCD burns the packages in /var/cache/apt/archives to CD or DVD for you. [https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)

---

