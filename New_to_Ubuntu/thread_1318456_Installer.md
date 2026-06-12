---
title: "Installer"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by spribo on 2009-11-07
I have an application in Lazarus, and I would like to make an installer for it, for Ubuntu. For Windows, I use NSIS, is there something equivalent for Ubuntu?

---

### Post by spribo on 2009-11-07
Please, provide a hint!

---

### Post by blazemore on 2009-11-07
The best thing would be to package it as a .deb file
This would mean anyone using Ubuntu or another Debian-based system could install it straight away, and you could provide updates.

There's an advanced guide here [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

But I think there are some tools to help automate the process.

---

### Post by spribo on 2009-11-08
Like?

---

### Post by 3rdalbum on 2009-11-08
You don't need a program to help you create packages - it's easy to do.

Take a look at this tutorial - it's been written back-to-front in some ways, but in the end it comes down to you putting a file into a folder (just modify an existing one), putting your files-to-be-installed into the folders you want it to be in when it's installed, and running one command.

[http://www.quietsche-entchen.de/cgi-bin/wiki.cgi/-wiki/CreatingDebianPackages](http://www.quietsche-entchen.de/cgi-bin/wiki.cgi/-wiki/CreatingDebianPackages)

---

