---
title: "downloading and using .tar"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by datafiend on 2010-06-06
Hi all.
I've finally installed my linux on an old pc that was collecting dust and am trying to get into ubuntu.

How do you install a new app that you've downloaded using tar? I have downloaded the flash plugin, but I can't get it to install. 

Keep in mind I'm on UBUNTU 5.04 (i know it's old), but am hoping flash will still work on this.

also, when i installed ubuntu (from a disk) i don't think i ever created a root account, or if i did I can't log in as root anymore. any ideas on that one?

any help is appreciated.

---

### Post by MedianMajik on 2010-06-06
[Use this]("http://www.mattiasgeniar.be/wp-content/uploads/2008/10/linux-wallpaper-for-beginners.jpg") wallpaper to see commands for installing from source.  Note that installing from source assumes the tar or tar.gz file is located in your home directory (the one with your user name).

---

### Post by geoffjay on 2010-06-06
First off I would recommend getting a newer version of Ubuntu, you may run into a lot of issues trying to compile new software using an old kernel and old versions of Gnome/glib. I know I have at times.

Obviously check the repositories first for the package you're trying to install but if its not there the standard method of compiling from source starting from a tar.gz would be

$ tar zxvf application.tar.gz
$ cd application/
$ ./configure --prefix=/usr
$ make
$ sudo make install

Sometimes if the developer has set up an Autotools build environment before the configure you might have to run 

$ ./autogen.sh

but this is more commonly the case for code that comes from git/bzr/subversion branches. Definitely read the INSTALL and README documents for anything you want to compile.

As for the root account, Ubuntu doesn't set a password for it during installation, it's more common to prefix your commands with sudo to run as root. However, to load a root shell you can always:

$ sudo su -

---

### Post by 3rdalbum on 2010-06-06
Ubuntu 5.04 is ancient. Don't use it. I doubt Flash Player 10 would work on it, and I'd be surprised if Flash Player 9 would work. Any version of Flash Player that's older would be next-to-useless.

Ubuntu has never had a root account; instead you use 'sudo' to temporarily gain root permissions.

In later versions of Ubuntu, you simply install the 'flashplugin-nonfree' package using your package manager, so don't bother with the tar.gz. Just download Ubuntu 10.04 and it will be able to retrieve this package for you.

---

### Post by Paqman on 2010-06-06
> **3rdalbum said:**
> Ubuntu 5.04 is ancient. Don't use it.

+1 to this. It's no longer supported, so isn't receiving any security updates. Upgrade to a supported version immediately.

> **datafiend said:**
> 
How do you install a new app that you've downloaded using tar?

Generally speaking: you don't.

There shouldn't normally be any need to install software from a tarball. It's messy and can lead to an unstable system. Software on Ubuntu is installed through the built-in package manager that will download, decompress and install the package for you. Go to System > Admin > Synaptic Package Manager (or on newer versions Applications > Ubuntu Software Centre)

---

### Post by wojox on 2010-06-06
You wouldn't need to build it either. Just extract it and mv the driver to the proper place.

I also agree. Being 5.04 isn't supported anymore (no  more security updates), I would upgrade as well.

---

### Post by Soul-Sing on 2010-06-06
I think we shouldn't support 5.04 version installs (duh), they are full of security holes, unsafe, etc.
Neither an upgrade from it to 8.04.4, 9.04 or 10.4, the "way"is too long to make an upgrade a succes.
IMHO A clean install would do.

---

### Post by datafiend on 2010-06-06
ok guys - i get the hint d/l newer version of ubuntu. I guess 10.04 is the latest?

thanks for the help.

---

