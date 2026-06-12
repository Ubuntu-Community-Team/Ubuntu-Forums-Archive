---
title: "Error while trying to install proprietary ATI drivers for old graphics card"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by josephpford on 2009-11-15
I went to the ATI download site and downloaded the proprietary driver for my ATI Mobility FireGL T2 graphics card in my IBM R50P laptop.

After downloading, I moved it to a new directory and set it to executable and then executed it.  Here is the output:

[INDENT]==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-14-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.FEruLw[/INDENT]

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I then tried executing the command with the flag '--iscurrentdistro' and '-iscurrentdistro' but only got the standard "help" message:

[INDENT]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
jford@jford-laptop:~/ati$ ./ati-driver-installer-9-3-x86.x86_64.run -iscurrentdistro
Unrecognized flag : -iscurrentdistro
Makeself version 2.1.3 
 1) Getting help or info about ./ati-driver-installer-9-3-x86.x86_64.run :
  ./ati-driver-installer-9-3-x86.x86_64.run -h|--help                     Print this message
  ./ati-driver-installer-9-3-x86.x86_64.run -i|--info                     Print embedded info : title, default target directory, embedded script 
  ./ati-driver-installer-9-3-x86.x86_64.run -l|--list                     Print the list of files in the archive
  ./ati-driver-installer-9-3-x86.x86_64.run -c|--check                    Checks integrity of the archive
  ./ati-driver-installer-9-3-x86.x86_64.run --extract NewDirectory        Extract this package to NewDirectory only
 
 2) Running ./ati-driver-installer-9-3-x86.x86_64.run :
  ./ati-driver-installer-9-3-x86.x86_64.run [options] [additional arguments to embedded script] with following options (in that order)
  --keep                              Do not erase target directory after running the embedded script
  Following arguments will be passed to the embedded script:
  --install                           Install the driver(default)
  --listpkg                           List all the generatable packages 
  --buildpkg package                  Build "package" if generatable ("package" as returned by --listpkg)
  --buildandinstallpkg package        Build and Install "package" as returned by --listpkg

jford@jford-laptop:~/ati$ 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/INDENT]

Anybody have any ideas on how I can get this to install?  The graphics in Windows are great (can watch Hulu.com, play a decent amount of video games, etc), but in Linux, it's horrible.  I can barely play video on hulu.com, can barely play any video games, etc.

---

### Post by josephpford on 2009-11-15
I found this site and will give it a try:

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

---

### Post by josephpford on 2009-11-15
Warning!

Do not use the above website to install ati drivers!!!  It hosed my system!

---

### Post by Mark Phelps on 2009-11-15
Unless your ATI card is one of the latest HD 3x/4x/5x or Mobility Radeon cards, there are NO ATI drives you can install that will work with your card and Ubuntu newer than 8.10.

Trying to force driver installation will only, as you have discovered, hose up your system big time.

The link below has instructions for removing the ATI drivers and replacing them with the open source drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

