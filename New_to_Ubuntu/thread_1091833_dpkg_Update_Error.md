---
title: "dpkg Update Error"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Dr Mac 24 on 2009-03-09
Hi,

I downloaded outstanding updates and ran them. Installing the 1st one gave error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Running "dpkg --configure -a" in Terminal gave "dpkg: requested operation requires superuser privilege". I then ran "sudo dpkg --configure -a" as suggested by a previous posting which produced the following:

"Setting up libperl5.10 (5.10.0-11.1ubuntu2.2) ...

Processing triggers for man-db ...
Setting up libgnutls26 (2.4.1-1ubuntu0.2) ...

dpkg: dependency problems prevent configuration of ghostscript:
 ghostscript depends on libgs8 (= 8.63.dfsg.1-0ubuntu6.2); however:
  Version of libgs8 on system is 8.63.dfsg.1-0ubuntu6.
dpkg: error processing ghostscript (--configure):
 dependency problems - leaving unconfigured
Setting up perl-modules (5.10.0-11.1ubuntu2.2) ...
Setting up perl (5.10.0-11.1ubuntu2.2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/lib/libcups.so.2 is not a symbolic link

Errors were encountered while processing:
 ghostscript"

Does anyone have any suggestions how I can sort things? Note I have a x64 processor.

Cheers,

D

---

### Post by drs305 on 2009-03-09
I'm running 64-bit Intrepid and the latest version of libgs8 listed in my synaptic is 8.63.dfsg.1-0ubuntu6.2, which is the version being sought. If you haven't run updates lately, run the following to make sure you have the latest version for your installation:
```

sudo apt-get update
sudo apt-get upgrade

```

You can look in synaptic to see which version is installed, or run:
```

aptitude show libgs8

```

---

### Post by Dr Mac 24 on 2009-03-11
drs305,

Tried your suggestion but no luck. I think I interrupted the updating process resetting the computer 1/2 way through the process, hence problem I guess. Note also on restart of computer the following appears:


> "Boot from (hd0,1) ext3 e5e3895d-28b2-4f3c-bdfb-9821d7838cdb
> Starting up...
> [0.004000] Aperture beyond 4GB. Ignoring.
> [0.004000] Your BIOS doesn't leave a aperture memory hole
> [0.004000] Please enable the IOMMU option in the BIOS setup
> [0.004000] This costs you 64 MB of RAM
> [0.612112] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"

Trying your suggestion gave:

ddddd@ggggggg:~$ sudo apt-get update
........
Get: 13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages [74.8kB]
Get: 14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources [18.6kB]
Get: 15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages [10.9kB]
Get: 16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources [4118B]
Fetched 748kB in 6s (110kB/s)                                                  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ddddd@ggggggg:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
daniel@EnviroFriendly:~$ 

I'm stuck.:(

---

### Post by balaknair on 2009-03-11
Try this to get dpkg to go through each package, check for errors and correct any errors it finds. It may take a while to complete though.

*sudo dpkg-reconfigure -phigh -a*


Alternatively, try the following commands in a terminal

*sudo dpkg -l | grep -v ^ii*

This will list any packages not installed correctly.
Then remove the faulty package with

*sudo dpkg --purge remove _faulty package_*
or 
*sudo dpkg-reconfigure _faulty package_*


(Replace _faulty package_ with the name of the offending package you see in the output to the dpkg -l command.)

Hope this helps.
All the best.

---

### Post by philinux on 2009-03-11
```
sudo dpkg --configure -a
```

It just needs the sudo bit. In Jaunty the error message displays this correctly.

---

### Post by Dr Mac 24 on 2009-03-11
Tried this but no luck. Thanks D

---

### Post by balaknair on 2009-03-11
What was the result you got? Could you post the output of the commands here?

---

### Post by Dr Mac 24 on 2009-03-11
Hi,

I've tried all suggestions and still no success. I even reloaded Ubuntu 8.10. This ran OK the problem occurs on loading updates. Here are the results of the suggestions I've tried:

[B]aaaaa@bbbbb:~$ sudo apt-get update
[/B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg
.
.
Get: 10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources [4118B]
Fetched 575kB in 8s (65.3kB/s)                                              
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

**aaaaa@bbbbb:~$ dpkg --configure -a**
dpkg: requested operation requires superuser privilege

**aaaaa@bbbbb:~$ aptitude show libgs8**
Package: libgs8
State: unpacked
Automatically installed: no
Version: 8.63.dfsg.1-0ubuntu6.2
Priority: optional
Section: text
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 8167k
Depends: libc6 (>= 2.7), libcomerr2 (>= 1.01), libcups2 (>= 1.3.8),
         libcupsimage2 (>= 1.3.8), libfontconfig1 (>= 2.4.0), libgnutls26 (>=2.4.0-0), libjpeg62, libkrb53 (>= 1.6.dfsg.2), libpaper1, libpng12-0
         (>= 1.2.13-4), libstdc++6 (>= 4.1.1), libtiff4, zlib1g (>=1:1.1.4)
Description: The Ghostscript PostScript/PDF interpreter Library
 Ghostscript is used for PostScript/PDF preview and printing.  Usually as a back-end to a program such as ghostview, it can display PostScript and PDF documents in an X11 environment. 
 The Ghostscript home page is at [http://www.ghostscript.com/](http://www.ghostscript.com/) 
 This package provides the Ghostscript library which makes the facilities of Ghostscript available to applications.

**aaaaa@bbbbb:~$ sudo dpkg -l | grep -v ^ii **
[sudo] password for aaaaa: 
Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend 
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad) 
||/ Name                                       Version                               Description 
+++-==========================================-=====================================-============================================ 
iU  apparmor-utils 2.3+1289-0ubuntu4.1 Utilities for controlling AppArmor
iU  at-spi 1.24.0-0ubuntu3.8.10.1 Assistive Technology Service Provider Interf 

And so on.... about 50 of such files were listed, but none flagged with dggk 1-. Therefore none faulty I guess.

Note that the GRUB now lists an additional kernel for Uduntu so I have now have two something like:

Ubuntu OS kernel ?.?.11
Ubuntu OS kernel ?.?.11 recovery (these two appeared on running updates)
Ubuntu OS kernel ?.?.7
Ubuntu OS kernel ?.?.7 recovery(these two the original installed system) 
Windows XP

Running kernel ?.?.11 produced the original problem But choosing ?.?.7 Ububto boots OK, but the "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem" still occurs. Hope this clarifies.

Cheers,

D

---

### Post by balaknair on 2009-03-11
> **Dr Mac 24 said:**
> Hi,

I've tried all suggestions and still no success. I even reloaded Ubuntu 8.10. This ran OK the problem occurs on loading updates. Here are the results of the suggestions I've tried:

[B]aaaaa@bbbbb:~$ sudo apt-get update
[/B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg
.
.
Get: 10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources [4118B]
Fetched 575kB in 8s (65.3kB/s)                                              
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

**aaaaa@bbbbb:~$ dpkg --configure -a**
dpkg: requested operation requires superuser privilege

**aaaaa@bbbbb:~$ aptitude show libgs8**
Package: libgs8
State: unpacked
Automatically installed: no
Version: 8.63.dfsg.1-0ubuntu6.2
Priority: optional
Section: text
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 8167k
Depends: libc6 (>= 2.7), libcomerr2 (>= 1.01), libcups2 (>= 1.3.8),
         libcupsimage2 (>= 1.3.8), libfontconfig1 (>= 2.4.0), libgnutls26 (>=2.4.0-0), libjpeg62, libkrb53 (>= 1.6.dfsg.2), libpaper1, libpng12-0
         (>= 1.2.13-4), libstdc++6 (>= 4.1.1), libtiff4, zlib1g (>=1:1.1.4)
Description: The Ghostscript PostScript/PDF interpreter Library
 Ghostscript is used for PostScript/PDF preview and printing.  Usually as a back-end to a program such as ghostview, it can display PostScript and PDF documents in an X11 environment. 
 The Ghostscript home page is at [http://www.ghostscript.com/](http://www.ghostscript.com/) 
 This package provides the Ghostscript library which makes the facilities of Ghostscript available to applications.

**aaaaa@bbbbb:~$ sudo dpkg -l | grep -v ^ii **
[sudo] password for aaaaa: 
Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend 
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad) 
||/ Name                                       Version                               Description 
+++-==========================================-=====================================-============================================ 
iU  apparmor-utils 2.3+1289-0ubuntu4.1 Utilities for controlling AppArmor
iU  at-spi 1.24.0-0ubuntu3.8.10.1 Assistive Technology Service Provider Interf 

And so on.... about 50 of such files were listed, but none flagged with dggk 1-. Therefore none faulty I guess.

Note that the GRUB now lists an additional kernel for Uduntu so I have now have two something like:

Ubuntu OS kernel ?.?.11
Ubuntu OS kernel ?.?.11 recovery (these two appeared on running updates)
Ubuntu OS kernel ?.?.7
Ubuntu OS kernel ?.?.7 recovery(these two the original installed system) 
Windows XP

Running kernel ?.?.11 produced the original problem But choosing ?.?.7 Ububto boots OK, but the "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem" still occurs. Hope this clarifies.

Cheers,

D


OK, Dr Mac, I think I see where you're having trouble. 

> **aaaaa@bbbbb:~$ dpkg --configure -a**
dpkg: requested operation requires superuser privilege

make that
```
sudo dpkg --configure -a
```

Just copy paste the above line into a terminal and type in your password when prompted. The **sudo** before the rest of the command is important, without it you get the 
```
dpkg: requested operation requires superuser privilege
```

 > aaaaa@bbbbb:~$ sudo dpkg -l | grep -v ^ii
[sudo] password for aaaaa:
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-==========================================-=====================================-============================================
iU apparmor-utils 2.3+1289-0ubuntu4.1 Utilities for controlling AppArmor
iU at-spi 1.24.0-0ubuntu3.8.10.1 Assistive Technology Service Provider Interf

And so on.... about 50 of such files were listed, but none flagged with dggk 1-. Therefore none faulty I guess.

Nope. What that means is all the packages listed are faulty. The command ***sudo dpkg -l | grep -v ^ii*** lists are all packages that 'dpkg' finds to be improperly installed. So to do a step by step removal/repair you would have to enter  ***sudo dpkg-reconfigure _faulty package_*** for each package
eg:
```
sudo dpkg-reconfigure apparmor-utils
sudo dpkg-reconfigure at-spi
```

In this case it would be easier to just run
```
sudo dpkg-reconfigure -phigh -a
```



**_So here's what I think you should do_**

1) Try the simplest step first. Copy paste the command given below **exactly** as shown, including the sudo at the beginning of the line.
```
sudo dpkg --configure -a
```

2) If it doesn't work, and/or you still get the error after a reboot, proceed to the next command.
```
sudo dpkg-reconfigure -phigh -a
```

This step may take a while depending on the number of packages you have installed. What it does is stop each process, check for errors, reconfigure/repair, and restart it.

3) If even that doesn't work, you can consider manually deleting each faulty package one by one and reinstalling the broken packages
```
sudo dpkg --purge remove **xxxxx** && sudo apt-get install **xxxxx**
```

