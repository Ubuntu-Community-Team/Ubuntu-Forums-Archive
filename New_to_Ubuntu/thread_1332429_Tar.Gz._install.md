---
title: "Tar.Gz. install"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by ibbill on 2009-11-20
imagination-2.1.tar.gz Have extracted the following to the desk now have a folder on the desk top see pic
 Have tried to follow all the help fourms on installing this with no luck.

What do I have to put in the terminal now.

Is there no way of changing these aggravating Tar files to deb. which installs it self without  all the terminal codes.

Thanks for your help 

Bill

---

### Post by QIII on 2009-11-20
The issue is that the tarred file could be any sort of file.  In many ways, it is analogous to a .zip file in Windows and the files included have to be extracted. 

If the underlying file is a .deb, then things are simple.  If it is an .rpm, then it can be converted to a .deb (in many cases.  That is not universally the case.)

If it is source code that has to be compiled, there is probably no way to just magically turn it into a .deb file.

.deb files are preconfigured installation files for Debian-based OSs, like Ubuntu.

.rpm files are preconfigured installation files for Red Hat-like systems.  These can often be converted to .deb files.

Source code that has to be compiled can generally not be installed in any other manner than the author describes in his/her installation instructions.

If you are lucky, you MAY be able to install it following the EXAMPLE here. This is not for Imagination, but it demonstrates the idea:

[http://www.linuxscrew.com/2008/06/11/create-deb-or-rpm-from-targz-with-checkinstall/](http://www.linuxscrew.com/2008/06/11/create-deb-or-rpm-from-targz-with-checkinstall/)

All that said, Imagination 1.5 appears to be in the Karmic repos.  Not sure what version of Ubuntu you are using, but it may be in the repos for previous versions as well.

[]("http://www.linuxscrew.com/2008/06/11/create-deb-or-rpm-from-targz-with-checkinstall/")

---

### Post by Slimbo on 2009-11-20
```
./configure
make
sudo make install

```Before you execute any of these commands, check README file. These commands are not universal and for each application they might be different.

---

### Post by QIII on 2009-11-20
> **Slimbo said:**
> Before you execute any of these commands, check README file. These commands are not universal and for each application they might be different.

Spot on.

---

### Post by mlentink on 2009-11-20
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Kevbert on 2009-11-20
You can get an older version from the Karmic Repos (via Synaptic) or if you want to risk it 2.1 is [[COLOR="Red"]here[/COLOR]]("http://packages.ubuntu.com/lucid/imagination"). You may have problems with dependencies (support files). You could try what Slimbo suggests after extracting all the files from the archive. There may be a readme file or an install document file within the tar.gz archive telling you how to install.

---

### Post by ibbill on 2009-11-20
Thanks for your help. It is in the repo but an old version and will not update for some reason.

I have decided that if the file or program I want is not in Deb then will just ignore them from now on. As I have mentioned before the seniors computer room are running ubuntu 9.10 on 4 computers. Trying to explain how to install a tar file to other seniors is way beyond me let alone installing it my self.(no idea how)

curious why the programs are tar files and not set  up as deb boggles my mind.(Keeping things simple would help)

Again thanks for your help

Bill

---

### Post by ibbill on 2009-11-20
> **Kevbert said:**
> You can get an older version from the Karmic Repos (via Synaptic) or if you want to risk it 2.1 is [[COLOR="Red"]here[/COLOR]]("http://packages.ubuntu.com/lucid/imagination"). You may have problems with dependencies (support files). You could try what Slimbo suggests after extracting all the files from the archive. There may be a readme file or an install document file within the tar.gz archive telling you how to install.

This is as clear as mud to me. Keeping it simple not

thanks for your help read me file below.

Imagination is a lightweight DVD slide show maker developed with GTK+2.

NOTE FOR PACKAGERS:
===================

Before packaging Imagination (unless this hasn't already been done) please
comment line 22 in file src/support.c from this:

#define PLUGINS_INSTALLED 0
to this:
#define PLUGINS_INSTALLED 1

If you fail to do so Imagination won't be able to load the transitions and the
transition's images when the package is installed.

UPGRADE FROM 1.5 TO 2.0 NOTES:
==============================

Because Imagination's backend changed from 1.5 to 2.0, old transition plugins do
not work with new version anymore. This and the fact that some transitions have
been grouped together may cause some trouble if you don't uninstall previous
version of Imagination prior installing 2.0.

But if you did this already, there is a simple fix. Just navigate to
Imagination's plugin folder (PREFIX/lib/imagination) and delete remnants of old
installation by executing:
$ su
# rm -f fade.*

or 
$ sudo rm -f fade.*  :confused:

---

### Post by Slimbo on 2009-11-20
> **ibbill said:**
> 
curious why the programs are tar files and not set  up as deb boggles my mind.(Keeping things simple would help)


tar.gz isn't supposed to be a program. It contains the source code which later on can be customized and compiled with some specific configuration and other tweaks.
Actually, it's fairly easy - just start doing it and try not to hit the Delete button every time something fails :)

---

### Post by QIII on 2009-11-20
Kevbert has the idea if you want to backport.  But as he says, that can be problematic.

There are great benefits to using the repos when an application is available there:

The app has been generally tested for performance with Ubuntu; there is a MOTU (Master of the Universe -- the guys who package stuff for the repos); and, perhaps most convenient, apps installed through Synaptic can be accounted for easily before you upgrade/fresh install and that list can be used to quickly re-install all the latest versions applicable for the new version of Ubuntu you have installed without having to re-install them one by one.

Install what is in the repos if you don't have a burning desire for the bleeding edge.  Backport if you think you can.

---

### Post by oldos2er on 2009-11-20
"curious why the programs are tar files and not set up as deb boggles my mind.(Keeping things simple would help)"

 Not everyone uses Debian or Debian-based (hence "deb" packages) versions of Linux. 

 As was mentioned, "tar" or tar.gz is just an archive which could contain anything.

---

### Post by ibbill on 2009-11-20
> **oldos2er said:**
> "curious why the programs are tar files and not set up as deb boggles my mind.(Keeping things simple would help)"

 Not everyone uses Debian or Debian-based (hence "deb" packages) versions of Linux. 

 As was mentioned, "tar" or tar.gz is just an archive which could contain anything.


Thanks for the info.

---

