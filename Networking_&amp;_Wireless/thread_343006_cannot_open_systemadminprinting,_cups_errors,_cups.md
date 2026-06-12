---
title: "cannot open system/admin/printing, cups errors, cups server could not be contacted.."
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by dsimpson on 2007-01-20
I posted earlier and received no real help and only 1 reply, I am trying again in the hopes that someone out there has solved this problem. I checked all the posts and tried all the suggestions but none worked. 
   I tried uninstalling cups through synaptic and was unable to, it said that there were errors and they needed to be fixed first, but when I tried to fix, it said it was unable to fix. I keep getting the "cups server could not be contacted. I have made so many changes due to all the posts that I tried to follow that I don't even know where to begin, but if there is a way to fix the error without having to do a complete new install of Ubuntu, I really would want to go that route. 
   As I said, I cannot open System,Administration,Printing, and I have tried System/Administration/Services and cups is now disabled, I have reinstalled cups and nothing, I mean nothing has worked. My problems seemed to start when I was setting up my network to allow another printer to print from my local printer, I made changes in my /etc/cups/cupsd.conf and that was when the problems began. The only other change that I made was to disable ipv6 and I don't know it that could be the cause. I would be happy just being able to make my printer a local printer again, but cannot even do that, someone please help if you can.[-o<

---

### Post by Paerez on 2007-01-20
try running these commands:
```
sudo dpkg-reconfigure cupsys
sudo /etc/init.d/cupsys restart
```
Post any weird output you get, then try again.

---

### Post by dsimpson on 2007-01-20
Thank you, on the reconfigure try got this message output;

(/usr/sbin/dpkg-reconfigure: cupsys is broken or not fully installed)

did the cupsys restart and tried the reconfigure and still got the same message.

What was the likely scenario that I would hope to have come up with this attempt? I tried to install via synaptic to see if I could replace the missing or broken errors but I cannot install until the broken files are repaired, and I am unable to fix them through synaptic. Any other ideas?

---

### Post by Paerez on 2007-01-20
try:
```
sudo aptitude reinstall cupsys
```

---

### Post by dsimpson on 2007-01-20
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
cupsys is not currently installed, so it will not be reinstalled.
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Tried and this is what came up...Crazy, but I need to reinstall somehow. It says that in cannot be reinstalled because cupsys is currently not installed, have you any clue what that means when you aren't able to install from synaptic???

---

### Post by Paerez on 2007-01-21
ok:
```
sudo aptitude install cupsys
sudo dpkg-reconfigure cupsys
sudo /etc/init.d/cupsys restart
```

---

### Post by dsimpson on 2007-01-22
(sudo aptitude install cupsys)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for cupsys
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
(sudo dpkg reconfigure cupsys)

(sudo dpkg-reconfigure cupsys)
/usr/sbin/dpkg-reconfigure: cupsys is broken or not fully installed

(sudo /etc/init.d/cupsys restart)

After entering this last command it just went back to the command line, no message was initiated by this command. It seems that cupsys cannot repair itself. cannot reconfigure, cannot restart, and so far cannot be reinstalled. This has been the most perplexing and difficult problem I have had to date. The help though, is greatly appreciated, keep it coming, and if there is anyone out there that is an Ubuntu, Debian. or Linux whizkid or just an old hand at this, please feel free to jump right in..Thanks:!:

---

### Post by bapoumba on 2007-01-22
Hi,

