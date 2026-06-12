---
title: "Packages"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by taskma on 2010-08-31
Hi

I am a Windows user moving over to Ubuntu, because the company where I work at run too many applications on Windows that slow down Windows too much.  Example of a test I ran today.  To build my Java apps take about 2 minutes in Windows and 8 seconds on Ubuntu
I don't really know what to search for so here is my question.  It has probably been asked before, but I don't have a clue where to start.

The work problem:
I don't have unlimited internet at work, 200MB allowed per month and max of 5MB file download at a time

Solution:
Download applications at home and take to work

The download problem:
When I download applications with Ubuntu, e.g. Wine, they also install.  I don't know where the download is or how to make a single file from everything that was downloaded.  From what I understand Linux works with packages, but isn't there an application that I can use to just download a package and not install it?

Example on this Wine page
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) there is this link apt://wine1.3
When I go to that link, Wine installs automatically.  I need to get the Wine file so that I can take it to work and install there

This would be same for everything really.  I can't install KDE at work except if I take a full live CD on a USB stick (don't have CD players) and then build a machine from that.

If there is an application that can do this it can solve all download issues I have, I think

---

### Post by oldos2er on 2010-08-31
```
sudo apt-get -d install wine
``` will do what you want. Package files are stored in /var/cache/apt/archives

---

### Post by Zeike on 2010-08-31
Alternatively you can download official packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by taskma on 2010-09-01
Thank you.  That will help alot

---

### Post by anand_30 on 2010-09-01
hi,
I am relatively new user to ubuntu but I have tried to take .deb files in /var/cache/apt/archives and install them on other computer.But this didn't work all the time.For most of the times there is 'dependencies not satisfied' problem.Also downloading packages from website is too time wasting as it requires us to search many pages to get desired pacakge.

So to avoid these problems there is another way.
For this you will need freshly installed ubuntu os(live usb will do).
Now open synaptic search for your software and select it to install.Then without applying the changes go to File>>Generate package download script>>give name e.g. wine >>save it in folder e.g.wine packages.

Now go to that folder and double click on that file>>Run in terminal.
All packages including all dependencies will be downloaded in wine folder.

