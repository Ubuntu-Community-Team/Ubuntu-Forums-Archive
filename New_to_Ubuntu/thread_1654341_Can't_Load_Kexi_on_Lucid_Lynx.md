---
title: "Can't Load Kexi on Lucid Lynx"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by candra on 2010-12-28
Greetings,

I am using - Ubuntu 10.04 LTS - the Lucid Lynx - released in April 2010.

I recently tried to install the KEXI database but it is NOT "showing up" anywhere on my computer. 

This below thread (short) contains all the details:

[http://ubuntuforums.org/showthread.php?t=1645452](http://ubuntuforums.org/showthread.php?t=1645452)

If anyone has any further insight, it'd be greatly appreciated. 

Candra

---

### Post by davidmohammed on 2010-12-28
any errors if you run 

kexi

in a terminal session?

---

### Post by candra on 2010-12-28
Here is what happens when typing Kexi in terminal window:

candra@candra-desktop:~$ kexi
No command 'kexi' found, did you mean:
 Command 'lexi' from package 'tendra' (universe)
kexi: command not found
candra@candra-desktop:~$

Yet as noted in my earlier thread, the Symantec Package Manager acts as though KEXI is loaded on my computer. Apparently loading Kexi on Lucid Lynx has be "tricky" and this problem of not showing up has happened before. But as noted, I have already tried all solutions given by others...

Any other suggestions you have are welcome.

---

### Post by Elfy on 2010-12-28
Have you tried to create a new dbase?

```
kexi --createdb test
```

I have also closed your other thread. Please do not post duplicate threads.

---

### Post by davidmohammed on 2010-12-28
umm - the ppa referred to only has maverick and natty packages.

suggest use the kubuntu backport repository and install from there

i.e.

add this to software sources: ppa:kubuntu-ppa/backports

then

sudo apt-get install kexi

---

### Post by candra on 2010-12-28
> **davidmohammed said:**
> umm - the ppa referred to only has maverick and natty packages.

suggest use the kubuntu backport repository and install from there

i.e.

add this to software sources: ppa:kubuntu-ppa/backports

then

sudo apt-get install kexi


I added the repository as suggested and then executed the install command in the terminal window. Here is what happened:


```
candra@candra-desktop:~$ sudo apt-get install kexi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kexi
```

---

### Post by davidmohammed on 2010-12-28
... now getting confused - 

if you look [here]("http://packages.ubuntu.com/lucid-backports/kexi") - kexi is clearly packaged.

can you run

sudo apt-get update && sudo apt-get upgrade

to check if there are any issues with your package management.

---

### Post by candra on 2010-12-28
> **davidmohammed said:**
> ... now getting confused - 

if you look [here]("http://packages.ubuntu.com/lucid-backports/kexi") - kexi is clearly packaged.

can you run

sudo apt-get update && sudo apt-get upgrade

to check if there are any issues with your package management.

Here below is the output when I ran what you suggested:

```
:~$ sudo apt-get update && sudo apt-get upgrade
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                     
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://archive.canonical.com/ lucid/partner Translation-en_US              
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Hit http://us.archive.ubuntu.com lucid Release                                 
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu/ lucid/main Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://archive.canonical.com lucid Release                                 
Hit http://us.archive.ubuntu.com lucid-updates Release                         
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Hit http://us.archive.ubuntu.com lucid/restricted Packages           
Hit http://us.archive.ubuntu.com lucid/main Sources                  
Hit http://us.archive.ubuntu.com lucid/restricted Sources                      
Hit http://us.archive.ubuntu.com lucid/universe Packages                       
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://us.archive.ubuntu.com lucid/universe Sources                        
Hit http://us.archive.ubuntu.com lucid/multiverse Packages           
Hit http://us.archive.ubuntu.com lucid/multiverse Sources            
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://us.archive.ubuntu.com lucid-updates/main Packages         
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources    
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages     
Hit http://security.ubuntu.com lucid-security/restricted Packages    
Hit http://security.ubuntu.com lucid-security/main Sources           
Hit http://security.ubuntu.com lucid-security/restricted Sources     
Hit http://security.ubuntu.com lucid-security/universe Packages      
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources      
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages   
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://security.ubuntu.com lucid-security/universe Sources       
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  kdebase-runtime kdelibs-bin kdelibs5 kdelibs5-data kdepimlibs5 kpackagekit
  krosspython krossruby libakonadiprivate1 libattica0 libdbusmenu-qt2
  libkdcraw8 libkexiv2-8 libphonon4 libplasma3 libqt4-assistant libqt4-dbus
  libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-svg
  libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4
  libsoprano4 phonon phonon-backend-xine plasma-scriptengine-javascript
  python-kde4 python-qt4 soprano-daemon virtuoso-nepomuk
The following packages will be upgraded:
  kdebase-runtime-data oxygen-icon-theme python-sip shared-desktop-ontologies
4 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
Need to get 19.9MB of archives.
After this operation, 1,364kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ lucid/main kdebase-runtime-data 4:4.5.3-0ubuntu1~lucid1~ppa1 [4,356kB]
Get:2 http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ lucid/main oxygen-icon-theme 4:4.5.3-0ubuntu1~lucid1~ppa1 [15.4MB]
Get:3 http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ lucid/main python-sip 4.10.2-1ubuntu1~lucid1~ppa1 [72.4kB]
Get:4 http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ lucid/main shared-desktop-ontologies 0.5-0ubuntu1~lucid1~ppa1 [124kB]
Fetched 19.9MB in 1min 32s (216kB/s)                                           
(Reading database ... 189221 files and directories currently installed.)
Preparing to replace kdebase-runtime-data 4:4.4.2-0ubuntu4.1 (using .../kdebase-runtime-data_4%3a4.5.3-0ubuntu1~lucid1~ppa1_all.deb) ...
Unpacking replacement kdebase-runtime-data ...
Replacing files in old package kdelibs5-data ...
Preparing to replace oxygen-icon-theme 4:4.4.2-0ubuntu2 (using .../oxygen-icon-theme_4%3a4.5.3-0ubuntu1~lucid1~ppa1_all.deb) ...
Unpacking replacement oxygen-icon-theme ...
Preparing to replace python-sip 4.10.1-0ubuntu1 (using .../python-sip_4.10.2-1ubuntu1~lucid1~ppa1_i386.deb) ...
Unpacking replacement python-sip ...
Preparing to replace shared-desktop-ontologies 0.3-1 (using .../shared-desktop-ontologies_0.5-0ubuntu1~lucid1~ppa1_all.deb) ...
Unpacking replacement shared-desktop-ontologies ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up kdebase-runtime-data (4:4.5.3-0ubuntu1~lucid1~ppa1) ...

Setting up oxygen-icon-theme (4:4.5.3-0ubuntu1~lucid1~ppa1) ...
Setting up python-sip (4.10.2-1ubuntu1~lucid1~ppa1) ...

Setting up shared-desktop-ontologies (0.5-0ubuntu1~lucid1~ppa1) ...
Processing triggers for python-support ...
:~$ 
```

Then I again tried to install Kexi and here is what happened:

```
:~$ sudo apt-get install kexi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kexi
:~$ 
```

---

### Post by davidmohammed on 2010-12-28
hmmm - give up!

on the [koffice website]("http://userbase.kde.org/KOffice/Download#Ubuntu_and_Kubuntu") they recommend moving to 10.10 to install kexi.  Kexi as you have found is not in the 2.1.2 version of KOffice.

I thought that backports had the latest version.  Looks like my bad.

---

### Post by davidmohammed on 2010-12-28
....


hold the front-page!

I've just enabled the backports repository in software sources - updates.

I then installed koffice from software centre - note in the more info button it should report koffice at version 2.2.0

then I typed in a terminal session

kexi

---

### Post by candra on 2010-12-28
> **davidmohammed said:**
> ....


hold the front-page!

I've just enabled the backports repository in software sources - updates.

I then installed koffice from software centre - note in the more info button it should report koffice at version 2.2.0

then I typed in a terminal session

kexi

YES, YES, YES, THAT WORKED!! KEXI IS INSTALLED AND RECOGNIZED...

...Now my issue is that there is an error when opening my old kexi database from my earlier version of kexi. But alas, that is a separate matter...

Thanks for all your hard work...

candra

---

