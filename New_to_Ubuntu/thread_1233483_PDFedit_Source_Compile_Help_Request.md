---
title: "PDFedit Source Compile Help Request"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by lkraemer on 2009-08-06
I am running Ubuntu 8.04.3 LTS, and I have downloaded the source for
PDFedit version 0.4.3, and extracted the tar.gz to a folder located at
/home/larry/pdfedit-0.4.3.  I was thinking that a compile would be easy
with the information I found on this forum.

I read the README document that was extracted, and I have searched the
forum and found two postings on how to compile the source.  I have
version 3.2 installed from the repos, but would like to get that upgraded 
to version 4.3 to fix a BUG I have found when I delete multiple sheets
and the software exits abruptly.

PDFEdit Dependencies needed are listed here:
[http://packages.ubuntu.com/hardy/utils/pdfedit](http://packages.ubuntu.com/hardy/utils/pdfedit)

libc6
libfontconfig1
libfreetype6
libgcc1
libice6
libjpeg62
libpaper1
libpng12-0
libqt3-mt
libsm6
libstdc++6
libx11-6
libxext6
zlib1g

libboost-dev		I NEED
libcppunit-dev		I NEED

build-essential
bcp			I NEED
doxygen			I NEED
I VERIFIED in SYNAPTIC that all were installed except for the ones I have
marked as NEED.  I installed those with Synaptic.

This website says I also need the following:
[http://www.linuxtent.com/?p=117](http://www.linuxtent.com/?p=117)
sudo apt-get install build-essential boost-build libboost-thread-dev libboost-thread1.34.1 libboost-iostreams1.34.1 libboost-iostreams-dev qt3-dev-tools

I installed these with sudo apt-get xxxx
Which installs the following:
comerr-dev libaudio-dev libcupsys2-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libgl1-mesa-dev libglu1-mesa-dev libgnutls-dev libgnutlsxx13 libgpg-error-dev libice-dev libjpeg62-dev libkadm55 libkrb5-dev liblcms1-dev liblzo2-dev libmng-dev libopencdk10-dev libpng12-dev libpthread-stubs0 libpthread-stubs0-dev libqt3-headers libqt3-mt-dev libsm-dev libtasn1-3-dev libx11-dev libxau-dev libxcb-xlib0-dev libxcb1-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxmu-dev libxmu-headers libxrandr-dev libxrender-dev libxt-dev mesa-common-dev x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev 

Before running ./configure the site states to do the following:
export QTDIR=/usr/share/qt3
sudo ln -s /usr/include/qt3/ /usr/share/qt3/include
sudo apt-get install libqt3-mt-dev

Then:
./configure
make
sudo make install

And this website states to make a deb, so it it easier to remove, if needed.
[http://ubuntuforums.org/archive/index.php/t-538338.html](http://ubuntuforums.org/archive/index.php/t-538338.html)


I can't get the compile to work.  And I have so many warnings and errors,
that I am way over my head.  And at this point I haven't a clue as to
how to get all the files that have been created, removed from their 
various locations, or how to get back to a system state before this
compile was attempted.

Has anyone been able to compile version 4.3 of PDFedit, or have any ideas
that would be of help?  I am afraid I am in over my head at this point.

Thanks.

lkraemer

---

