---
title: "upgrading OpenOffice from 2.4 to OOo 3"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by rockerphil on 2009-10-03
ok, the title pretty well explains it, but here's some quick info about my system first. i'm running an old Dell Dimensin L500cx with 512 MB of PC100 SDRAM, and a 500 MHz Intel Celeron processor. the OS is a custom DE built from a CLI install using Fluxbox as the WM, rox-filer as the file manager, feh and idesk for icon rendering and an assortment of other lightweight apps to round off the OS. now, down to the matter at hand. i'm trying to upgrade OOo from 2.4 to OOo 3. i began by completely removing the version of OOo i already had and then downloaded the archive for my system from OpenOffice.org, extracted the files and installed all the debs using dpkg but nothing is showing up in the Fluxbox menus, i'm not finding anything in the /usr/bin directory concering OpenOffice and when i try to launch oowriter from the terminal it says it's not installed and to use apt-get to install it. any suggestions guys? any help is appreciated and thanks in advance,

Phil

---

### Post by louieb on 2009-10-03
Maybe its in the /opt directory. Did you look there? 

also try
```
sudo updatedb
locate ooffice
```

---

### Post by anonymous_user on 2009-10-03
Fluxbox's menu does not automatically show new programs, you have to edit it and add the programs you want.

---

### Post by rockerphil on 2009-10-03
> **anonymous_user said:**
> Fluxbox's menu does not automatically show new programs, you have to edit it and add the programs you want.

it use to be that way, but the newer versions of fluxbox has aut-updating menus, but none the less i've solved the problem. it installed, just as a different command, running

```
openoffice.org3
```

from a terminal launches a nifty little screen that asks me which OOo program i want to launch, i.e. Base, Writer, Math, Calc, Impress and the like. i've thus added the entry to my ~/.fluxbox/menu file.  but oh well, thanks for the assistance guys, marking this thread as solved

Phil

---

### Post by ceciliaFX on 2009-10-23
has anyone tried [this]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml") process. sounds reasonable

---

