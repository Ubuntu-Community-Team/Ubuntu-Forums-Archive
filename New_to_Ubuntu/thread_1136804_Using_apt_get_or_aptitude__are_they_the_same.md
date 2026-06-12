---
title: "Using apt get or aptitude : are they the same?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by yeehi on 2009-04-25
A while back I remember something about aptitude being better than apt as it remembered changes made or something like that.

Is it true? apt looks just like an abbreviation of aptitude to me...

---

### Post by gettinoriginal on 2009-04-25
there is some interesting reading on the subject here at the link below.

[http://ubuntuforums.org/showthread.php?t=997663](http://ubuntuforums.org/showthread.php?t=997663)

---

### Post by Therion on 2009-04-25
This should help clarify the differences between all the APT tools and front-ends:

[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)

---

### Post by ibuclaw on 2009-04-25
This used to be true, but apt-get now works alot better at resolving dependencies if things ever get broken. Also, there is a fundamental difference between them: aptitudes **tries** to be smarter than you. Whereas apt-get just **assumes** that you know what you are doing.

Imagine this complex scenario: If you want to install package **A**, but this breaks the current versions of **B** and **C**, and **D** and **E** depend on **B** and **C** to stay at their current version. Both applications will treat this differently.

apt-get will search for a the existence of, and will choose to upgrade the versions of **all** packages until all dependencies are resolved between them.

aptitude will favour the currently installed versions, **D** and **E**, so all packages will be held back, unless manually forced for upgrade.

The same is for uninstalling too. If you try to uninstall package **X**, but that breaks packages **F** through to **W** which all depend on **X**. So will see a similar situation.

apt-get will remove **all** broken dependencies. Since you don't want/use package **X**, you sure don't want package **F** through to **W** either.

aptitude will again favour the currently installed packages, and will **keep** package **X** installed unless you manually select packages **F** through to **W** to be uninstalled also.

Depending on which angle you see it from, it can either be a lifesaver or tedious.
Yesterday I spent 30 minutes in aptitude trying to remove 400MB of packages (mostly texlive) as they were installed as a build dependency for another application, which I wasn't planning on recompiling afterwards. . . This required searching through the database seeking and purging everything that was broken by the removal.
I was rather annoyed, if you were to ask me at the time.

Regards
Iain

---

### Post by yeehi on 2009-04-27
Oh thank you, everybody!

tinivole, that was very clear! :)

---

