---
title: "Copied over /usr/bin/perl"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by sheldon1 on 2010-07-28
Hey hey hey,

Long story short, I just accidentally copied a perl script to 

/usr/bin/perl  

using the command 

'sudo cp name-of-script /usr/bin/perl'


Meaning that I deleted the original contents of that file (bad news). I'm not sure what was there to begin with, but none of my perl scripts are working anymore.

I don't think that there's a way to undo the operation. My next thought is to download a copy of whatever was in /usr/bin/perl and copy it into that directory, then check to see if the perl scripts I'm using start working again.

Does anybody know where I can find the contents of /usr/bin/perl or do you have any other ideas?

If not, this will be the third Linux installation I've fubar'd by messing around (unwittingly) with files related to programming languages . . . *slaps forehead* . . . 

Thankfully, there isn't anything important on this computer, so I could just do a fresh install if push comes to shove. 

Thanks in advance.

-sheldon

---

### Post by cariboo on 2010-07-28
You should be able to re-install perl via synaptic. Why are you putting perl scripts in /usr/bin, all user created scripts should go in /usr/local/bin.

---

### Post by t0p on 2010-07-28
Ouch!  What you unwittingly deleted was your computer's perl binary - so now your computer has no perl anymore.

First of all, get that script you copied to /usr/bin/perl and move it to somewhere safe (eg your Desktop):

```
sudo mv /usr/bin/perl ~/Desktop/some-script-or-other
```

Now reinstall perl with apt-get:

```
sudo apt-get install perl
```

---

### Post by AlphaLexman on 2010-07-28
> **cariboo907 said:**
> all user created scripts should go in /usr/local/bin.
Some users even prefer a '~/bin' or '~/scripts' added to the $PATH variable.

---

### Post by sheldon1 on 2010-07-28
> **cariboo907 said:**
> You should be able to re-install perl via synaptic. Why are you putting perl scripts in /usr/bin, all user created scripts should go in /usr/local/bin.

I tried to remove the perl package using synaptic, and then re-install. My computer freezes about 10% of the way into the uninstall.

Using apt-get install perl gives me errors. First, it asks me to run 

sudo dpkg --configure -a

Since my computer shut down while adding/removing software. When I do, it returns