```
~ $ aptitude show cupsys
Package: cupsys
State: installed
Automatically installed: no
Version: 1.2.4-2ubuntu3
Priority: optional
Section: net
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 6521k
Depends: libc6 (>= 2.4-1), libcupsimage2 (>= 1.2.1), libcupsys2 (>= 1.2.3),
         libdbus-1-3, libgnutls13 (>= 1.4.0-0), libldap2 (>= 2.1.17-1), libpam0g
         (>= 0.76), libpaper1, libslp1, zlib1g (>= 1:1.2.1), adduser (>= 3.12),
         debconf (>= 1.2.9) | debconf-2.0, patch, poppler-utils | xpdf-utils,
         perl-modules, procps, gs-esp, lsb-base (>= 3), cupsys-common, ssl-cert
         (>= 1.0.11), sysv-rc (>= 2.86.ds1-14.1ubuntu2)
Recommends: cupsys-client, smbclient (>= 3.0.9), foomatic-filters
Suggests: cupsys-bsd, cupsys-driver-gutenprint | cupsys-driver-gimpprint,
          foomatic-filters-ppds, xpdf-korean | xpdf-japanese |
          xpdf-chinese-traditional | xpdf-chinese-simplified, cups-pdf, hplip
Conflicts: cupsys-pstoraster (< 2)
Replaces: cupsys-pstoraster

```
It's in main repositories, even though some dependences are in universe. Can you paste again your sources.list ? (**cat /etc/apt/sources.list**).

One more thing, to enable admin access to cups web interface : **sudo adduser cupsys shadow** and then browse **localhost:631**, but before, you have to have it up and running ;)

---

### Post by dsimpson on 2007-01-22
Hi Bapoumba,
Here is the listing from my /etc/apt/sources.list

[COLOR="Red"]# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

## Major bug fix updates produced after the final release of the
## distribution.
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb http:archive/canonical.com/ubuntu dapper-commercial main
[/COLOR]

Is this what you were asking for? Did sudo adduser cupsys shadow, result were as follows;
[COLOR="Red"]Adding user `cupsys' to group `shadow'...
Done.[/COLOR]

As for browsing the localhost:631: how is this done? I tried to enter into terminal and got "command not found", tried entering into browser and nothing, you will have to instruct me more please, and about having it up and running, exactly how could I accomplish this? Is that what the code that will be entered into terminal, (the one you send) be used? Will that start and get it up running? 

I am waiting for further instructions before entering the code, so that I don't do something that I totally do not understand. :confused:

---

