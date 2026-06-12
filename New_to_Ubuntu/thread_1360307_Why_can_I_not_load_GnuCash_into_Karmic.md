---
title: "Why can I not load GnuCash into Karmic?"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-12-20
I keep getting unresolved dependencies....what gives?

---

### Post by LuisGMarine on 2009-12-21
What are the exact errors that you are getting? 

Try running the following commands, and if any of them spit any errors make sure you post back exactly what went wrong.

```
sudo aptitude update
sudo aptitude install gnucash
```

---

### Post by dunbrokin on 2009-12-21
he following NEW packages will be installed:
  gnucash-common{a} gnucash-docs{a} guile-1.6{a} guile-1.6-libs{a} 
  guile-1.6-slib{a} libcrypt-ssleay-perl{a} libdate-manip-perl{a} 
  libfinance-quote-perl{a} libguile-ltdl-1{a} libgwenhywfar47{a} 
  libhtml-tableextract-perl{a} libktoblzcheck1c2a{a} libofx4{a} libosp5{a} 
  libqthreads-12{a} slib{a} 
0 packages upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.8MB of archives. After unpacking 56.5MB will be used.
The following packages have unmet dependencies:
  gnucash: Depends: libaqbanking20 which is a virtual package.
           Depends: libgoffice-0-6 (>= 0.6.6) but it is not installable
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gnucash [Not Installed]

Leave the following dependencies unresolved:
gnucash-common recommends gnucash (>= 2.2.9-1~getdeb1)
Score is -10081

Accept this solution? [Y/n/q/?]

---

### Post by LuisGMarine on 2009-12-21
I can't seem to find anything on that package.  I just installed it through the Ubuntu Software Manager.  Did you try that?

---

### Post by dunbrokin on 2009-12-21
> **LuisGMarine said:**
> I can't seem to find anything on that package.  I just installed it through the Ubuntu Software Manager.  Did you try that?

Yes, when did you install it?

gnucash:
 Depends: libaqbanking20  but it is not installable
 Depends: libgoffice-0-6 (>=0.6.6) but it is not installable

---

### Post by LuisGMarine on 2009-12-21
Just now.  I'm on Karmic 64-bit.  Maybe you did something to your sources.list?

---

### Post by LowSky on 2009-12-21
You can get the .deb's including all the requred ones from [HERE]("http://packages.ubuntu.com/karmic/gnucash")

---

### Post by LuisGMarine on 2009-12-21
I think it has something to do with your sources.  I just installed it on my computer again with aptitude and it installed what seems updated version of those packages that you are missing.  For example I downloaded libaqbanking29.

post the contents of /etc/sources.list

---

### Post by dunbrokin on 2009-12-21
> **LuisGMarine said:**
> 
post the contents of /etc/sources.list

Nothing in this file?!?!?

---

### Post by LuisGMarine on 2009-12-21
> **dunbrokin said:**
> Nothing in this file?!?!?

Sorry my mistake:

```
gedit /etc/apt/sources.list
```

Try that command and then post what you have in there.

---

### Post by dunbrokin on 2009-12-21
> **LowSky said:**
> You can get the .deb's including all the requred ones from [HERE]("http://packages.ubuntu.com/karmic/gnucash")

Does not work....errors were encountered

Error: Breaks exisiting package 'gnucash-common' conflict: gnucash (< 2.2.9-1~getdeb1)


error with /tmp/gnucash_2.2.9-0ubuntu4-i386.deb

---

### Post by dunbrokin on 2009-12-21
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic main restricted
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic-updates main restricted
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic universe
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic universe
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic-updates universe
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic multiverse
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic multiverse
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic-updates multiverse
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic-security main restricted
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic-security main restricted
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic-security universe
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic-security universe
deb [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic-security multiverse
deb-src [http://mirror.ihug.co.nz/ubuntu/](http://mirror.ihug.co.nz/ubuntu/) karmic-security multiverse
deb [http://packages.unknown-horizons.org/karmic](http://packages.unknown-horizons.org/karmic) weekly main # disabled on upgrade to karmic
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main # disabled on upgrade to karmic
deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) karmic main # disabled on upgrade to karmic
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) karmic main
# deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) karmic main
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.2)]/ karmic main restricted

---

