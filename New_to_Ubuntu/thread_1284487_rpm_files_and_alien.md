---
title: "rpm files and alien"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by lowpine on 2009-10-06
hey guys,

I'm trying to install drivers and software for a lightscribe dvd burner.

I found a thread that alluded to using alien to install the rpm files.  I'm a bit stumped, I don't see alien in the availble packages in the applicaton-add/remove list, nor am I even sure that I need alien, as that wasn't clear to me.

any help is appreciated.

thanks

---

### Post by scorp123 on 2009-10-06
> **lowpine said:**
>  I found a thread that alluded to using alien to install the rpm files. And why not the *.deb packages? Those would work right away.

[http://download.lightscribe.com/ls/lightscribe-1.18.8.1-linux-2.6-intel.deb](http://download.lightscribe.com/ls/lightscribe-1.18.8.1-linux-2.6-intel.deb)

[http://download.lightscribe.com/ls/lightscribeApplications-1.18.6.1-linux-2.6-intel.deb](http://download.lightscribe.com/ls/lightscribeApplications-1.18.6.1-linux-2.6-intel.deb)

---

### Post by PacSci on 2009-10-06
Ubuntu's native package format is .deb - .rpm is used by many other distros, though. You do indeed need Alien to install these packages, as Ubuntu's packaging system cannot handle them standalone.

Since Alien is a command-line program, it's not in Add/Remove. You can follow the instructions at [https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto) to install Alien and run it on the .rpm in question.

---

### Post by scorp123 on 2009-10-06
> **PacSci said:**
> Ubuntu's native package format is .deb  Exactly. And there are *.deb files for those programs he wants. So there is no need to "alien" anything here.

---

### Post by lowpine on 2009-10-06
wow! thanks for the speedy replys..... ok, thanks for the links, I had the driver deb file, but the other thread linked to rpm file for the software, thus my question.

I'll give it a go! thanks!

---