### Post by bapoumba on 2007-01-22
[http://cutlersoftware.com/ubuntuinstall/]("http://cutlersoftware.com/ubuntuinstall/")

To install packages, you'll have to edit your sources.list file and uncomment the repositories, ie remove the # at the beginning of the repositories lines. The ones to be deleted are in red, one to be added in blue :
```
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

## Major bug fix updates produced after the final release of the
## distribution.
[COLOR="Blue"]#[/COLOR] deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
[COLOR="Red"]#[/COLOR] deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
[COLOR="Red"]#[/COLOR] deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
[COLOR="Red"]#[/COLOR] deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[COLOR="Red"]#[/COLOR] deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
[COLOR="Red"]#[/COLOR] deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
[COLOR="Red"]#[/COLOR] deb http://security.ubuntu.com/ubuntu dapper-security main restricted
[COLOR="Red"]#[/COLOR] deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
[COLOR="Red"]#[/COLOR] deb http://security.ubuntu.com/ubuntu dapper-security universe
[COLOR="Red"]#[/COLOR] deb-src http://security.ubuntu.com/ubuntu dapper-security universe
[COLOR="Red"]#[/COLOR] deb http:archive/canonical.com/ubuntu dapper-commercial main
```

To edit the sources.list file, we'll use nano, a small text editor that works in a terminal :

1- open a terminal
2- **sudo nano -B /etc/apt/sources.list**
remove the red # and add the blue # at the exact same place I marked it.
3- save the file : CTRL+O (like in Ocean), and hit enter to save it with the same name
4- exit : CTRL+X

Then run **sudo apt-get update** or **sudo aptitude update** and paste the errors if there are any. You mays have to run **sudo apt-get dist-upgrade** or **sudo aptitude dist-upgrade** if they are many packages to upgrade and NO ERRORS to the update. Do not dist-upgrade if you notice errors, just paste them in here and wait someone as a look at it.

If all goes well, paste the output to **apt-cache show cupsys** or **aptitude show cupsys**. If cupsys in installed okay, as you did put cupsys in the shadow group (second command I gave you, Done means it's ... done ;)), open a web browser (you may be using Firefox) and type **localhost:631** in url. You should get cups web interface to administrate your printers :)

---

### Post by dsimpson on 2007-01-22
Hello, made the changes you suggested and at the end did

---

### Post by dsimpson on 2007-01-22
Hello, made the changes you suggested and at the end did aptitude show cupsys and tried the localhost:631 and it didn't work, sending the output for the show cupsys;

eaglesoldier@eaglesoldier:~$ aptitude show cupsys
No candidate version found for cupsys
Package: cupsys
State: not installed (configuration files remain)
Version: 1.2.2-0ubuntu0.6.06
Priority: optional
Section: net
Maintainer: Debian CUPS Maintainers <pkg-cups-devel@lists.alioth.debian.org>
Uncompressed Size: 10.4M
Depends: libc6 (>= 2.3.4-1), libcupsimage2 (>= 1.2.1), libcupsys2 (>= 1.2.1),
         libgnutls12 (>= 1.2.5), libldap2 (>= 2.1.17-1), libpam0g (>= 0.76),
         libpaper1, libslp1, zlib1g (>= 1:1.2.1), adduser (>= 3.12), debconf (>=         1.2.9) | debconf-2.0, patch, poppler-utils | xpdf-utils, perl-modules,
         procps, gs-esp, lsb-base (>= 3)
Recommends: cupsys-client, smbclient (>= 3.0.9), foomatic-filters
Suggests: cupsys-bsd, cupsys-driver-gutenprint | cupsys-driver-gimpprint,
          foomatic-filters-ppds, xpdf-korean | xpdf-japanese |
          xpdf-chinese-traditional | xpdf-chinese-simplified, cups-pdf, hplip
Conflicts: cupsys-pstoraster (< 2)
Replaces: cupsys-pstoraster
Description: Common UNIX Printing System(tm) - server
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and general
 replacement for lpd and the like.  It supports the Internet Printing Protocol
 (IPP), and has its own filtering driver model for handling various document
 types.

 This package provides the CUPS scheduler/daemon and related files.

 The terms "Common UNIX Printing System" and "CUPS" are trademarks of Easy
 Software Products ([www.easysw.com)](www.easysw.com)), and refer to the original source packages
 from which these packages are made.

State = not installed seems to be the only thing different from the 1st printout you sent me, it seems I am real close but still am missing something. What am I doing wrong? I am attaching the apt-cache show cupsys printout so that you can check that over also.

eaglesoldier@eaglesoldier:~$ apt-cache show cupsys
Package: cupsys
Status: deinstall ok config-files
Priority: optional
Section: net
Installed-Size: 10168
Maintainer: Debian CUPS Maintainers <pkg-cups-devel@lists.alioth.debian.org>
Architecture: i386
Version: 1.2.2-0ubuntu0.6.06
Config-Version: 1.2.2-0ubuntu0.6.06
Replaces: cupsys-pstoraster
Depends: libc6 (>= 2.3.4-1), libcupsimage2 (>= 1.2.1), libcupsys2 (>= 1.2.1), libgnutls12 (>= 1.2.5), libldap2 (>= 2.1.17-1), libpam0g (>= 0.76), libpaper1, libslp1, zlib1g (>= 1:1.2.1), adduser (>= 3.12), debconf (>= 1.2.9) | debconf-2.0, patch, poppler-utils | xpdf-utils, perl-modules, procps, gs-esp, lsb-base (>= 3)Recommends: cupsys-client, smbclient (>= 3.0.9), foomatic-filters
Suggests: cupsys-bsd, cupsys-driver-gutenprint | cupsys-driver-gimpprint, foomatic-filters-ppds, xpdf-korean | xpdf-japanese | xpdf-chinese-traditional | xpdf-chinese-simplified, cups-pdf, hplip
Conflicts: cupsys-pstoraster (<< 2)
Conffiles:
 /etc/default/cupsys 69cdfd521582ec36807b482439642f8d
 /etc/cups/cupsd.conf 3b67c0e1f04e4be6ab79ba7ac4c25d01
 /etc/cups/mime.convs 4a9ed8da95072f4b69e9219c1fa78afa
 /etc/cups/mime.types 7d24bc214f581f7b6c41b7ad4f8d7074
 /etc/init.d/cupsys c9b8d049aa3b4bb66df717373f004975
 /etc/pam.d/cupsys ff2488324854f7b1e892bb0df062d5f0
 /etc/logrotate.d/cupsys 282d47b0d8afc6f9459c5d68b25d3652
Description: Common UNIX Printing System(tm) - server
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and
 general replacement for lpd and the like.  It supports the Internet
 Printing Protocol (IPP), and has its own filtering driver model for
 handling various document types.
 .
 This package provides the CUPS scheduler/daemon and related files.
 .
 The terms "Common UNIX Printing System" and "CUPS" are trademarks of
 Easy Software Products ([www.easysw.com)](www.easysw.com)), and refer to the original
 source packages from which these packages are made.

