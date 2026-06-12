---
title: "Difference between .bin and .deb installation file"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by mrajaram on 2008-12-18
I'm a linux noob. .bin installation files seems to be distribution agnostic. For example, see [http://get.adobe.com/air/](http://get.adobe.com/air/) Then, why not use .bin as common standard instead of having different package formats for debian(.deb), redhat(.rpm) etc. What is the different difference between .bin files and the above mentioned file formats?

---

### Post by lovelyvik293 on 2008-12-18
The bin files are the files which in be installed on every linux ditro,But the .deb files are only to be installed on Debian family of OS like ubuntu.

---

### Post by emshains on 2008-12-18
As far as I know, .bin files only provide a package of an app or a library. If you don't have the dependencies needed, the application may not work properly. But a .deb file comes with a list of dependencies it needs, so if you haven't got something it needs, it will tell apt to get it.

---

### Post by appi2012 on 2008-12-18
.bin is generally harder to install. .debs, in ubuntu, install by double clicking. If I am not mistaken, .debs allow the package to be managed like other packages installed through the repositories. So .debs appear in synaptic, and you can uninstall them easily. (i think)

---

### Post by mrajaram on 2008-12-18
@lovelyvik293 Thanks for your reply. But,that was part of my question. Then why not use .bin file as a standard across all linux distros instead of creating different package formats for every distributions? That will make things easy for developers right?

---

### Post by Locke_99GS on 2008-12-18
deb's provide dependency information, which apt can sort out on its own, as well as placement/location information. bin's do not, and will require you to manage dependency issues on your own.

---

### Post by lovelyvik293 on 2008-12-18
The .deb are packages which are easy to install.Most linux distros have there specific package formats like 'rpm' in fedora.

---

### Post by donkyhotay on 2008-12-18
A .bin is an actual program (like a .exe in windows) that usually only installs one package. Assuming the program is self-contained this is fine. Most programs though require multiple packages to work correctly and rather then copy the same information over and over again (imagine the inefficiency of every program having it's own 'display a mouse cursor on the screen' code) it just has one copy that multiple programs use. In order to make certain that some of the less common libraries are installed (like say a system that converts text to voice) the .deb file will try to install these dependencies as well. The problem that people often run into with .debs is when the dependencies are missing and need to be installed manually themselves.

---

### Post by lykwydchykyn on 2008-12-18
.bin is an extension used for a variety of binary files, but usually an executable binary file.  Kind of analogous to .exe on Windows.

.deb is a non-executable data package of software install data.  Kind of like an .msi file on Windows.  

There are several reasons to prefer .deb or .rpm files on Linux to some distro-agnostic .bin installer, for instance:
 - When you use a package manager, dependencies are automatically checked for and (depending on the PM) taken care of.
 - A package manager can check for conflicts between packages, which acts like a bit of a security check.  For instance, if you download "way-cool-game.deb" and the install tries to overwrite /bin/bash or delete /etc, for example, the package manager won't do it; it will throw out an error because those files belong to one (or more) other packages.  A .bin running as root will not care what it overwrites or deletes.
 - In order to be distro-agnostic, the software in .bin-style installs are typically statically-linked.  There is a lot of debate about the merits of statically-linked packages vs. dynamically-linked packages (which is what .deb files usually (but not exclusively) install).  Essentially, this means that if your program relies on another external library, (e.g., gtk) the statically-linked version will contain its own copy, whereas the dynamically-linked will use a shared copy installed on your system.

Package management is different from the way things are done on other systems, but once you get used to the difference you see that it provides a lot of benefits.

---

### Post by kanikilu on 2008-12-18
> **mrajaram said:**
> Thanks for your reply. But,that was part of my question. Then why not use .bin file as a standard across all linux distros instead of creating different package formats for every distributions? That will make things easy for developers right?
Because a ".bin" is just a binary...all you can do is run it or delete it. A package like a .deb can be used to resolve dependencies, upgrade, uninstall, find version and other information about the program, and all sorts of nifty things.

Why everyone doesn't use the same package format? That's the beauty of linux: choice. I'm sure it would make things easier on devs, and think that's why *many* distributions use either deb or rpm (and there are tools to, for instance, to convert an rpm to a deb), but at the end of the day, I guess not *everyone* wants a precompiled binary...

*EDIT* - See the post above, he definitely described it better - the exe and msi analogies are *apt* ;)

