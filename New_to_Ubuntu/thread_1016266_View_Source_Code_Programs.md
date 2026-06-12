---
title: "View Source Code Programs"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Pergi on 2008-12-19
Hello all! I want to see the source code of the programs that Ubuntu has. Specifically, i want to see the code of the game Gnometris that is by default installed at Ubuntu 8.04

Maybe someone can tell me which is the directory on file system that has all the source codes of those programs? I searched at google and in other forums with keywords the title of this thread but i didn't find an answer.
Thank you in advance.

---

### Post by andrew.46 on 2008-12-19
Hi,

The game gnomemetris is part of the gnome-games package. Details can be seen:

[http://packages.ubuntu.com/intrepid/gnome-games](http://packages.ubuntu.com/intrepid/gnome-games)

and to the right you will see a link to the original source code:

[http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.24.1.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.24.1.orig.tar.gz)

Just open the archive and view the source with your favourite editor, better with one that does a little syntax highlighting. My own preferred editor for this purpose is Bluefish.

Hope this helps?

 Andrew

---

### Post by Michael.Godawski on 2008-12-19
hi,


these are all files installed with the meta-package gnome-games:

```
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/gnome-games
/usr/share/doc/gnome-games/NEWS.gz
/usr/share/doc/gnome-games/TODO
/usr/share/doc/gnome-games/AUTHORS
/usr/share/doc/gnome-games/copyright
/usr/share/doc/gnome-games/README.gz
/usr/share/doc/gnome-games/changelog.Debian.gz
/usr/share/man
/usr/share/man/man6
/usr/share/man/man6/glchess.6.gz
/usr/share/man/man6/glines.6.gz
/usr/share/man/man6/gnibbles.6.gz
/usr/share/man/man6/gnobots2.6.gz
**/usr/share/man/man6/gnometris.6.gz**
/usr/share/man/man6/gnomine.6.gz
/usr/share/man/man6/gnotravex.6.gz
/usr/share/man/man6/gnotski.6.gz
/usr/share/man/man6/gtali.6.gz
/usr/share/man/man6/iagno.6.gz
/usr/share/man/man6/mahjongg.6.gz
/usr/share/man/man6/same-gnome.6.gz
/usr/share/man/man6/sol.6.gz
/usr/share/man/man6/blackjack.6.gz
/usr/share/man/man6/gnect.6.gz
/usr/share/man/man6/gnome-sudoku.6.gz
/usr/share/menu
/usr/share/menu/gnome-games
/usr/share/applications
/usr/share/applications/sol.desktop
/usr/share/applications/freecell.desktop
/usr/share/applications/blackjack.desktop
**/usr/share/applications/gnometris.desktop**
/usr/share/applications/gnect.desktop
/usr/share/applications/gnomine.desktop
/usr/share/applications/same-gnome.desktop
/usr/share/applications/mahjongg.desktop
/usr/share/applications/gtali.desktop
/usr/share/applications/gnotravex.desktop
/usr/share/applications/gnotski.desktop
/usr/share/applications/glines.desktop
/usr/share/applications/iagno.desktop
/usr/share/applications/glchess.desktop
/usr/share/applications/gnobots2.desktop
/usr/share/applications/gnibbles.desktop
/usr/share/applications/gnome-sudoku.desktop
/usr/games
/usr/games/blackjack
/usr/games/glchess
/usr/games/glines
/usr/games/gnect
/usr/games/gnibbles
/usr/games/gnobots2
/usr/games/gnome-gnuchess
/usr/games/gnome-sudoku
**/usr/games/gnometris**
/usr/games/gnomine
/usr/games/gnotravex
/usr/games/gnotski
/usr/games/gtali
/usr/games/iagno
/usr/games/mahjongg
/usr/games/same-gnome
/usr/games/sol
/usr/lib
/usr/lib/gnome-games
/usr/lib/gnome-games/gnome-games-render-cards


```perhaps these will suit your needs; besides I have found these paths doing this:
I went to Synaptic, there searched for gnome-games, right-clicked onto the package, selected properties, then went to Installed Files.

I am not a programmer myself so cannot tell you which file has the source code you wish to see.

---

### Post by snova on 2008-12-19
Source code is not installed. You have to go get it.

As suggested earlier (and I learned something myself), go to "packages.ubuntu.com/intrepid/<package name>" and download the link on the right that ends in "orig.tar.gz". It's a simple archive.

> I am not a programmer myself so cannot tell you which file has the source code you wish to see.

Those files are, respectively, a man page, desktop file, and executable. Not much use in this situation. ;)

---

### Post by andrew.46 on 2008-12-19
Hi,

And of course there is a nice search page:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

which allows easy searching of *all* packages in *all* variants of Ubuntu. There are other methods to download the source but I think this is the easiest for just 1 or 2 packages. The 'apt-get source <package-name>' method can produce some confusion and a bunch of files although it will of course also get the required source code.

Andrew

---

### Post by niteshifter on 2008-12-19
> **andrew.46 said:**
> Hi,

And of course there is a nice search page:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

which allows easy searching of *all* packages in *all* variants of Ubuntu. There are other methods to download the source but I think this is the easiest for just 1 or 2 packages. The 'apt-get source <package-name>' method can produce some confusion and a bunch of files although it will of course also get the required source code.

Andrew

Hopefully this will clear up some of that confusion. From the man page on apt-get:
>  source
           source causes apt-get to fetch source packages. APT will examine
           the available packages to decide which source package to fetch. It
           will then find and download into the current directory the newest
           available version of that source package. Source packages are
           tracked separately from binary packages via deb-src type lines in
           the sources.list(5) file. This probably will mean that you will not
           get the same source as the package you have installed or as you
           could install. If the --compile options is specified then the
           package will be compiled to a binary .deb using dpkg-buildpackage,
           if --download-only is specified then the source package will not be
           unpacked.

[B]           A specific source version can be retrieved by postfixing the source
           name with an equals and then the version to fetch, similar to the
           mechanism used for the package files.[/B] This enables exact matching
           of the source package name and version, implicitly enabling the
           APT::Get::Only-Source option.



You can see the version info easily via synaptic.

---

### Post by Pergi on 2008-12-20
Thank you all very much for your replies :)

---

### Post by hyper_ch on 2008-12-20
and you have to make sure that you added the source repos also...

---

