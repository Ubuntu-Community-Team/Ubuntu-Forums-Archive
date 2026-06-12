---
title: "Removing a package"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by grantmcduling on 2011-04-29
Hi, I have loaded/installed a package to my home folder. I now want to remove it but can't. I have tried the Synaptec as well as sudo apt-get remove but it can't find it. So I have just deleted the folders from my home folder and suspect there are now dependencies lurking in the system somewhere. How can I be sure to clean everything out?

Grant

---

### Post by mcduck on 2011-04-29
That depends on what kind of package you installed, and how you did it.

The package management will only handle things insalled using the package amnager, so that woud include anything from the repositories and anything installe d manually using .deb packages. If you use any other method to install something, you pretty much ave to sort out things yourself.

(As a tip, programs installed from source code will often include their own uninstall script. You can also install them using checkinstall, that will convert the program into a .deb package allowing you to manage it through the normal package management tools. And programs that you didn't need to compile but only extracted somewhere can just be deleted to uninstall.)

---