Now in synaatic just unmak all in Edit(as far as u don't want these softwares installed on live usb)

Now copy folder wine packages to other computer.using terminal go to that folder and execute command 
```
sudo dpkg -iR ./ 
```
You are done.

I am not that much knowledgeable in ubuntu but this always work for me.

Hope this helps.

---

### Post by Ampi on 2010-09-01
I normally always have internet so I don't have this problem. 

When I install software through the Synaptic Package Manager (which has a very easy graphical interface) before you "Apply" the changes (including automatically all the dependencies you are going to need) there is the possibility to check the option "Download package files only". 

It sounds to me that this would be the perfect solution, no? You then can use the packages including the dependencies on your computer at work...

---

### Post by howefield on 2010-09-01
You can also buy repository DVDs for not a lot of money.

Suppose it depends on often you'll use them as to whether it is a useful thing, but just to let you know that they are available.

---

### Post by taskma on 2010-09-02
Thank you guys.  That is alot of help.  I will start by creating a clean live CD usb stick again as my downloader

The repo DVD sounds like a good idea, but living in South Africa I don't know how long it will take to get the DVD's and I usually want something as soon as I find it.  Doesn't the DVD have rather old versions?

---

### Post by taskma on 2010-09-03
I did this now with Pidgin and Alien.  Haven't tested the installs yet.  Alien wasn't happy.  It added cdrom for some of the deb files.  I removed that and it downloaded.  Why would it add cdrom?

Alien file before
#!/bin/sh
wget -c cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/main/x/xz-utils/xz-utils_4.999.9beta+20091116-1_i386.deb
wget -c cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb
wget -c cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/main/d/dpkg/dpkg-dev_1.15.5.6ubuntu4.1_all.deb
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/h/html2text/html2text_1.3.2a-14build1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/html2text/html2text_1.3.2a-14build1_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/g/gettext/gettext_0.17-8ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gettext/gettext_0.17-8ubuntu3_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/i/intltool-debian/intltool-debian_0.35.0+20060710.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/intltool-debian/intltool-debian_0.35.0+20060710.1_all.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/p/po-debconf/po-debconf_1.0.16_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/po-debconf/po-debconf_1.0.16_all.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/d/debhelper/debhelper_7.4.15ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/debhelper/debhelper_7.4.15ubuntu1_all.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/l/lua5.1/liblua5.1-0_5.1.4-5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/lua5.1/liblua5.1-0_5.1.4-5_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpmio0_4.7.2-1lbuild1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpmio0_4.7.2-1lbuild1_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm-common_4.7.2-1lbuild1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm-common_4.7.2-1lbuild1_all.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpm0_4.7.2-1lbuild1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpm0_4.7.2-1lbuild1_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpmbuild0_4.7.2-1lbuild1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpmbuild0_4.7.2-1lbuild1_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm2cpio_4.7.2-1lbuild1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm2cpio_4.7.2-1lbuild1_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm_4.7.2-1lbuild1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm_4.7.2-1lbuild1_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/a/alien/alien_8.79ubuntu0.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/alien/alien_8.79ubuntu0.1_all.deb)
wget -c cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.3-4ubuntu5_i386.deb
wget -c cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/main/g/gcc-4.4/g++-4.4_4.4.3-4ubuntu5_i386.deb
wget -c cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/main/g/gcc-defaults/g++_4.4.3-1ubuntu1_i386.deb
wget -c cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/main/b/build-essential/build-essential_11.4build1_i386.deb
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/c/cvs/cvs_1.12.13-12ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cvs/cvs_1.12.13-12ubuntu1_i386.deb)
wget -c cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/libs/libsys-hostname-long-perl/libsys-hostname-long-perl_1.4-2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/libs/libsys-hostname-long-perl/libsys-hostname-long-perl_1.4-2_all.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/libm/libmail-sendmail-perl/libmail-sendmail-perl_0.79.16-1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/libm/libmail-sendmail-perl/libmail-sendmail-perl_0.79.16-1_all.deb)



Alien file after
#!/bin/sh
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/h/html2text/html2text_1.3.2a-14build1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/html2text/html2text_1.3.2a-14build1_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/g/gettext/gettext_0.17-8ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gettext/gettext_0.17-8ubuntu3_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/i/intltool-debian/intltool-debian_0.35.0+20060710.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/intltool-debian/intltool-debian_0.35.0+20060710.1_all.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/p/po-debconf/po-debconf_1.0.16_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/po-debconf/po-debconf_1.0.16_all.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/d/debhelper/debhelper_7.4.15ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/debhelper/debhelper_7.4.15ubuntu1_all.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/l/lua5.1/liblua5.1-0_5.1.4-5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/lua5.1/liblua5.1-0_5.1.4-5_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpmio0_4.7.2-1lbuild1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpmio0_4.7.2-1lbuild1_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm-common_4.7.2-1lbuild1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm-common_4.7.2-1lbuild1_all.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpm0_4.7.2-1lbuild1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpm0_4.7.2-1lbuild1_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpmbuild0_4.7.2-1lbuild1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpmbuild0_4.7.2-1lbuild1_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm2cpio_4.7.2-1lbuild1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm2cpio_4.7.2-1lbuild1_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm_4.7.2-1lbuild1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm_4.7.2-1lbuild1_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/a/alien/alien_8.79ubuntu0.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/alien/alien_8.79ubuntu0.1_all.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/c/cvs/cvs_1.12.13-12ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cvs/cvs_1.12.13-12ubuntu1_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/libs/libsys-hostname-long-perl/libsys-hostname-long-perl_1.4-2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/libs/libsys-hostname-long-perl/libsys-hostname-long-perl_1.4-2_all.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/libm/libmail-sendmail-perl/libmail-sendmail-perl_0.79.16-1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/libm/libmail-sendmail-perl/libmail-sendmail-perl_0.79.16-1_all.deb)

---

