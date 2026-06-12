---
title: "installing epiphany"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Merps on 2008-12-15
sudo apt-get install epiphany-browser
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package epiphany-browser is not available, but is referred to by another package

it is an old version of ubuntu, can I still install other applications to it and specifically browsers other than firefox?

---

### Post by mkvnmtr on 2008-12-15
I believe I had it in 6.06. The problem might be that you are using a distro that no longer has support. What system are you using?

---

### Post by Merps on 2008-12-15
I think it is 7.04, if it is out of support, is there no way to install apps anymore?  the problem is that firefox is clogging up my system.

I had tried applications --> add/remove and synaptic package manager and they all seem to be out of action.

That said there must be a way to install applications on old versions?

---

### Post by Michael.Godawski on 2008-12-15
You can try to download a .deb file of the application you want to install.
Try to search for it on the inet.

---

### Post by Merps on 2008-12-15
> **Michael.Godawski said:**
> You can try to download a .deb file of the application you want to install.
Try to search for it on the inet.

you mean try and install from a source file, or is there a debian installer too?

from here?
[http://live.gnome.org/Epiphany/Downloads](http://live.gnome.org/Epiphany/Downloads)

then how to install?

---

### Post by AndyCooll on 2008-12-15
There should be a deb installer. Epiphany's homepage is here: [Epiphany]("http://projects.gnome.org/epiphany/")

:cool:

---

### Post by Michael.Godawski on 2008-12-15
try this

[http://packages.debian.org/en/etch/i386/epiphany-browser/down](http://packages.debian.org/en/etch/i386/epiphany-browser/down)

---

### Post by Merps on 2008-12-15
> **Michael.Godawski said:**
> try this

[http://packages.debian.org/en/etch/i386/epiphany-browser/down](http://packages.debian.org/en/etch/i386/epiphany-browser/down)

 Debian

skip the navigation
>> Debian >> Packages
Error

two or more packages specified (down epiphany-browser)


it points to an error, what to do with it anyway, I am not familiar with debian at all.

---

### Post by Merps on 2008-12-15
> **AndyCooll said:**
> There should be a deb installer. Epiphany's homepage is here: [Epiphany]("http://projects.gnome.org/epiphany/")

:cool:

cool link, and I wrote a question to their mailing list about this, but I can't see an obvious approach there either.

---

### Post by Merps on 2008-12-15
> **AndyCooll said:**
> There should be a deb installer.


did you mean this?

su && apt-get install epiphany-browser?

I tried it anyway:

su && apt-get install epiphany-browser
Password: 
su: Authentication failure
Sorry.

---

### Post by Merps on 2008-12-15
we are in absolute starters, aren't we? ok then

what about [http://www.getdeb.net/](http://www.getdeb.net/)

is it a case of finding the correct deb file and double clicking on it?

ah nuts it only has:

Ubuntu Intrepid	(32 bits)
Ubuntu Intrepid	(64 bits)
Ubuntu Hardy	(32 bits)
Ubuntu Hardy	(64 bits)

maybe there is another site with older deb files?

---

### Post by Tom--d on 2008-12-15
If you are on Ubuntu 7.04. I think there is no support left. The repos have been closed. Thats why you can't install anything.

Upgrade to 8.04 LTS or 8.10; both have epiphany.

---

### Post by Merps on 2008-12-15
ok I found these, now what do I do with them?



Package epiphany-browser

    * etch (stable) (gnome): Intuitive GNOME web browser
      2.14.3-7: alpha amd64 arm hppa i386 ia64 mips mipsel powerpc s390 sparc

[http://packages.debian.org/search?keywords=epiphany&searchon=names&suite=stable&section=all](http://packages.debian.org/search?keywords=epiphany&searchon=names&suite=stable&section=all)

which leads onto here:
[http://packages.debian.org/etch/epiphany-browser](http://packages.debian.org/etch/epiphany-browser)

and at the bottom is:

Download epiphany-browser
Download for all available architectures Architecture 	Package Size 	Installed Size 	Files
alpha 	4,036.5 kB	11572 kB 	[list of files]
amd64 	3,986.2 kB	11176 kB 	[list of files]
arm 	3,955.0 kB	11028 kB 	[list of files]
hppa 	4,075.7 kB	11440 kB 	[list of files]
i386 	3,969.9 kB	9924 kB 	[list of files]

but there is no information regarding which distros and versions of the distro it is designed to be run on.

It seems a shame that working repositories for old versions are blocked.  My problem is that the hardware I have doesn't run so well with the latest distros and 7.04 works great except the browser firefox makes me crazy.

---

### Post by Michael.Godawski on 2008-12-15
If you are on a 32 bit machine (you probably are) then the i386 package is for you.
Debs are like exes in windows, double click that's it. But you will likely run into dependencies issues. 

So make a backup of your data (when you do not have an separate home partition - do a backup anyway :p) and upgrade, or do a fresh install of intrepid. Just my advice...

edit: what hardware do you have?

---

### Post by bapoumba on 2008-12-15
Please do not mix up debian repos with ubuntu, that's asking for trouble..

Feisty has reached end of life and the repos moved here: [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

Epiphany for Feisty (look at the bottom of the page): [http://packages.ubuntu.com/feisty/epiphany-browser](http://packages.ubuntu.com/feisty/epiphany-browser)

If you can upgrade to Hardy, please do.

---

### Post by Merps on 2008-12-15
> **bapoumba said:**
> Please do not mix up debian repos with ubuntu, that's asking for trouble..

Feisty has reached end of life and the repos moved here: [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

Epiphany for Feisty (look at the bottom of the page): [http://packages.ubuntu.com/feisty/epiphany-browser](http://packages.ubuntu.com/feisty/epiphany-browser)

If you can upgrade to Hardy, please do.

That is awesome, lol, I have been trying to get that running for ages. *does a couple of laps of the room* :D  (posted while using epiphany on 7.04)

---