### Post by LuisGMarine on 2009-12-21
wow your sources are jacked up.  I've never seen anything like it....

Are you sure you are running Karmic?  Or did you install jaunty and then dist-upgrade to karmic?

This might take me a while to figure out if it's safe to just post what a fresh install of karmic sources looks like .. or suppose to be,..

what is the output when you run this command?
```
lsb_release -a
```

---

### Post by dunbrokin on 2009-12-21
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic


Yeah upgraded from Jaunty...

---

### Post by Statik on 2009-12-21
The problem is that you are using the getdeb repository. That's not necessary. Temporarily disable it, reload your sources, then install the one in the official repositories. While getdeb is a great source, I use it, it isn't as well maintained as the official repositories. Usually thats not a problem. It looks like it is this time.

Good luck!

Statik

---

### Post by LuisGMarine on 2009-12-21
If that is the case then, just replace your current */etc/apt/sources.list* with the following text:

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://hr.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://hr.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://hr.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://hr.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://hr.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://hr.archive.ubuntu.com/ubuntu/ karmic universe
deb http://hr.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://hr.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://hr.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://hr.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://hr.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://hr.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://hr.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://hr.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse 
```

That is the no crap default /etc/apt/source.list.  After you replace your file with the text above, I would run an update

```
sudo aptitude update
```

```
sudo aptitude upgrade
```

Then after this is all fixed, try installing gnu cash, hopefully this time it will install.  I wish you the best, good luck and let us know if it works!

---

### Post by dunbrokin on 2009-12-21
> **Statik said:**
> The problem is that you are using the getdeb repository. That's not necessary. Temporarily disable it, reload your sources, then install the one in the official repositories. While getdeb is a great source, I use it, it isn't as well maintained as the official repositories. Usually thats not a problem. It looks like it is this time.

Good luck!

Statik

Thanks...how do I turn off getdeb?

---

### Post by dunbrokin on 2009-12-22
bump

---

### Post by Sathallrin on 2009-12-22
System->Administration->Software Sources
Go to the Other Software tab and uncheck the one for getdeb.net

---

### Post by dunbrokin on 2009-12-22
Maybe it is my eyes...but I cannot see a getdeb source shown in my sources list as shown above !!???

---

### Post by Sathallrin on 2009-12-22
maybe you don't have the getdeb source then.

Looks like you do have the getdeb version of gnucash installed (which is conflicting with the default common packages)

try doing:
sudo apt-get --purge remove gnucash

then do:
sudo apt-get install gnucash

---

### Post by dunbrokin on 2009-12-22
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnucash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libofx4 guile-1.6 libcrypt-ssleay-perl libosp5 libgwenhywfar47
  libaqbanking29-plugins libaqofxconnect5 libfinance-quote-perl libqbanking8
  libktoblzcheck1c2a libaqbanking29 guile-1.6-libs slib
  libaqbanking-plugins-libgwenhywfar47 libhtml-tableextract-perl
  libqthreads-12 libaqhbci16 libdate-manip-perl aqbanking-tools gnucash-docs
  libaqbanking29-plugins-qt libaqbanking-data guile-1.6-slib gnucash-common
  libguile-ltdl-1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by dunbrokin on 2009-12-22
sudo apt-get install gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnucash: Depends: libaqbanking20 but it is not installable
           Depends: libgoffice-0-6 (>= 0.6.6) but it is not installable
E: Broken packages

---

### Post by Sathallrin on 2009-12-22
Try running autoremove as it says, and then try installing again

sudo apt-get autoremove

---

### Post by dunbrokin on 2009-12-22
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  aqbanking-tools gnucash-common gnucash-docs guile-1.6 guile-1.6-libs
  guile-1.6-slib libaqbanking-data libaqbanking-plugins-libgwenhywfar47
  libaqbanking29 libaqbanking29-plugins libaqbanking29-plugins-qt libaqhbci16
  libaqofxconnect5 libcrypt-ssleay-perl libdate-manip-perl
  libfinance-quote-perl libguile-ltdl-1 libgwenhywfar47
  libhtml-tableextract-perl libktoblzcheck1c2a libofx4 libosp5 libqbanking8
  libqthreads-12 slib
0 upgraded, 0 newly installed, 25 to remove and 0 not upgraded.
After this operation, 71.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 270847 files and directories currently installed.)
Removing libaqbanking29-plugins-qt ...
Removing gnucash-common ...
Removing gnucash-docs ...
Removing guile-1.6-slib ...
Removing guile-1.6 ...
Removing guile-1.6-libs ...
Removing libqbanking8 ...
Removing libaqbanking-plugins-libgwenhywfar47 ...
Removing libfinance-quote-perl ...
Removing libcrypt-ssleay-perl ...
Removing libdate-manip-perl ...
Removing libguile-ltdl-1 ...
Removing libhtml-tableextract-perl ...
Removing libofx4 ...
Removing libosp5 ...
Removing libqthreads-12 ...
Removing slib ...
Ignoring install-info called from maintainer script
The package slib should be rebuild with new debhelper to get trigger support
Removing aqbanking-tools ...
Removing libaqbanking29-plugins ...
Removing libaqhbci16 ...
Removing libaqofxconnect5 ...
Removing libaqbanking29 ...
Removing libaqbanking-data ...
Removing libgwenhywfar47 ...
Removing libktoblzcheck1c2a ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for doc-base ...
Processing 1 removed doc-base file(s)...
Registering documents with scrollkeeper...

~$ sudo apt-get --purge remove gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnucash is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

~$ sudo apt-get install gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnucash: Depends: libaqbanking20 but it is not installable
           Depends: libgoffice-0-6 (>= 0.6.6) but it is not installable
E: Broken packages

---

### Post by Sathallrin on 2009-12-22
That is strange. I just checked my libgoffice and it is 0-8. So try this:

sudo apt-get install libgoffice-0-8

then install gnucash:
sudo apt-get install gnucash

---

### Post by dunbrokin on 2009-12-22
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgoffice-0-8 is already the newest version.
libgoffice-0-8 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by dunbrokin on 2009-12-22
sudo apt-get install gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnucash: Depends: libaqbanking20 but it is not installable
           Depends: libgoffice-0-6 (>= 0.6.6) but it is not installable
E: Broken packages

---

### Post by dunbrokin on 2009-12-23
bump

---

### Post by Sathallrin on 2009-12-23
In Synaptic Package Manager, when you search for gnucash. What does it say under Latest Version?

Mine shows 2.2.9-0ubuntu4
Is yours the same?

---

### Post by dunbrokin on 2009-12-23
2.2.9.1 - getdeb1

---

### Post by Sathallrin on 2009-12-23
That is very strange you have the getdeb version listed.

Try running this so I can see if is in your sources:

rgrep getdeb /etc/apt

---

### Post by Sathallrin on 2009-12-23
another thing that has a chance of working is if you run this:

sudo apt-get remove gnucash && sudo apt-get update && sudo apt-get install gnucash

---

### Post by dunbrokin on 2009-12-23
/etc/apt/sources.list.d/getdeb.list.distUpgrade:deb [http://getdeb.masio.com.mx/](http://getdeb.masio.com.mx/) jaunty/
/etc/apt/sources.list.d/getdeb.list:deb [http://getdeb.masio.com.mx/](http://getdeb.masio.com.mx/) jaunty/ # disabled on upgrade to karmic
/etc/apt/sources.list.d/getdeb.list.save:deb [http://getdeb.masio.com.mx/](http://getdeb.masio.com.mx/) jaunty/ # disabled on upgrade to karmic

---

### Post by dunbrokin on 2009-12-23
> **Sathallrin said:**
> another thing that has a chance of working is if you run this:

sudo apt-get remove gnucash && sudo apt-get update && sudo apt-get install gnucash

Nope...did not work....same message as before regarding broken packages.

---

### Post by dunbrokin on 2009-12-24
bump

---

### Post by Sathallrin on 2009-12-24
Ahh, your package output helps. Looks like you still have Jaunty sources for getdeb.
Do this to get rid of them

sudo rm /etc/apt/sources.list.d/getdeb.list
sudo rm /etc/apt/sources.list.d/getdeb.list.distUpgrade
sudo rm /etc/apt/sources.list.d/getdeb.list.save

Then do:
sudo apt-get update && sudo apt-get install gnucash

---

### Post by dunbrokin on 2009-12-24
Thank you for your time and patience, that worked a treat!!

Much obliged!

---

### Post by Sathallrin on 2009-12-28
Glad we figured it out and you got it working!

---