---

### Post by Michael.Godawski on 2008-12-18
Some theory:
_debian packages_
> Debian's packaging system (dpkg) is similar to other popular packaging systems like [RPM]("http://foldoc.org/?RPM").  There are over 2200 packages of precompiled software available in the main (free) section of the Debian 2.1 distribution alone -- this is what sets Debian apart from many other Linux distributions.  The high quality and huge number of official packages (most Debian systems' /usr/local/ remains empty -- almost everything most Linux users want is officially packaged) are what draw many people to use Debian. _binary files_
 > Any [file format]("http://foldoc.org/index.cgi?file+format") for [digital]("http://foldoc.org/index.cgi?digital") [data]("http://foldoc.org/index.cgi?data") that does not consist of a sequence of printable [characters]("http://foldoc.org/index.cgi?characters") ([text]("http://foldoc.org/index.cgi?text")). The term is often used for executable [machine code]("http://foldoc.org/index.cgi?machine+code").  All digital data, including characters, is actually binary data (unless it uses some (rare) system with more than two discrete levels) but the distinction between binary and text is well established.  On modern [operating systems]("http://foldoc.org/index.cgi?operating+systems") a text file is simply a binary file that happens to contain only printable characters, but some older systems distinguish the two file types, requiring programs to handle them differently. 
 A common class of binary files is programs in [machine language]("http://foldoc.org/index.cgi?machine+language") ("[executable]("http://foldoc.org/index.cgi?executable") files") ready to load into memory and execute.  Binary files may also be used to store data output by a program, and intended to be read by that or another program but not by humans.  Binary files are more efficient for this purpose because the data (e.g. numerical data) does not need to be converted between the binary form used by the [CPU]("http://foldoc.org/index.cgi?CPU") and a printable (ASCII) representation.  The disadvantage is that it is usually necessary to write special purpose programs to manipulate such files since most general purpose utilities operate on text files.  There is also a problem sharing binary numerical data between processors with different [endian]("http://foldoc.org/index.cgi?endian")ness. 
taken from:
[http://foldoc.org/](http://foldoc.org/)

might be little old but some things do not change :)

---

### Post by mrajaram on 2008-12-18
> **lykwydchykyn said:**
> .bin is an extension used for a variety of binary files, but usually an executable binary file.  Kind of analogous to .exe on Windows.

.deb is a non-executable data package of software install data.  Kind of like an .msi file on Windows.  

There are several reasons to prefer .deb or .rpm files on Linux to some distro-agnostic .bin installer, for instance:
 - When you use a package manager, dependencies are automatically checked for and (depending on the PM) taken care of.
 - A package manager can check for conflicts between packages, which acts like a bit of a security check.  For instance, if you download "way-cool-game.deb" and the install tries to overwrite /bin/bash or delete /etc, for example, the package manager won't do it; it will throw out an error because those files belong to one (or more) other packages.  A .bin running as root will not care what it overwrites or deletes.
 - In order to be distro-agnostic, the software in .bin-style installs are typically statically-linked.  There is a lot of debate about the merits of statically-linked packages vs. dynamically-linked packages (which is what .deb files usually (but not exclusively) install).  Essentially, this means that if your program relies on another external library, (e.g., gtk) the statically-linked version will contain its own copy, whereas the dynamically-linked will use a shared copy installed on your system.

Package management is different from the way things are done on other systems, but once you get used to the difference you see that it provides a lot of benefits.

Perfect! Thanks lykwydchykyn

---

### Post by HotShotDJ on 2008-12-18
> **mrajaram said:**
> That will make things easy for developers right?Typically, developers distribute source packages (*.tar.gz, *.tar.bz2).  After that, it is up to the various distributions (such as Ubuntu, Fedora, SuSE, etc.) and system integrators to create the binary packages for their users.  If every distribution switched to a single packaging standard tommorow (¡Milagro de los dioses!) it would have little effect on F/OSS developers.

---

### Post by emshains on 2008-12-19
> **mrajaram said:**
> Perfect! Thanks lykwydchykyn

LOL, you thanked everybody, but him.

---