/usr/share/debconf/frontend: 5: use: not found
/usr/share/debconf/frontend: 6: use: not found
/usr/share/debconf/frontend: 7: use: not found
/usr/share/debconf/frontend: 8: Syntax error: "(" unexpected
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up g++ (4:4.4.3-1ubuntu1) ...
/usr/sbin/dpkg-divert: 18: BEGIN: not found
/usr/sbin/dpkg-divert: 19: {PERL_DL_NONLAZY}: not found
/usr/sbin/dpkg-divert: 20: Syntax error: "}" unexpected
/usr/sbin/dpkg-divert: 18: BEGIN: not found
/usr/sbin/dpkg-divert: 19: {PERL_DL_NONLAZY}: not found
/usr/sbin/dpkg-divert: 20: Syntax error: "}" unexpected
/usr/sbin/update-alternatives: 18: BEGIN: not found
/usr/sbin/update-alternatives: 19: {PERL_DL_NONLAZY}: not found
/usr/sbin/update-alternatives: 20: Syntax error: "}" unexpected
dpkg: error processing g++ (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 man-db
 g++

I installed g++ earlier today, before this happened, but getting this message anyway. My guess is that perl is needed in order to run any kind of installation correctly.

Regardless, I try 

sudo apt-get install perl

and get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
perl is already the newest version.
The following packages were automatically installed and are no longer required:
  libtwolame0 gstreamer0.10-plugins-ugly librsvg2-2.18-cil libgdata1.4-cil
  kdemultimedia-kio-plugins libkcddb4 libqtscript4-core libtaglib2.0-cil
  libqtscript4-gui libqtscript4-uitools libwnck2.20-cil libqtscript4-sql
  libsidplay1 libqtscript4-xml libmad0 libtag-extras1 libopencore-amrnb0
  liblastfm0 libqtscript4-network libopencore-amrwb0 libmpeg2-4
  libnotify0.4-cil libgnomedesktop2.20-cil liba52-0.7.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
/usr/sbin/dpkg-preconfigure: 6: BEGIN: not found
eval: 1: qq{: not found
/usr/sbin/dpkg-preconfigure: 8: use: not found
/usr/sbin/dpkg-preconfigure: 9: use: not found
/usr/sbin/dpkg-preconfigure: 10: Syntax error: "(" unexpected
Setting up man-db (2.5.7-2) ...
/usr/share/debconf/frontend: 5: use: not found
/usr/share/debconf/frontend: 6: use: not found
/usr/share/debconf/frontend: 7: use: not found
/usr/share/debconf/frontend: 8: Syntax error: "(" unexpected
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up g++ (4:4.4.3-1ubuntu1) ...
/usr/sbin/dpkg-divert: 18: BEGIN: not found
/usr/sbin/dpkg-divert: 19: {PERL_DL_NONLAZY}: not found
/usr/sbin/dpkg-divert: 20: Syntax error: "}" unexpected
/usr/sbin/dpkg-divert: 18: BEGIN: not found
/usr/sbin/dpkg-divert: 19: {PERL_DL_NONLAZY}: not found
/usr/sbin/dpkg-divert: 20: Syntax error: "}" unexpected
/usr/sbin/update-alternatives: 18: BEGIN: not found
/usr/sbin/update-alternatives: 19: {PERL_DL_NONLAZY}: not found
/usr/sbin/update-alternatives: 20: Syntax error: "}" unexpected
dpkg: error processing g++ (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up cups-bsd (1.4.3-1ubuntu1.2) ...
/usr/share/debconf/frontend: 5: use: not found
/usr/share/debconf/frontend: 6: use: not found
/usr/share/debconf/frontend: 7: use: not found
/usr/share/debconf/frontend: 8: Syntax error: "(" unexpected
dpkg: error processing cups-bsd (--configure):
 subprocess installed post-installation script returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)


At this point, I'm a bit hesitant to run

apt-get autoremove perl

Because that's how I destroyed my last Linux install on this machine ;)

To me, the error messages are clearly telling me that perl is needed to add/remove software, but that perl isn't working correctly.

Any ideas?

---

### Post by sheldon1 on 2010-07-28
> **AlphaLexman said:**
> Some users even prefer a '~/bin' or '~/scripts' added to the $PATH variable.


Believe me, I'll be sure to put them in the right places next time. I've never dealt with perl scripts before, and the instructions on the site I got the script from (something to help me delete files from my ipod shuffle) just said "put it somewhere" (great advice, dude) so I just put it in the directory referenced at the top of the code, which, now I can see is obviously /usr/bin/perl

[http://userweb.cs.utexas.edu/users/walter/geek/ipodshuffle-linux.html](http://userweb.cs.utexas.edu/users/walter/geek/ipodshuffle-linux.html)

*slaps forehead again*

Thanks for the help!

-sheldon

---

### Post by sisco311 on 2010-07-28
EDIT: d'oh, gmargo is right, /usr/bin/perl is provided by perl-base and not perl.

---

### Post by gmargo on 2010-07-28
Probably the scripts involved are trying to use perl!  Here's how to recover the perl binary:


[LIST=1]
[*]Use browser to navigate to [http://packages.ubuntu.com/lucid/perl-base](http://packages.ubuntu.com/lucid/perl-base)
[*]Scroll down to the "Download perl-base" section and download .deb file appropriate to architecture (i386 in my case).
[*] On the command line, navigate to whereever you saved the "perl-base_5.10.1-8ubuntu2_ARCH.deb" file.
[*] Extract the contents of the .deb file into the current directory: "dpkg-deb -x perl-base_5.10.1-8ubuntu2_i386.deb"
[*] Copy extracted binary: "sudo cp -p ./usr/bin/perl /usr/bin/perl"
[/LIST]

---

### Post by sheldon1 on 2010-07-28
> **gmargo said:**
> Probably the scripts involved are trying to use perl!  Here's how to recover the perl binary:


[LIST=1]
[*]Use browser to navigate to [http://packages.ubuntu.com/lucid/perl-base](http://packages.ubuntu.com/lucid/perl-base)
[*]Scroll down to the "Download perl-base" section and download .deb file appropriate to architecture (i386 in my case).
[*] On the command line, navigate to whereever you saved the "perl-base_5.10.1-8ubuntu2_ARCH.deb" file.
[*] Extract the contents of the .deb file into the current directory: "dpkg-deb -x perl-base_5.10.1-8ubuntu2_i386.deb"
[*] Copy extracted binary: "sudo cp -p ./usr/bin/perl /usr/bin/perl"
[/LIST]

Good thinking. That was my first thought when it happened, I just didn't know where to find the file. 

When I downloaded the .deb, it gave me the option to re-install perl. So, I re-installed and now everything is working. I'm surprised that this re-install script didn't need perl. Strange, but convenient.

THANKS ALL!!! WE ARE VICTORIOUS ONCE AGAIN

---

