---
title: "update problem"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by getgood123 on 2010-11-23
hi when ever i try to update i get this error message 

W:Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-i386_Packages), E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/debs.peadrop.com_dists_feisty_backports_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.




i have tried  apt-get update

---

### Post by sikander3786 on 2010-11-23
Please post the output of

```
cat /etc/apt/sources.list
```

---

### Post by getgood123 on 2010-11-23
deb [http://packages.enlightenment.org/ubuntu](http://packages.enlightenment.org/ubuntu) jaunty main extras
deb-src [http://packages.enlightenment.org/ubuntu](http://packages.enlightenment.org/ubuntu) jaunty main extras

---

### Post by sikander3786 on 2010-11-23
> **getgood123 said:**
> deb [http://packages.enlightenment.org/ubuntu](http://packages.enlightenment.org/ubuntu) jaunty main extras
deb-src [http://packages.enlightenment.org/ubuntu](http://packages.enlightenment.org/ubuntu) jaunty main extras
I wonder if this is the complete output for above mentioned command?

Which version of Ubuntu are you using?

---

### Post by getgood123 on 2010-11-23
Maverick Meerkat

---

### Post by getgood123 on 2010-11-23
> **sikander3786 said:**
> I wonder if this is the complete output for above mentioned command?

Which version of Ubuntu are you using?

deb [http://afterxleep.com/apt](http://afterxleep.com/apt) feisty main
deb [http://apt.mepis.org/6.0/](http://apt.mepis.org/6.0/) mepis main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
deb [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) feisty restricted main multiverse preview universe
deb-src [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) feisty restricted main multiverse preview universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego secondlife all internode google bcm43xx
deb-src [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) feisty-cafuego secondlife all internode google bcm43xx
deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main
deb [http://bluez.sourceforge.net/download/debian/](http://bluez.sourceforge.net/download/debian/) ./
deb [http://cl.archive.ubuntu.com/ubuntu](http://cl.archive.ubuntu.com/ubuntu) feisty-backports restricted main multiverse universe
deb-src [http://cl.archive.ubuntu.com/ubuntu](http://cl.archive.ubuntu.com/ubuntu) feisty-backports restricted main multiverse universe
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) feisty-updates restricted main
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) feisty-updates restricted main
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free
deb [http://debian.o-hand.com](http://debian.o-hand.com) feisty/
deb [http://debs.peadrop.com](http://debs.peadrop.com) feisty backports
deb-src [http://debs.peadrop.com](http://debs.peadrop.com) feisty backports
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) feisty all
deb-src [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) feisty all
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy suspend2
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy suspend2
deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17
deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17
deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) feisty main
deb [http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu](http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu) feisty musicbrainz
deb-src [http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu](http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu) feisty musicbrainz
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets all
deb-src [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets all
deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) feisty all
deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) feisty all
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty non-free free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty non-free free
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas all
deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) feisty-seveas all
deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) feisty-backports main
deb-src [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) feisty-backports main
deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./
deb-src [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./
deb [http://pkg-initng.alioth.debian.org/debian/](http://pkg-initng.alioth.debian.org/debian/) experimental main
deb [http://pkg-voip.buildserver.net/ubuntu](http://pkg-voip.buildserver.net/ubuntu) feisty main
deb-src [http://pkg-voip.buildserver.net/ubuntu](http://pkg-voip.buildserver.net/ubuntu) feisty main
deb [http://repository.debuntu.org/](http://repository.debuntu.org/) feisty multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) feisty multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe
deb [http://snapshots.ekiga.net/ubuntu/](http://snapshots.ekiga.net/ubuntu/) feisty main
deb-src [http://snapshots.ekiga.net/ubuntu/](http://snapshots.ekiga.net/ubuntu/) feisty main
deb [http://snapshots.seconix.com/ubuntu/](http://snapshots.seconix.com/ubuntu/) feisty main
deb-src [http://snapshots.seconix.com/ubuntu/](http://snapshots.seconix.com/ubuntu/) feisty main
deb [http://snapshots.voxgratia.org/ubuntu/](http://snapshots.voxgratia.org/ubuntu/) feisty main
deb-src [http://snapshots.voxgratia.org/ubuntu/](http://snapshots.voxgratia.org/ubuntu/) feisty main
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) feisty universe multiverse
deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty eyecandy multimedia misc
deb-src [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty eyecandy multimedia misc
deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-intern uniklu
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) feisty uniklu-intern uniklu
deb [http://ubuntusoftware.info/](http://ubuntusoftware.info/) feisty all
deb [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental all
deb-src [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental all
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.imbrandon.com/packages](http://www.imbrandon.com/packages) feisty beryl all
deb-src [http://www.imbrandon.com/packages](http://www.imbrandon.com/packages) feisty beryl all
deb [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/) feisty main
deb-src [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/) feisty main
deb-src [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/) ./
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/) ./
deb [http://www.linux2go.dk/ubuntu](http://www.linux2go.dk/ubuntu) feisty main
deb-src [http://www.linux2go.dk/ubuntu](http://www.linux2go.dk/ubuntu) feisty main
deb [http://www.mpe.mpg.de/~ach/kubuntu/feisty](http://www.mpe.mpg.de/~ach/kubuntu/feisty) ./
deb-src [http://www.mpe.mpg.de/~ach/kubuntu/feisty](http://www.mpe.mpg.de/~ach/kubuntu/feisty) ./
deb [http://www.tvfreeplayer.com/linux/falcon](http://www.tvfreeplayer.com/linux/falcon) feisty all mods vlc
deb-src [http://www.tvfreeplayer.com/linux/falcon](http://www.tvfreeplayer.com/linux/falcon) feisty all mods vlc
deb [http://www.uv.es/cuan/repos](http://www.uv.es/cuan/repos) feisty extras
deb-src [http://www.uv.es/cuan/repos](http://www.uv.es/cuan/repos) feisty extras
deb [http://packages.enlightenment.org/ubuntu](http://packages.enlightenment.org/ubuntu) jaunty main extras
deb-src [http://packages.enlightenment.org/ubuntu](http://packages.enlightenment.org/ubuntu) jaunty main extras
I'm very sorry

---

### Post by sikander3786 on 2010-11-23
> **getgood123 said:**
> Maverick Meerkat

Your sources.list seems to be completely messed up. Many entries from the previous releases. How did you add them here?

Please generate a new sources.list here selecting proper release, your territory and the standard repositories.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Then backup your existing sources.list by

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bad
```

Delete the original one,

```
sudo rm /etc/apt/sources.list
```

Create a new and put all your text in that.

```
gksudo gedit /etc/apt/sources.list
```

Save, close and try apt-get update again.

Good Luck!

---

### Post by getgood123 on 2010-11-23
thanks it seams to be working

---

### Post by sikander3786 on 2010-11-23
> **getgood123 said:**
> thanks it seams to be working
Glad to know that :-)

You can now mark this thread Solved using [COLOR="Red"]**Thread Tools**[/COLOR] near the top of this page. It would save our mates some time and they can use it to look into un-solved threads instead.

Happy Ubuntu-ing!

---

