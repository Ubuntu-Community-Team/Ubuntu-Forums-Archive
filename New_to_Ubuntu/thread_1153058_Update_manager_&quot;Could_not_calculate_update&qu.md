---
title: "Update manager &quot;Could not calculate update&quot; on partial update"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by TadeoDiaz on 2009-05-08
I am running Intrepid and for a few days it has been notifying me of new updates. When I run update manager it says that I have to run a partial update but when I try to run it hangs on "preparing to update" and I get a window that says:

Could not calculate upgrade
An unresolvable problem occurred while calculating upgrade
This can be caused by:
*Upgrading to a pre-release version of Ubuntu
*Running the current pre-release version of Ubuntu
*Unofficial software packages not provided by Ubuntu
This is most likely a transient problem, please try again later.

I've tried it for the past 4 days with the same result (The same issue is happening on my tower running Intrepid but I have not tried to run partial upgrade).

Does anyone know why it's happening or how to fix it? Thanks

---

### Post by taurus on 2009-05-08
Can you post your /etc/apt/sources.list?  Open a terminal and run this command.  Then, post the whole output here.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by nandemonai on 2009-05-08
Try marking all updates in synaptic and applying it there.

---

### Post by TadeoDiaz on 2009-05-08
Here is what I get in terminal after running ```
cat /etc/apt/sources.list
```

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
# deb http://ppa.launchpad.net/awn-testing/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/awn-testing/ubuntu intrepid main
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb http://ppa.launchpad.net/synce/ubuntu intrepid main
deb-src http://ppa.launchpad.net/synce/ubuntu intrepid main
```

---

### Post by TadeoDiaz on 2009-05-08
> **nandemonai said:**
> Try marking all updates in synaptic and applying it there.

When I tried reloading the package information I got this:

```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D
```

---

### Post by taurus on 2009-05-08
Make sure you close synaptic first.  Then, post the outputs of these two commands from a terminal.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

p.s.  Looks like you need ppa.launchpag.net key.

[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by TadeoDiaz on 2009-05-08
> **taurus said:**
> Make sure you close synaptic first.  Then, post the outputs of these two commands from a terminal.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

p.s.  Looks like you need ppa.launchpag.net key.

[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

For :sudo apt-get update: I get:

```
Get:1 http://ppa.launchpad.net intrepid Release.gpg [307B]
Ign http://ppa.launchpad.net intrepid/main Translation-en_US
Get:2 http://ppa.launchpad.net intrepid Release.gpg [307B]
Ign http://ppa.launchpad.net intrepid/main Translation-en_US         
Get:3 http://ppa.launchpad.net intrepid Release [65.9kB]             
Hit http://us.archive.ubuntu.com intrepid Release.gpg                
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US     
Hit http://security.ubuntu.com intrepid-security Release.gpg                   
Ign http://ppa.launchpad.net intrepid Release                                  
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US        
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Get:4 http://ppa.launchpad.net intrepid Release [46.7kB]             
Ign http://ppa.launchpad.net intrepid Release                                  
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US         
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-backports Release.gpg      
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com intrepid-security Release
Ign http://us.archive.ubuntu.com intrepid-backports/main Translation-en_US
Hit http://ppa.launchpad.net intrepid/main Packages                 
Ign http://us.archive.ubuntu.com intrepid-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-backports/multiverse Translation-en_US
Ign http://ppa.launchpad.net intrepid/main Packages                  
Hit http://us.archive.ubuntu.com intrepid Release                    
Ign http://ppa.launchpad.net intrepid/main Sources                             
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Hit http://us.archive.ubuntu.com intrepid-updates Release            
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://us.archive.ubuntu.com intrepid-backports Release          
Hit http://security.ubuntu.com intrepid-security/restricted Packages           
Hit http://security.ubuntu.com intrepid-security/main Sources        
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://us.archive.ubuntu.com intrepid/main Packages
Hit http://us.archive.ubuntu.com intrepid/restricted Packages
Hit http://us.archive.ubuntu.com intrepid/main Sources
Hit http://us.archive.ubuntu.com intrepid/restricted Sources
Hit http://us.archive.ubuntu.com intrepid/universe Packages
Hit http://ppa.launchpad.net intrepid/main Sources
Hit http://us.archive.ubuntu.com intrepid/universe Sources
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-backports/main Packages
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-backports/universe Packages
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Packages
Fetched 616B in 1s (482B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D
W: You may want to run apt-get update to correct these problems
```

For :sudo apt-get dist-upgrade: I get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  language-support-en language-support-translations-en
  openoffice.org-help-en-gb openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za thunderbird-locale-en-gb
The following packages will be upgraded:
  libmodplug0c2 libpango1.0-0 libpango1.0-common libpango1.0-dev
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-math openoffice.org-style-human
  openoffice.org-writer python-uno ttf-opensymbol uno-libs3 ure
21 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Need to get 71.5MB of archives.
After this operation, 25.1MB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  openoffice.org-emailmerge ure uno-libs3 openoffice.org-calc
  openoffice.org-impress openoffice.org-draw openoffice.org-math
  openoffice.org-writer openoffice.org-style-human openoffice.org-common
  openoffice.org-gtk openoffice.org-gnome python-uno ttf-opensymbol
  openoffice.org-base-core openoffice.org-core openoffice.org-java-common
Install these packages without verification [y/N]? y
Get:1 http://us.archive.ubuntu.com intrepid-updates/main libmodplug0c2 1:0.7-7ubuntu0.8.10.1 [121kB]
Get:2 http://ppa.launchpad.net intrepid/main openoffice.org-emailmerge 1:3.1.0~rc2-1ubuntu1~intrepid1 [6796B]
Get:3 http://ppa.launchpad.net intrepid/main ure 1.5.0+OOo3.1.0~rc2-1ubuntu1~intrepid1 [1384kB]
Get:4 http://us.archive.ubuntu.com intrepid-updates/main libpango1.0-dev 1.22.2-0ubuntu1.1 [362kB]
Get:5 http://us.archive.ubuntu.com intrepid-updates/main libpango1.0-common 1.22.2-0ubuntu1.1 [66.4kB]
Get:6 http://us.archive.ubuntu.com intrepid-updates/main libpango1.0-0 1.22.2-0ubuntu1.1 [293kB]
Get:7 http://ppa.launchpad.net intrepid/main uno-libs3 1.5.0+OOo3.1.0~rc2-1ubuntu1~intrepid1 [1093kB]
Get:8 http://ppa.launchpad.net intrepid/main openoffice.org-calc 1:3.1.0~rc2-1ubuntu1~intrepid1 [4383kB]
Get:9 http://ppa.launchpad.net intrepid/main openoffice.org-impress 1:3.1.0~rc2-1ubuntu1~intrepid1 [457kB]
Get:10 http://ppa.launchpad.net intrepid/main openoffice.org-draw 1:3.1.0~rc2-1ubuntu1~intrepid1 [2014kB]
Get:11 http://ppa.launchpad.net intrepid/main openoffice.org-math 1:3.1.0~rc2-1ubuntu1~intrepid1 [241kB]
Get:12 http://ppa.launchpad.net intrepid/main openoffice.org-writer 1:3.1.0~rc2-1ubuntu1~intrepid1 [5769kB]
Get:13 http://ppa.launchpad.net intrepid/main openoffice.org-style-human 1:3.1.0~rc2-1ubuntu1~intrepid1 [3810kB]
Get:14 http://ppa.launchpad.net intrepid/main openoffice.org-common 1:3.1.0~rc2-1ubuntu1~intrepid1 [17.1MB]
Get:15 http://ppa.launchpad.net intrepid/main openoffice.org-gtk 1:3.1.0~rc2-1ubuntu1~intrepid1 [177kB]
Get:16 http://ppa.launchpad.net intrepid/main openoffice.org-gnome 1:3.1.0~rc2-1ubuntu1~intrepid1 [3012B]
Get:17 http://ppa.launchpad.net intrepid/main python-uno 1:3.1.0~rc2-1ubuntu1~intrepid1 [92.8kB]
Get:18 http://ppa.launchpad.net intrepid/main ttf-opensymbol 1:3.1.0~rc2-1ubuntu1~intrepid1 [252kB]
Get:19 http://ppa.launchpad.net intrepid/main openoffice.org-base-core 1:3.1.0~rc2-1ubuntu1~intrepid1 [542kB]
Get:20 http://ppa.launchpad.net intrepid/main openoffice.org-core 1:3.1.0~rc2-1ubuntu1~intrepid1 [29.1MB]
Get:21 http://ppa.launchpad.net intrepid/main openoffice.org-java-common 1:3.1.0~rc2-1ubuntu1~intrepid1 [4291kB]
Fetched 71.5MB in 1min14s (964kB/s)                                            
(Reading database ... 151173 files and directories currently installed.)
Removing language-support-en ...
Removing language-support-translations-en ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]
Removing openoffice.org-help-en-gb ...
Removing openoffice.org-l10n-en-gb ...
Removing openoffice.org-l10n-en-za ...
Removing thunderbird-locale-en-gb ...
(Reading database ... 150413 files and directories currently installed.)
Preparing to replace openoffice.org-emailmerge 1:3.0.1-7ubuntu1~intrepid1 (using .../openoffice.org-emailmerge_1%3a3.1.0~rc2-1ubuntu1~intrepid1_all.deb) ...
Removing extension org.openoffice.legacy.mailmerge.py... done.
Unpacking replacement openoffice.org-emailmerge ...
Preparing to replace libmodplug0c2 1:0.7-7 (using .../libmodplug0c2_1%3a0.7-7ubuntu0.8.10.1_i386.deb) ...
Unpacking replacement libmodplug0c2 ...
Preparing to replace libpango1.0-dev 1.22.2-0ubuntu1 (using .../libpango1.0-dev_1.22.2-0ubuntu1.1_i386.deb) ...
Unpacking replacement libpango1.0-dev ...
Preparing to replace libpango1.0-common 1.22.2-0ubuntu1 (using .../libpango1.0-common_1.22.2-0ubuntu1.1_all.deb) ...
Cleaning up font configuration of pango...
Cleaning up category xfont..
Unpacking replacement libpango1.0-common ...
Preparing to replace libpango1.0-0 1.22.2-0ubuntu1 (using .../libpango1.0-0_1.22.2-0ubuntu1.1_i386.deb) ...
Unpacking replacement libpango1.0-0 ...
Preparing to replace ure 1.4.1+OOo3.0.1-7ubuntu1~intrepid1 (using .../ure_1.5.0+OOo3.1.0~rc2-1ubuntu1~intrepid1_i386.deb) ...
Unpacking replacement ure ...
Preparing to replace uno-libs3 1.4.1+OOo3.0.1-7ubuntu1~intrepid1 (using .../uno-libs3_1.5.0+OOo3.1.0~rc2-1ubuntu1~intrepid1_i386.deb) ...
Unpacking replacement uno-libs3 ...
Preparing to replace openoffice.org-calc 1:3.0.1-7ubuntu1~intrepid1 (using .../openoffice.org-calc_1%3a3.1.0~rc2-1ubuntu1~intrepid1_i386.deb) ...
Unpacking replacement openoffice.org-calc ...
Preparing to replace openoffice.org-impress 1:3.0.1-7ubuntu1~intrepid1 (using .../openoffice.org-impress_1%3a3.1.0~rc2-1ubuntu1~intrepid1_i386.deb) ...
Unpacking replacement openoffice.org-impress ...
Preparing to replace openoffice.org-draw 1:3.0.1-7ubuntu1~intrepid1 (using .../openoffice.org-draw_1%3a3.1.0~rc2-1ubuntu1~intrepid1_i386.deb) ...
Unpacking replacement openoffice.org-draw ...
Preparing to replace openoffice.org-math 1:3.0.1-7ubuntu1~intrepid1 (using .../openoffice.org-math_1%3a3.1.0~rc2-1ubuntu1~intrepid1_i386.deb) ...
Unpacking replacement openoffice.org-math ...
Preparing to replace openoffice.org-writer 1:3.0.1-7ubuntu1~intrepid1 (using .../openoffice.org-writer_1%3a3.1.0~rc2-1ubuntu1~intrepid1_i386.deb) ...
Unpacking replacement openoffice.org-writer ...
Preparing to replace openoffice.org-style-human 1:3.0.1-7ubuntu1~intrepid1 (using .../openoffice.org-style-human_1%3a3.1.0~rc2-1ubuntu1~intrepid1_all.deb) ...
Unpacking replacement openoffice.org-style-human ...
Preparing to replace openoffice.org-common 1:3.0.1-7ubuntu1~intrepid1 (using .../openoffice.org-common_1%3a3.1.0~rc2-1ubuntu1~intrepid1_all.deb) ...
Unpacking replacement openoffice.org-common ...
Preparing to replace openoffice.org-gtk 1:3.0.1-7ubuntu1~intrepid1 (using .../openoffice.org-gtk_1%3a3.1.0~rc2-1ubuntu1~intrepid1_i386.deb) ...
Unpacking replacement openoffice.org-gtk ...
Preparing to replace openoffice.org-gnome 1:3.0.1-7ubuntu1~intrepid1 (using .../openoffice.org-gnome_1%3a3.1.0~rc2-1ubuntu1~intrepid1_i386.deb) ...
Unpacking replacement openoffice.org-gnome ...
Preparing to replace python-uno 1:3.0.1-7ubuntu1~intrepid1 (using .../python-uno_1%3a3.1.0~rc2-1ubuntu1~intrepid1_i386.deb) ...
Unpacking replacement python-uno ...
Preparing to replace ttf-opensymbol 1:3.0.1-7ubuntu1~intrepid1 (using .../ttf-opensymbol_1%3a3.1.0~rc2-1ubuntu1~intrepid1_all.deb) ...
Unpacking replacement ttf-opensymbol ...
Preparing to replace openoffice.org-base-core 1:3.0.1-7ubuntu1~intrepid1 (using .../openoffice.org-base-core_1%3a3.1.0~rc2-1ubuntu1~intrepid1_i386.deb) ...
Unpacking replacement openoffice.org-base-core ...
Preparing to replace openoffice.org-core 1:3.0.1-7ubuntu1~intrepid1 (using .../openoffice.org-core_1%3a3.1.0~rc2-1ubuntu1~intrepid1_i386.deb) ...
Unpacking replacement openoffice.org-core ...
Preparing to replace openoffice.org-java-common 1:3.0.1-7ubuntu1~intrepid1 (using .../openoffice.org-java-common_1%3a3.1.0~rc2-1ubuntu1~intrepid1_all.deb) ...
Unpacking replacement openoffice.org-java-common ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up libmodplug0c2 (1:0.7-7ubuntu0.8.10.1) ...

Setting up libpango1.0-common (1.22.2-0ubuntu1.1) ...
Cleaning up font configuration of pango...
Cleaning up category xfont..
Updating font configuration of pango...
Cleaning up category xfont..
Updating category xfont..

Setting up libpango1.0-0 (1.22.2-0ubuntu1.1) ...

Setting up libpango1.0-dev (1.22.2-0ubuntu1.1) ...
Setting up uno-libs3 (1.5.0+OOo3.1.0~rc2-1ubuntu1~intrepid1) ...

Setting up ure (1.5.0+OOo3.1.0~rc2-1ubuntu1~intrepid1) ...
Setting up ttf-opensymbol (1:3.1.0~rc2-1ubuntu1~intrepid1) ...
Updating fontconfig cache...

Setting up openoffice.org-style-human (1:3.1.0~rc2-1ubuntu1~intrepid1) ...
Setting up openoffice.org-common (1:3.1.0~rc2-1ubuntu1~intrepid1) ...
Installing new version of config file /etc/openoffice/sofficerc ...

Setting up openoffice.org-core (1:3.1.0~rc2-1ubuntu1~intrepid1) ...
Setting up openoffice.org-base-core (1:3.1.0~rc2-1ubuntu1~intrepid1) ...

Setting up openoffice.org-calc (1:3.1.0~rc2-1ubuntu1~intrepid1) ...

Setting up openoffice.org-draw (1:3.1.0~rc2-1ubuntu1~intrepid1) ...

Setting up openoffice.org-impress (1:3.1.0~rc2-1ubuntu1~intrepid1) ...

Setting up openoffice.org-math (1:3.1.0~rc2-1ubuntu1~intrepid1) ...

Setting up openoffice.org-writer (1:3.1.0~rc2-1ubuntu1~intrepid1) ...

Setting up openoffice.org-gtk (1:3.1.0~rc2-1ubuntu1~intrepid1) ...

Setting up openoffice.org-gnome (1:3.1.0~rc2-1ubuntu1~intrepid1) ...

Setting up python-uno (1:3.1.0~rc2-1ubuntu1~intrepid1) ...

Setting up openoffice.org-java-common (1:3.1.0~rc2-1ubuntu1~intrepid1) ...

Setting up openoffice.org-emailmerge (1:3.1.0~rc2-1ubuntu1~intrepid1) ...
Adding extension /usr/lib/openoffice/basis3.1/program/mailmerge.py... done.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
```

It looks like that ran the update. Thanks taurus!!!! Oh and thanks for the ppa.launchpag.net key update thread, ill make sure i take care of that right now

---

