---
title: "A dpkg issue that blows."
date: 2009-01-18
forum: New to Ubuntu
---

### Post by TeresaStyles on 2009-01-18
Hi.  I am new here but have been using Ubuntu for several years.

I upgraded from 7 to 8.10 making sure everything was updated first. When I went to install a program via Synaptic I got this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

OK, fine I sudo dpkg --configure -a and get this:

Options marked[*] produce a lot of output - pipe it through `less' or `more' !
teresa@teresa-desktop:~$ sudo dpkg --configure -a
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed

Someone suggested I sudo dpkg -l | grep -v ii | grep -v rc
and post the results in a new thread (this one).  Here are the results:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
||/ Name                                       Version                                 Description
+++-==========================================-=======================================-============================================
iW  cups                                       1.3.9-2ubuntu6.1                        Common UNIX Printing System(tm) - server
iU  cupsys                                     1.3.9-2ubuntu6.1                        Common UNIX Printing System (transitional pa
iW  xterm                                      235-1ubuntu1.1                          X terminal emulator


It looks to me like a prior version of cups failed to clean up after itself.  Then again I don't know much hence this thread.  What should I do?  A clean install is an option as I save all my data to a separate physical HDD so it would not be a big pain in the ***.  However I would like to know how to fix this as I am eager to learn about Linux.

Thanks guys!

---

### Post by stderr on 2009-01-18
Hi again

Firstly I would advise doing 

sudo dpkg --configure xterm
sudo dpkg --configure cups
sudo dpkg --configure cupsys

and posting the output.

We may end up having to remove (purge) those packages and their dependencies, and reinstall them...

---

### Post by cdtech on 2009-01-18
I would try this first:
```
sudo dpkg --configure -a && sudo apt-get -f install
```
Then try the update........

**UPDATE::.**
You may have a corrupted file within the "/var/lib/dpkg/updates" folder. In this case you can remove any temporary files within this directory:
```
cd /var/lib/dpkg/updates
```
Then remove the files within that directory:
```
sudo rm *
```
Then your update should work.........

---

### Post by TeresaStyles on 2009-01-18
teresa@teresa-desktop:~$ sudo dpkg --configure xterm
[sudo] password for teresa: 
dpkg: error processing xterm (--configure):
 package xterm is not ready for configuration
 cannot configure (current status `triggers-awaited')
Errors were encountered while processing:
 xterm
teresa@teresa-desktop:~$ sudo dpkg --configure cups
dpkg: error processing cups (--configure):
 package cups is not ready for configuration
 cannot configure (current status `triggers-awaited')
Errors were encountered while processing:
 cups
teresa@teresa-desktop:~$ sudo dpkg --configure cupsys
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
teresa@teresa-desktop:~$

---

### Post by TeresaStyles on 2009-01-18
> **cdtech said:**
> I would try this first:
```
sudo dpkg --configure -a && sudo apt-get -f install
```
Then try the update........

**UPDATE::.**
You may have a corrupted file within the "/var/lib/dpkg/updates" folder. In this case you can remove any temporary files within this directory:
```
cd /var/lib/dpkg/updates
```
Then remove the files within that directory:
```
sudo rm *
```
Then your update should work.........

sudo dpkg --configure -a && sudo apt-get -f install
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed

None of that worked.  There are no longer any temp. files there and I keep getting the damned error.

---

### Post by cdtech on 2009-01-18
Clear the cache:
```
sudo apt-get autoremove
```

---

### Post by roshanjose on 2009-01-18
just run these 2 commands in the terminal in the same order as i typed

sudo dpkg --configure -a 

 sudo apt-get -f install



this will help....if it just tell me what's the outcome

---

### Post by stderr on 2009-01-18
> **TeresaStyles said:**
> teresa@teresa-desktop:~$ sudo dpkg --configure cupsys
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

Hmm, well, personally I'd now try:

```
sudo apt-get purge cupsys
```

and then

```
sudo dpkg --configure -a
```

well you may as well do as recommended by cdtech

```
sudo dpkg --configure -a && sudo apt-get -f install
```

and then re-install cupsys

```
sudo apt-get install cupsys
```

---

### Post by TeresaStyles on 2009-01-18
> **cdtech said:**
> Clear the cache:
```
sudo apt-get autoremove
```

teresa@teresa-desktop:~$ sudo apt-get autoremove
[sudo] password for teresa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: error processing cups (--configure):
 package cups is not ready for configuration
 cannot configure (current status `triggers-awaited')
Processing triggers for menu ...
dpkg: error processing xterm (--configure):
 package xterm is not ready for configuration
 cannot configure (current status `triggers-awaited')
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

Nope.

---

### Post by TeresaStyles on 2009-01-18
> **roshanjose said:**
> just run these 2 commands in the terminal in the same order as i typed

sudo dpkg --configure -a 

 sudo apt-get -f install



this will help....if it just tell me what's the outcome

I tried that.

---

### Post by TeresaStyles on 2009-01-18
> **stderr said:**
> Hmm, well, personally I'd now try:

```
sudo apt-get purge cupsys
```

and then

```
sudo dpkg --configure -a
```

well you may as well do as recommended by cdtech

```
sudo dpkg --configure -a && sudo apt-get -f install
```

and then re-install cupsys

```
sudo apt-get install cupsys
```

teresa@teresa-desktop:~$ sudo apt-get purge cupsys
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

The same crap.  Did my upgrade just go terribly wrong and I should do a fresh install?

---

### Post by cdtech on 2009-01-18
Let's find out which packages are causing the problems:
```
sudo dpkg -l | grep -v ^ii
```

---

### Post by stderr on 2009-01-18
> **TeresaStyles said:**
> teresa@teresa-desktop:~$ sudo apt-get purge cupsys
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

The same crap.  Did my upgrade just go terribly wrong and I should do a fresh install?

There'll be a way round it... we just haven't found it yet :-k

@cdtech: that's the first thing I recommended - see Teresa's first post :)

---

### Post by cdtech on 2009-01-18
sorry, missed that......:P

---

### Post by TeresaStyles on 2009-01-18
> **cdtech said:**
> Let's find out which packages are causing the problems:
```
sudo dpkg -l | grep -v ^ii
```

Sorry for my late replies in my own thread.  Things are hectic in my home right now.

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version                                 Description
+++-==========================================-=======================================-============================================
rc  bluez-audio                                3.26-0ubuntu6                           Bluetooth audio support
rc  console-tools                              1:0.2.3dbs-65ubuntu7                    Linux console and font utilities
iW  cups                                       1.3.9-2ubuntu6.1                        Common UNIX Printing System(tm) - server
rc  cups-pdf                                   2.4.8-1ubuntu1                          PDF printer for CUPS
iU  cupsys                                     1.3.9-2ubuntu6.1                        Common UNIX Printing System (transitional pa
rc  dhcdbd                                     3.0-1ubuntu1                            D-Bus interface to the ISC DHCP client
rc  discover1                                  1.7.22ubuntu1                           hardware identification system
rc  hwdb-client-common                         0.6.14                                  common files for Ubuntu Hardware Database cl
rc  iamerican                                  3.1.20.0-4.4                            An American English dictionary for ispell
rc  ibritish                                   3.1.20.0-4.4                            A British English dictionary for ispell
rc  libavcodec1d                               3:0.cvs20070307-5ubuntu7.1              ffmpeg codec library
rc  libavformat1d                              3:0.cvs20070307-5ubuntu7.1              ffmpeg file format library
rc  libavutil1d                                3:0.cvs20070307-5ubuntu7.1              ffmpeg utility library
rc  libbind9-30                                1:9.4.2.dfsg.P2-2                       BIND9 Shared Library used by BIND
rc  libbluetooth2                              3.29-0ubuntu1                           Library to use the BlueZ Linux Bluetooth sta
rc  libcamel1.2-11                             2.22.3-0ubuntu2                         The Evolution MIME message handling library
rc  libchromexvmc1                             1:0.2.901-0ubuntu4                      XvMC Libraries used by the Openchrome VIA dr
rc  libchromexvmcpro1                          1:0.2.901-0ubuntu4                      XvMC Pro Libraries used by the Openchrome VI
rc  libdc1394-13                               1.1.0-5ubuntu1                          high level programming interface for IEEE139
rc  libdiscover1                               1.7.22ubuntu1                           hardware identification library
rc  libdjvulibre15                             3.5.20-2                                Runtime support for the DjVu image format
rc  libdns32                                   1:9.4.2-10                              DNS Shared Library used by BIND
rc  libdns35                                   1:9.4.2.dfsg.P2-2                       DNS Shared Library used by BIND
rc  libedataserver1.2-9                        2.22.3-0ubuntu2                         Utility library for evolution data servers
rc  libffi4                                    4.2.4-1ubuntu3                          Foreign Function Interface library runtime
rc  libgail18                                  1.22.1-0ubuntu1                         GNOME Accessibility Implementation Library -
rc  libgdl-gnome-1-0                           0.7.11-1                                GNOME DevTool libraries (GNOME)
rc  libgmime-2.0-2                             2.2.11-2ubuntu1                         MIME library
rc  libgnome-desktop-2                         1:2.22.3-0ubuntu1                       Utility library for loading .desktop files -
rc  libgnomekbd2                               2.22.0-1                                GNOME library to manage keyboard configurati
rc  libgnomekbdui2                             2.22.0-1                                User interface library for libgnomekbd - sha
rc  libgnutls13                                2.0.4-1ubuntu2.1                        the GNU TLS library - runtime library
rc  libgpmg1                                   1.19.6-25ubuntu1                        General Purpose Mouse - shared library
rc  libgucharmap6                              1:2.22.1-0ubuntu2                       Unicode browser widget library (shared libra
rc  libhunspell-1.1-0                          1.1.9-1                                 spell checker and morphological analyzer (sh
rc  libisc32                                   1:9.4.2-10ubuntu0.1                     ISC Shared Library used by BIND
rc  libisc35                                   1:9.4.2.dfsg.P2-2                       ISC Shared Library used by BIND
rc  libisccc30                                 1:9.4.2.dfsg.P2-2                       Command Channel Library used by BIND
rc  libisccfg30                                1:9.4.2.dfsg.P2-2                       Config File Handling Library used by BIND
rc  liblame0                                   3.97-0.0                                LAME Ain't an MP3 Encoder
rc  libltdl3                                   1.5.26-1ubuntu1                         A system independent dlopen wrapper for GNU 
rc  liblwres30                                 1:9.4.2.dfsg.P2-2                       Lightweight Resolver Library used by BIND
rc  libmtp7                                    0.2.6.1-2ubuntu1                        Media Transfer Protocol (MTP) library
rc  libntfs-3g23                               1:1.2216-1ubuntu2                       ntfs-3g filesystem in userspace (FUSE) libra
rc  libopenal0a                                1:0.0.8-7                               OpenAL is a portable library for 3D spatiali
rc  libopencdk10                               0.6.6-1ubuntu1                          Open Crypto Development Kit (OpenCDK) (runti
rc  libopenexr2ldbl                            1.2.2-4.4ubuntu1                        runtime files for the OpenEXR image library
rc  libparted1.7-1                             1.7.1-5.1ubuntu9.1                      The GNU Parted disk partitioning shared libr
rc  libpoppler-glib2                           0.6.4-1ubuntu3.1                        PDF rendering library (GLib-based shared lib
rc  libpoppler2                                0.6.4-1ubuntu3.1                        PDF rendering library
rc  libpostproc1d                              3:0.cvs20070307-5ubuntu7.1              ffmpeg video postprocessing library
rc  libsmbios1                                 0.13.10-1ubuntu1.1                      Provide access to (SM)BIOS information -- dy
rc  libsvg1                                    0.1.4-4                                 library for parsing SVG files (shared librar
rc  libtotem-plparser10                        2.22.3-0ubuntu2                         Totem Playlist Parser library - runtime vers
rc  libx264-57                                 1:0.svn20071224-0.0ubuntu1              x264 video coding library
rc  linux-image-2.6.24-18-generic              2.6.24-18.32                            Linux kernel image for version 2.6.24 on x86
rc  linux-image-2.6.24-19-generic              2.6.24-19.41                            Linux kernel image for version 2.6.24 on x86
rc  linux-restricted-modules-2.6.24-18-generic 2.6.24.13-18.41                         Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                         Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-ubuntu-modules-2.6.24-18-generic     2.6.24-18.26                            Ubuntu supplied Linux modules for version 2.
rc  linux-ubuntu-modules-2.6.24-19-generic     2.6.24-19.28                            Ubuntu supplied Linux modules for version 2.
rc  myspell-en-us                              1:2.4.0~m240-1ubuntu1                   English_american dictionary for myspell
rc  scrollkeeper                               0.3.14-15ubuntu1                        A free electronic cataloging system for docu
rc  xserver-xorg-video-via                     1:0.2.2-5                               X.Org X server -- VIA display driver
iW  xterm                                      235-1ubuntu1.1                          X terminal emulator

And I do appreciate all of you trying to help me out.

---

### Post by kansasnoob on 2009-01-18
> **TeresaStyles said:**
> Hi.  I am new here but have been using Ubuntu for several years.

I upgraded from 7 to 8.10 making sure everything was updated first. When I went to install a program via Synaptic I got this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

OK, fine I sudo dpkg --configure -a and get this:

Options marked[*] produce a lot of output - pipe it through `less' or `more' !
teresa@teresa-desktop:~$ sudo dpkg --configure -a
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed

Someone suggested I sudo dpkg -l | grep -v ii | grep -v rc
and post the results in a new thread (this one).  Here are the results:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
||/ Name                                       Version                                 Description
+++-==========================================-=======================================-============================================
iW  cups                                       1.3.9-2ubuntu6.1                        Common UNIX Printing System(tm) - server
iU  cupsys                                     1.3.9-2ubuntu6.1                        Common UNIX Printing System (transitional pa
iW  xterm                                      235-1ubuntu1.1                          X terminal emulator


It looks to me like a prior version of cups failed to clean up after itself.  Then again I don't know much hence this thread.  What should I do?  A clean install is an option as I save all my data to a separate physical HDD so it would not be a big pain in the ***.  However I would like to know how to fix this as I am eager to learn about Linux.

Thanks guys!

I have a real dumb question, you said, "I upgraded from 7 to 8.10 making sure everything was updated first."

It's not possible to upgrade from 7.04 or 7.10 to 8.10. Lets say it was 7.10 (Gutsy), you'd first have to upgrade to 8.04.1 and then upgrade to 8.10.

So the dumb question is, what version did you upgrade from and what version did you upgrade to? And what method did you use to upgrade?

It might be helpful (at least interesting) to see the output of:

```
cat /etc/apt/sources.list
```

---

### Post by stderr on 2009-01-18
> **TeresaStyles said:**
> Things are hectic in my home right now.

Oh, we'll let you off this once ;)

Could you try running this? It should give you more debugging info. I'm not sure how useful it'll be though... but I think 73773 should be the most verbose output possible, if my quick maths serves me well :p

```
sudo dpkg -D73773 --configure -a
```

---

### Post by igknighted on 2009-01-18
> **kansasnoob said:**
> I have a real dumb question, you said, "I upgraded from 7 to 8.10 making sure everything was updated first."

It's not possible to upgrade from 7.04 or 7.10 to 8.10. Lets say it was 7.10 (Gutsy), you'd first have to upgrade to 8.04.1 and then upgrade to 8.10.

So the dumb question is, what version did you upgrade from and what version did you upgrade to? And what method did you use to upgrade?

It might be helpful (at least interesting) to see the output of:

```
cat /etc/apt/sources.list
```

Well, it is possible to TRY to go directly from 7.XX to 8.10, but you would end up in dependency hell like this most likely.  @OP... if you did try to skip releases in an upgrade, save any important info you might have and do a clean install.

---

### Post by TeresaStyles on 2009-01-18
> **kansasnoob said:**
> I have a real dumb question, you said, "I upgraded from 7 to 8.10 making sure everything was updated first."

It's not possible to upgrade from 7.04 or 7.10 to 8.10. Lets say it was 7.10 (Gutsy), you'd first have to upgrade to 8.04.1 and then upgrade to 8.10.

So the dumb question is, what version did you upgrade from and what version did you upgrade to? And what method did you use to upgrade?

It might be helpful (at least interesting) to see the output of:

```
cat /etc/apt/sources.list
```

OK, I installed it from 7.10 via CD originally.  Then I upgraded I guess twice since you think what I did is impossible.  The first upgrade I think was done via a prompt saying an upgrade is available.  The second one (to 8.10 intrepid) was done with sudo apt-get upgrade.

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports restricted main multiverse universe

---

### Post by TeresaStyles on 2009-01-18
OK, sorry.  I didn't read your post well enough.  I must have skipped an upgrade there.  No wonder everything is FUBAR.  Thanks for all your help.  I will reinstall.

---

### Post by sfagerhaug on 2009-01-19
I had the same issue and did the following to get around it:

[LIST=1]
[*]Deselect all third party sources in the software sources
[*]sudo apt-get purge cupsys
[*]sudo apt-get purge cups
[*]sudo apt-get purge xterm
[*]sudo apt-get purge libxine1-bin 
[*]sudo apt-get autoremove 
[*]sudo apt-get -f install
[/LIST]

Once this was done my dpkg was back in business.   I then re-installed cups, cupsys, and xterm.

Hope this helps.

---

