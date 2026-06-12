---
title: "is there a way to add all dependences and libraries ?"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by MBG1987 on 2009-08-19
ubunt 9.04 is already installed on my pc, every time i downloaded a package it says that u have toi install other pachages (dependences) in order to run this program ,so it's very time consuming ! my question is :what i have to do to download all requered dependences an libraries to my OS ? thank you

---

### Post by credobyte on 2009-08-19
That would be insane. Each and every application depends on different libraries, including non-Gnome ones ( eg. KDE ).

---

### Post by Cheesemill on 2009-08-19
If you use Add/Remove programs then all dependancies will be taken care of automatically.

---

### Post by dawynn on 2009-08-19
You cannot install all available libraries, nor would you want to.  Some libraries are incompatable with other libraries -- designed this way.  In cases where those libraries are needed, one needs to be chosen, but the choice ultimately belongs to the end user.

Yes, there often are other dependencies for each package, but there are worse ways of handling things.  I read recently that Mac applications include many of the libraries with *every* package that needs the libraries, then those libraries are stored locally to the software that needs them.  This has the potential to force the system to carry multiple duplicate libraries, and in some cases, differing versions of the same libraries.

In the Windows world (at least the ones I'm familiar with -- up through XP or so), there are dll's.  While different programs can share a dll, Windows seems to be uncaring as to whether it keeps track of who all is using a shared dll.  Try removing software once, and you'll likely see messages along the lines of shared library xyz.dll no longer *appears* to be used by any programs.  Want to delete -- may cause instability?

In Debian-based systems, library packages have the potential to be shared.  By sharing a library, if your system already has the library installed, then new packages do not need to download the new library also.  And dpkg / apt do not allow the removal of a library under normal circumstances without first removing all packages that depend on the library (yes, I realize that dpkg allows the "force" commands, but that would be abnormal circumstances).

Also, by splitting packages up into various libraries, etc., people with slow connections can break upgrades down into smaller chunks, and even perform installations over multiple sessions.

---

### Post by mcduck on 2009-08-19
> **MBG1987 said:**
> ubunt 9.04 is already installed on my pc, every time i downloaded a package it says that u have toi install other pachages (dependences) in order to run this program ,so it's very time consuming ! my question is :what i have to do to download all requered dependences an libraries to my OS ? thank you

Tine consuming? Are you trying to download and install the dependencies by hand? In that case you'd better start using the package management tools.. :D Read this: [http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

(and no, downloading everything from repositories isn't possible, and wouldn't really make any sense. You'd end with thousands of programs you don't need for anything)

---

