---
title: "Ubuntu"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by JrHoratio on 2010-08-02
Is there any real difference between Ubuntu and Fedora?

---

### Post by kaldor on 2010-08-02
Of course :)

Different software, different purposes, different utilities.

-Fedora doesn't use sudo or apt-get to do things via the terminal.

-Fedora uses the latest (and often not so greatest) software but fixes the bugs and sends them back upstream. 

-Different package management. It's RPM powered.

-More hands-on than Ubuntu; install and configure your drivers by hand, etc

-Uses the default GNOME environment instead of customizing it (much).

-Fedora is based on RedHat, Ubuntu is based on Debian (big difference).

Just try out both and you'll see what I mean.

---

### Post by snowpine on 2010-08-02
This link will answer many of your questions:

[http://distrowatch.com/dwres.php?resource=major](http://distrowatch.com/dwres.php?resource=major)

---

### Post by -kg- on 2010-08-02
In relation to what?

They use different package managers.  Ubuntu uses the Debian based Aptitude while Fedora uses RPM (Redhat Package Manager).

Ubuntu uses GRUB 2 while Fedora (as far as I know) still uses Legacy GRUB (unpatched for accessing an ext4 partition...you still have to have a separate /boot partition formatted to ext3).  This is the default...I think that GRUB 2 is available in Fedora's repositories.

Ubuntu is developed as an OS in itself, while Fedora is used as a development platform for Redhat Enterprise.

There are quite a few differences.  I'm sure others will come up with some more.

---

### Post by limestone on 2010-08-02
I would like to compare fedora as the opposite of debian and Ubuntu as the opposite of suse :)
That's just how I experience it. Does not have with the question to do, but I needed that said. :P

---

### Post by RJ12 on 2010-08-02
As everyone is saying, Fedora is RPM based and uses yum as the package manager and Ubuntu is Debian which uses Aptitude (not going to actually be in 10.10) and Apt. Fedora also doesn't really have a restricted-extras package, but does have RPMFusion as a repo to get things like Flash and MP3 codecs. There is easyLife to help with that too. Fedora does not really have a customized GNOME enviornment like Ubuntu. It ships with mainly the standard one. Fedora also does not use Sudo (but you can install it using easyLife) instead you switch the the root account using "su". Ubuntu also uses Ubiquity as the installer while Fedora uses Anaconda. You configure your account after the system is installed instead of in the beginning like in the Ubuntu installer.

---

### Post by gdonwallace on 2010-08-02
The short answer is Yes, there are a lot of differences between the two.  Most importantly, Fedora is a Red Hat Linux based release where Ubuntu is based on Debian.  Depending on how it is installed, the base Fedora comes with KDE desktop as the "general" while Ubuntu uses Gnome.  The underlying technology that runs the two is quite similar. (i.e. Directory structure, commands, etc)  The biggest difference is how programs get installed and how updates are handled on the two systems.

Fedora uses the Yellow Update Manager (YUM for short) and RPM (Red Hat Package Manager) files for downloading, updating and Installing programs.  Ubuntu uses Apt-get (Apptitude) for its updates and generally uses .deb based files for updates and downloads / installs.

Most everything else will be the same.  There are a few minor differences, but they can be worked through with a little forum reading / searching.  I have used both, although I use Ubuntu more often, and find that there is not much that I can't do or find an answer too for Fedora.

---

### Post by JrHoratio on 2010-08-15
> **kaldor said:**
> Of course :)

Different software, different purposes, different utilities.

-Fedora doesn't use sudo or apt-get to do things via the terminal.

-Fedora uses the latest (and often not so greatest) software but fixes the bugs and sends them back upstream. 

-Different package management. It's RPM powered.

-More hands-on than Ubuntu; install and configure your drivers by hand, etc

-Uses the default GNOME environment instead of customizing it (much).

-Fedora is based on RedHat, Ubuntu is based on Debian (big difference).

Just try out both and you'll see what I mean.
Yeah, i'm in a situation where I am using both in a class. I'm really new to this... So what is Debian?

---

### Post by Zorgoth on 2010-08-16
Debian is an Linux distro, and is Ubuntu's granddaddy.  ".deb" in fact stands for a Debian package.  Ubuntu is basically a fork of Debian.

---

### Post by mastablasta on 2010-08-16
Debian is also supposedly more stable.

---

### Post by JrHoratio on 2010-08-18
Thanks for all your help.

---