---

### Post by Paerez on 2007-01-22
ok now do the:```
sudo aptitude install cupsys
```

---

### Post by dsimpson on 2007-01-22
Hi, did the "[COLOR="Blue"]sudo aptitude install cupsys[/COLOR]". Tried to enter cups via browser, got the message "Unable to Connect". Thought I would attach the printout from install command that was issued and you can see if something is still missing. One question though, before all this takes effect, is it necessary to reboot in order for all this to work, I have been rebooting after each try to see if that makes a difference but nothing has changed. Just was wondering what possible steps I might be missing. Here is the printout;
[COLOR="Blue"]eaglesoldier@eaglesoldier:~$ sudo aptitude install cupsys
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for cupsys
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done[/COLOR]


I was wondering if this line has any effect on this not working?

[COLOR="Red"]No candidate version found for cupsys[/COLOR]

---

### Post by bapoumba on 2007-01-23
Hello,

after editing your sources.list, you have to run **sudo aptitude update** for the new sources.list to be taken into account.

So :
```
sudo aptitude update
sudo aptitude install cupsys
```

---

### Post by dsimpson on 2007-01-23
Hi, tried all that you suggested and still no luck in opening browser to edit cups printer. Will I have to do sudo apt-get dist-upgrade or sudo aptitude dist-upgrade since I am unable to open cups in the browser? Everything seems to be as you said to make it but still just at the door, can't get in yet.

[COLOR="Blue"]# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

## Major bug fix updates produced after the final release of the
## distribution.
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.[/COLOR]

Here is what is in my sources.list now.

---

### Post by bapoumba on 2007-01-23
Hi dsimpson,
This is what your sources.list should look like :
> **dsimpson said:**
> 

#deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted

# updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

# base
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

# backports
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

#security
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

