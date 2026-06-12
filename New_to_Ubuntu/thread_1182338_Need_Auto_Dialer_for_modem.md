---
title: "Need Auto Dialer for modem"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by ghost_dancer on 2009-06-08
I'm using v9.04 (installed in Windows XP) and cannot get WvDial-1.60 to work because I don't know how to compile it. (another lame windows user). I live in the country and dialup is all that is available. Any help out there?

excerpt from README:

Compiling and Installing WvDial
===============================

If you are not using our pre-compiled Debian package, you will need to
compile WvDial yourself.  This is not too difficult as long as you have a
few things installed on your Linux system:

    - pppd 2.2.0f or 2.3.5, with the pppd program preferably 
        at /usr/sbin/pppd.

    - gcc 2.7.2 or higher, with g++.

    - GNU make; you may need version 3.75 or higher, I'm not sure.

    - WvStreams; version 4.4 or higher.

Almost any halfway modern Linux system should have all of these. The last is
available from [http://alumnit.ca/wiki/index.php?page=DownloadReleases](http://alumnit.ca/wiki/index.php?page=DownloadReleases)

Building WvDial is a simple matter.  First, check the Makefile to see if
everything looks okay to you.  By default, wvdial and wvdialconf will
install in /usr/local/bin with their man pages in /usr/local/man/man1. 
That's probably right for most systems.

To build and install WvDial, then:
    make
    make install

Assuming you don't have any compile errors (and really, you shouldn't,
right?) you now have an installed WvDial system.

==========
Thanks . . .

---

### Post by keplerspeed on 2009-06-08
Should be able to use the precomiled debian package from here: [http://packages.debian.org/lenny/wvdial](http://packages.debian.org/lenny/wvdial)

in this case download the i386 version (box at bottom of page) and double click on the package once downloaded. Should be straight forward from there.

---

### Post by GeorgeVita on 2009-06-09
Hi **ghost_dancer**

as **wvdial** package have some dependencies, read [http://ubuntuforums.org/showpost.php?p=7386429&postcount=8](http://ubuntuforums.org/showpost.php?p=7386429&postcount=8)

There are 5 .deb packages to install. You could make a zip file with all of them (be sure to check their integrity and 32/64 bit version).

1. [http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download](http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download)
2. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download)
3. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download)
4. [http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download](http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download)
5. [http://packages.ubuntu.com/jaunty/i386/wvdial/download](http://packages.ubuntu.com/jaunty/i386/wvdial/download)

My **.zip** file for **i386 32bit** (size: 1,04 MB):
[http://acomelectronics.com/GeorgeVita/wvdial_904_i386.zip](http://acomelectronics.com/GeorgeVita/wvdial_904_i386.zip)

Info and checksums included (read them: [http://acomelectronics.com/GeorgeVita/restore_wvdial.html](http://acomelectronics.com/GeorgeVita/restore_wvdial.html))

I test it by copying all to a USB memory stick, and then paste them (or unzip them) to the ubuntu **9.04** running pc into **/var/cache/apt/archives/** directory using **sudo nautilus** from terminal. Then I installed all packages by double clicking each icon (of .deb package) in "as listed in above" order (1,2,3,4 and finally 5).

Regards,
George

---