replace the **xxxxx** in the above command with the package name(like **apparmor-utils** or **at-spi** so that it would read 
*sudo dpkg --purge remove **at-spi** && sudo apt-get install **at-spi***)

---

### Post by Dr Mac 24 on 2009-03-13
Your suggestion has worked to a large extent. Thanks. The computer now boots OK and the majority of the updates have been installed, about 35. However the following have stubbornly remained after trying your various suggestions a number of times:

[I]aaaa@bbbb:~$ sudo dpkg -l | grep -v ^ii
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version                               Description
+++-==========================================-=====================================-============================================
pU  console-setup                              1.25ubuntu4                           Set up the font and the keyboard on the cons
pt  initramfs-tools                            0.92bubuntu16                         tools for generating an initramfs
iU  libapparmor-perl                           2.3+1289-0ubuntu4.1                   AppArmor library Perl bindings
rc  myspell-en-us                              1:2.4.0-2ubuntu4                      English_american dictionary for myspell
iU  openoffice.org-calc                        1:2.4.1-11ubuntu2.1                   OpenOffice.org office suite - spreadsheet
iU  openoffice.org-common                      1:2.4.1-11ubuntu2.1                   OpenOffice.org office suite architecture ind
iU  openoffice.org-core                        1:2.4.1-11ubuntu2.1                   OpenOffice.org office suite architecture dep
iU  openoffice.org-draw                        1:2.4.1-11ubuntu2.1                   OpenOffice.org office suite - drawing
iU  openoffice.org-emailmerge                  1:2.4.1-11ubuntu2.1                   E-Mail Mailmerge component for OpenOffice.or
iU  openoffice.org-gnome                       1:2.4.1-11ubuntu2.1                   GNOME Integration for OpenOffice.org (VFS, G
iU  openoffice.org-gtk                         1:2.4.1-11ubuntu2.1                   GTK+ Integration for OpenOffice.org (Widgets
iU  openoffice.org-impress                     1:2.4.1-11ubuntu2.1                   OpenOffice.org office suite - presentation
iU  openoffice.org-math                        1:2.4.1-11ubuntu2.1                   OpenOffice.org office suite - equation edito
iU  openoffice.org-writer                      1:2.4.1-11ubuntu2.1                   OpenOffice.org office suite - word processor
iU  python-uno                                 1:2.4.1-11ubuntu2.1                   Python interface for OpenOffice.org
aaaa@bbbb:~$ sudo dpkg --purge remove console-setup && sudo apt-get install console-setup
dpkg - warning: ignoring request to remove remove which isn't installed.
dpkg: dependency problems prevent removal of console-setup:
 ubuntu-minimal depends on console-setup.
 kbd depends on console-setup | console-common; however:
  Package console-setup is to be removed.
  Package console-common is not installed.
dpkg: error processing console-setup (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 console-setup
aaaa@bbbb:~$[/I]

Running ***sudo dpkg-recongfigure-phihl -a*** causes the screen to go blank before processing has finished. I leave it for a while before pressing reset. And using ***sudo dpkg --purge remove console-setup && sudo apt-get install console-setup***

gives:

[I]dpkg - warning: ignoring request to remove remove which isn't installed. 
dpkg: dependency problems prevent removal of console-setup: 
 ubuntu-minimal depends on console-setup. 
 kbd depends on console-setup | console-common; however: 
  Package console-setup is to be removed. 
  Package console-common is not installed. 
dpkg: error processing console-setup (--purge): 
 dependency problems - not removing 
Errors were encountered while processing: 
 console-setup[/I] 


I would welcome any further suggestions. 

Cheers,

D

---

### Post by balaknair on 2009-03-13
Hi
Glad to know your problem was at least partly solved.

Packages like console-setup are needed by a critical system components, so removing them might not be advisable.
Open Office and myspell on the other hand are more straightforward.

Just open Synaptic> Edit> Fix Broken Packages. In most cases, this will repair the damaged packages. If errors persist, run ***sudo dpkg-configure -a*** in a terminal again, followed by ***sudo apt-get -f install***(does the same thing as Synaptic> Edit> Fix Broken Packages)


Run ***sudo dpkg -l | grep -v ^ii*** to check if all packages have been fixed.
To fix console-setup and initramfs-tools, if the previous steps have not fixed them already, try this command 
***sudo dpkg-reconfigure-phigh console-setup***
***sudo dpkg-reconfigure-phigh initramfs-tools***

---

### Post by Dr Mac 24 on 2009-03-14
Hi balaknair,


Job done:) **Thanks very much** for your help.

Cheers,

D

---

### Post by balaknair on 2009-03-14
> **Dr Mac 24 said:**
> Hi balaknair,


Job done:) **Thanks very much** for your help.

Cheers,

D
Glad to hear that.

Have fun with Ubuntu.

---