#commercial
deb [http://archive/canonical.com/ubuntu](http://archive/canonical.com/ubuntu) dapper-commercial main


I've edited it a bit, to add a couple repos that were missing and remove some comments.
You should have deleted only the # at the beginning of the lines, and not the whole lines ;)
These lines are the address where package managers go to fetch packages.

With this new sources.list, **sudo aptitude update** to have aptitude now where to look at, and then **aptitude show cupsys** for you to know what is the exact status of cupsys.

Please paste your modified sources.list and the output to these commands.

---

### Post by dsimpson on 2007-01-23
Hi bapoumba. I added what you sent and then went back and entered the lines of code that I had deleted and when I finished it says that I have duplicate sources.list entries in sucurity.ubuntu.com and it failed to resolve archive. I am attaching the output so you can check out what happened. If you need my /etc/apt/sources.list I can send that later.


Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [93.7kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Err [http://archive](http://archive) dapper-commercial Release.gpg
  Could not resolve 'archive'
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [93.7kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
99% [Waiting for headers] [Waiting for headers] [Connecting to archive] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://archive](http://archive) dapper-commercial Release.gpg
  Could not resolve 'archive'
Ign [http://archive](http://archive) dapper-commercial Release
Ign [http://archive](http://archive) dapper-commercial Release
Ign [http://archive](http://archive) dapper-commercial/main Packages
Ign [http://archive](http://archive) dapper-commercial/main Packages
Err [http://archive](http://archive) dapper-commercial/main Packages
  Could not resolve 'archive'
Err [http://archive](http://archive) dapper-commercial/main Packages
  Could not resolve 'archive'
Fetched 93.7kB in 3m23s (461B/s)
Failed to fetch http:archive/canonical.com/ubuntu/dists/dapper-commercial/Release.gpg  Could not resolve 'archive'
Failed to fetch [http://archive/canonical.com/ubuntu/dists/dapper-commercial/Release.gpg](http://archive/canonical.com/ubuntu/dists/dapper-commercial/Release.gpg)  Could not resolve 'archive'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch http:archive/canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz  Could not resolve 'archive'
Failed to fetch [http://archive/canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz](http://archive/canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz)  Could not resolve 'archive'
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
eaglesoldier@eaglesoldier:~$ aptitude show cupsys
Package: cupsys
State: not installed (configuration files remain)
Version: 1.2.2-0ubuntu0.6.06
Priority: optional
Section: net
Maintainer: Debian CUPS Maintainers <pkg-cups-devel@lists.alioth.debian.org>
Uncompressed Size: 10.4M
Depends: libc6 (>= 2.3.4-1), libcupsimage2 (>= 1.2.1), libcupsys2 (>= 1.2.1), libgnutls12 (>=
         1.2.5), libldap2 (>= 2.1.17-1), libpam0g (>= 0.76), libpaper1, libslp1, zlib1g (>=
         1:1.2.1), adduser (>= 3.12), debconf (>= 1.2.9) | debconf-2.0, patch, poppler-utils |
         xpdf-utils, perl-modules, procps, gs-esp, lsb-base (>= 3)
Recommends: cupsys-client, smbclient (>= 3.0.9), foomatic-filters
Suggests: cupsys-bsd, cupsys-driver-gutenprint | cupsys-driver-gimpprint,
          foomatic-filters-ppds, xpdf-korean | xpdf-japanese | xpdf-chinese-traditional |
          xpdf-chinese-simplified, cups-pdf, hplip
Conflicts: cupsys-pstoraster (< 2)
Replaces: cupsys-pstoraster
Description: Common UNIX Printing System(tm) - server
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and general replacement for lpd and the like.  It supports the Internet Printing Protocol (IPP), and has its own filtering driver model for handling various document types.

 This package provides the CUPS scheduler/daemon and related files.

 The terms "Common UNIX Printing System" and "CUPS" are trademarks of Easy Software Products
 ([www.easysw.com)](www.easysw.com)), and refer to the original source packages from which these packages are
 made.

---

### Post by bapoumba on 2007-01-23
Please **replace** your sources.list with this and **ONLY** this, nothing more, nothing less :

```
#deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted

# updates
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

# base
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

# backports
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

#security
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

#commercial
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

Duplicate repository lines in this file leads to errors (copying my lines + your former ones got some repo lines to appear twice). One error was my fault, there was a typo in the commercial repo. I've corrected it above. Sorry.

```
sudo aptitude update
sudo aptitude install cupsys
```

You'll get it installed, eventually ;)

---

### Post by dsimpson on 2007-01-23
Hi, getting closer, but still having errors. What is a child exited with status 1 error, and error exit status 2? Those seem to be the only hangup now. Here is the install with the errors noted. The update went well all reported done! The errors all popped up during install.

eaglesoldier@eaglesoldier:~$ sudo aptitude install cupsys
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  dbus dbus-1-utils flashplugin-nonfree language-pack-en language-pack-gnome-en
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-glib1 libavahi-qt3-1 libc6
  libc6-dev libc6-i686 libdbus-1-2 libdbus-glib-1-2 libgtop2-7 libkrb53 libpoppler1
  libpoppler1-glib libsoup2.2-8 locales openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-l10n-en-us openoffice.org-math
  openoffice.org-writer opera poppler-utils python-uno python2.4-dbus ttf-opensymbol
  xserver-xorg-core
0 packages upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up cupsys (1.2.2-0ubuntu0.6.06) ...
 [COLOR="Red"]* Starting Common Unix Printing System: cupsd cupsd: Child exited with status 1![/COLOR]
invoke-rc.d: initscript cupsys, action "start" failed.
[COLOR="Red"]dpkg: error processing cupsys (--configure):[/COLOR]
 [COLOR="Red"]subprocess post-installation script returned error exit status 2[/COLOR]
Errors were encountered while processing:
 cupsys
[COLOR="Red"]E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
A package failed to install.  Trying to recover:
Setting up cupsys (1.2.2-0ubuntu0.6.06) ...
 [COLOR="Red"]* Starting Common Unix Printing System: cupsd cupsd: Child exited with status 1![/COLOR]
invoke-rc.d: initscript cupsys, action "start" failed.
[COLOR="Red"]dpkg: error processing cupsys (--configure):[/COLOR]
 [COLOR="Red"]subprocess post-installation script returned error exit status 2[/COLOR]
Errors were encountered while processing:
 cupsys

---

### Post by bapoumba on 2007-01-24
Have a look at **/var/log/cups/error_log**, or attach it to a post, this is the file where cups errors are logged.
One possible way out of this is to purge cupsys package and reinstall it. But first, the log file ;)

---

### Post by dsimpson on 2007-01-24
Here it goes. 

not found!
E [10/Jan/2007:01:57:02 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:02 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:02 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:05 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:05 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:05 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:08 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:08 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:08 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:10 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:10 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:14 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:14 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:14 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:15 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:15 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:17 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:20 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:20 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:20 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:20 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:01:57:20 -0800] CUPS-Add-Modify-Printer: Unauthorized
E [10/Jan/2007:01:57:20 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:20 -0800] PID 534 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:21 -0800] PID 624 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] PID 626 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] PID 637 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] PID 639 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:21 -0800] PID 625 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] PID 640 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] PID 642 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:21 -0800] PID 638 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:21 -0800] PID 641 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] PID 643 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] PID 645 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:22 -0800] PID 644 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:22 -0800] PID 646 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] PID 647 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] PID 648 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] PID 649 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:22 -0800] PID 651 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] PID 650 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:22 -0800] PID 653 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] PID 656 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:22 -0800] PID 655 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:24 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:24 -0800] PID 659 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:24 -0800] PID 658 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:24 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:25 -0800] PID 670 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 672 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 671 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 674 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 675 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 676 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:25 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:25 -0800] PID 677 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 678 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 679 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:25 -0800] PID 680 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 682 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:25 -0800] PID 681 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:26 -0800] PID 683 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] PID 685 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] PID 692 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] PID 694 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:26 -0800] PID 684 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] PID 693 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] [Job 112] No %%BoundingBox: comment in header!
E [10/Jan/2007:01:57:26 -0800] PID 695 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] PID 696 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2007:01:57:26 -0800] PID 697 (/usr/lib/cups/backend/ipp) crashed on signal 9!
E [10/Jan/2007:01:57:38 -0800] [Job 113] No %%BoundingBox: comment in header!
E [10/Jan/2007:02:01:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:01:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:01:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:01:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:02:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:03:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:04:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:05:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:36 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:41 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:46 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:51 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:06:56 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:01 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:11 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:16 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:21 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:26 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:31 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:37 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:37 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:42 -0800] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2007:02:07:42 -0800] cupsdAuthorize: Local authentication certificate not found!
E [15/Jan/2007:20:19:22 -0800] Creating missing directory "/var/run/cups/certs"
E [15/Jan/2007:22:39:29 -0800] Creating missing directory "/var/run/cups/certs"
E [15/Jan/2007:23:06:43 -0800] Creating missing directory "/var/run/cups/certs"
E [17/Jan/2007:20:59:48 -0800] Creating missing directory "/var/run/cups/certs"
E [17/Jan/2007:21:38:37 -0800] Creating missing directory "/var/run/cups/certs"
E [17/Jan/2007:21:51:43 -0800] Creating missing directory "/var/run/cups/certs"
E [18/Jan/2007:11:51:19 -0800] Creating missing directory "/var/run/cups/certs"
E [18/Jan/2007:20:58:17 -0800] Creating missing directory "/var/run/cups/certs"
E [18/Jan/2007:23:18:33 -0800] Creating missing directory "/var/run/cups/certs"
E [18/Jan/2007:23:58:22 -0800] Unknown Location directive ... on line 34.
E [19/Jan/2007:00:21:38 -0800] Unknown Location directive ... on line 34.
E [19/Jan/2007:01:05:13 -0800] Unknown Location directive ... on line 36.
E [19/Jan/2007:01:05:18 -0800] Unknown Location directive ... on line 36.
E [19/Jan/2007:11:29:32 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:01:48:17 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:02:05:08 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:02:05:56 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:02:07:28 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:02:49:40 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:03:01:32 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:03:17:37 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:03:41:25 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:03:49:01 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:04:13:40 -0800] Unknown directive Only on line 15.
E [20/Jan/2007:04:13:40 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:04:15:34 -0800] Unknown directive Only on line 15.
E [20/Jan/2007:04:15:34 -0800] Unknown Location directive ... on line 36.
E [20/Jan/2007:14:12:45 -0800] Unknown directive Only on line 15.
E [20/Jan/2007:14:12:45 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:16:36:22 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:16:36:22 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:16:36:26 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:16:36:26 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:16:00 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:16:00 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:16:03 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:16:03 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:20:46 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:20:46 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:20:50 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:20:50 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:34:54 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:34:54 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:34:58 -0800] Unknown directive Only on line 15.
E [23/Jan/2007:17:34:58 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:42:01 -0800] Unknown Location directive ... on line 36.
E [23/Jan/2007:17:42:05 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:00:35:33 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:05:39 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:06:33 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:06:37 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:07:58 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:08:02 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:08:57 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:26:39 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:01:28:09 -0800] Unknown Location directive ... on line 36.
E [24/Jan/2007:02:14:07 -0800] Unknown Location directive </Location on line 36.E [24/Jan/2007:02:18:22 -0800] Unknown Location directive </Location on line 36.E [24/Jan/2007:02:18:28 -0800] Unknown Location directive </Location on line 36.E [24/Jan/2007:02:19:16 -0800] Unknown Location directive </Location on line 36.E [24/Jan/2007:02:27:04 -0800] Unknown Location directive </Location on line 37.E [24/Jan/2007:02:41:54 -0800] Unknown Location directive </Location on line 37.eaglesoldier@eaglesoldier:~$

:confused:

---

### Post by dsimpson on 2007-01-24
went in and copied my cupsys.conf for you to look at to see if you can identify where the problem lies, it seems that line 36 (blank line) and line 37 (location) are at least 2 of the problem areas. Do you have a generic file that you can compare this to to see what needs to be changed? It has been altered so much that the backup is worthless now, it isn't the original.


#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
Listen 192.168.2.3:631
# Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
Browsing Off
#BrowseOrder allow,deny
#BrowseAllow @LOCAL
#BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
Order allow,deny
Allow localhost
                                                _[COLOR="Red"]This Line[/COLOR]_
</Location /admin>                   _[COLOR="Red"]This Line[/COLOR]_

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
#<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
#Deny From All  
Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

# Include files in /etc/cups/conf.d
Include /etc/cups/cups.d/ports.conf
#Include /etc/cups/cups.d/browse.conf

#
#


Hope this might be helpful!:)

---

### Post by dsimpson on 2007-01-25
Thank you bapoumba, with your input, and the last advice I finally got it running. I really appreciate your patience, you're the man!!!! It is helpful people like you that make Ubuntu work. Thanks again!

---

### Post by bapoumba on 2007-01-26
Hey dsimpson, congratulations :)
Sorry, I have not been much around lately. I saw your previous post, but had no time to dig into it. And I am not the man ;)

---

