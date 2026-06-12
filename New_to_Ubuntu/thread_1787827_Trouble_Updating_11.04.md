---
title: "Trouble Updating 11.04"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by Tastiger on 2011-06-21
Since upgrading to 11.04 I have had issues with updating packages both through the package manager on the GUI as well as via terminal.

Firstly in the GUI the process will begin OK and then just sit there not doing anything - hard to describe without screen shots...

So the easiest way to describe what is happening is to post results from terminal:-
 
```
sudo apt-get update
```> Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty InRelease
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates InRelease
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty Release.gpg
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates Release.gpg
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/main i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/restricted i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/universe i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/multiverse i386 Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/main TranslationIndex
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/multiverse TranslationIndex
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/restricted TranslationIndex
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/universe TranslationIndex
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/main i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/universe TranslationIndex
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/main Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/multiverse Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/restricted Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/main Translation-en
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/universe Translation-en
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/multiverse Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/restricted Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Reading package lists... Done
```
sudo apt-get upgrade
```> Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  amarok amarok-common amarok-utils cups cups-bsd cups-client cups-common
  cups-ppdc foo2zjs gnome-user-guide icedtea-netx language-selector-common
  language-selector-kde language-selector-qt libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1
  xserver-xorg-input-synaptics
21 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/20.3 MB of archives.
After this operation, 111 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Reading changelogs... Done
    from Red Hat on confirming this (LP: #792309).
  * debian/local/filters/pdf-filters/pdftopdf/P2PResources.cxx: Fixed
    memory leak in pdftopdf filter which made the filter taking up several
    gigabytes when processing certain PDF files. Thanks to upstream
    author Koji Otani for the quick fix (LP: #790378).
  * debian/local/pstopdf.convs, debian/local/pstopdf.types: Do not apply
    the PDF printing workflow to PostScript input coming from the Adobe
    Reader. If this PostScript comes from an encrypted (DRM) PDF, it cannot
    be converted to PDF again by Ghostscript (LP: #782309).

 -- Till Kamppeter <till.kamppeter@gmail.com>  Mon,  5 Jun 2011 13:51:59 +0200

Get:1 Changelog for foo2zjs ([http://changelogs.ubuntu.com/changelogs/pool/main/f/foo2zjs/foo2zjs_20110210dfsg-1ubuntu2.1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/f/foo2zjs/foo2zjs_20110210dfsg-1ubuntu2.1/changelog)) [22.8 kB]
foo2zjs (20110210dfsg-1ubuntu2.1) natty-proposed; urgency=low

  * debian/patches/95-udev-firmware-script-no-hplip-rules-removal.patch:
    Removed the lines in the UDEV script for the automatic firmware upload into
    the printer which remove the UDEV rules files for HPLIP's automatic
    firmware upload. NO WARS BETWEEN FREE SOFTWARE PROJECTS! (LP: #783389).

 -- Till Kamppeter <till.kamppeter@gmail.com>  Wed,  8 Jun 2011 13:30:00 +0200

:

***.... and there the process halts!***

any suggestions appreciated

---

### Post by terrykiwi83 on 2011-06-21
I can honestly say in the many moons using Ubuntu I have never anywhere seen

```

Reading changelogs... Done
from Red Hat on confirming this (LP: #792309).

```

Wonder why it mentions Red Hat? Maybe someone here will know a bit more.

---

