---
title: "software installation"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by dromani on 2009-12-23
Sometime ago I installed ubuntu 9.4 in my laptop and I just loved it. Installing new software through the synaptic package manager.

At the end I had to remove it because 9.4 had a conflict with my sound card.

I recently installed the 9.10, in two machines and I'm happy to see that sound card works perfectly, but in both machines I have the same problem with software installing and updating.

Now for example, when updating software I get the following error:

> 
W: Failed to fetch [http://archive.getdeb.net/ubuntu/pool/apps/f/filezilla/filezilla_3.3.0-1~getdeb1_i386.deb](http://archive.getdeb.net/ubuntu/pool/apps/f/filezilla/filezilla_3.3.0-1~getdeb1_i386.deb)
  Could not connect to archive.getdeb.net:80 (94.126.144.44), connection timed out


W: Failed to fetch [http://archive.getdeb.net/ubuntu/pool/apps/f/filezilla/filezilla-common_3.3.0-1~getdeb1_all.deb](http://archive.getdeb.net/ubuntu/pool/apps/f/filezilla/filezilla-common_3.3.0-1~getdeb1_all.deb)
  Unable to connect to archive.getdeb.net http:


W: Failed to fetch [http://archive.getdeb.net/ubuntu/pool/apps/g/gimp/gimp_2.6.8-1~getdeb1_i386.deb](http://archive.getdeb.net/ubuntu/pool/apps/g/gimp/gimp_2.6.8-1~getdeb1_i386.deb)
  Unable to connect to archive.getdeb.net http:


W: Failed to fetch [http://archive.getdeb.net/ubuntu/pool/apps/g/gimp/libgimp2.0_2.6.8-1~getdeb1_i386.deb](http://archive.getdeb.net/ubuntu/pool/apps/g/gimp/libgimp2.0_2.6.8-1~getdeb1_i386.deb)
  Unable to connect to archive.getdeb.net http:


W: Failed to fetch [http://archive.getdeb.net/ubuntu/pool/apps/g/gimp/gimp-data_2.6.8-1~getdeb1_all.deb](http://archive.getdeb.net/ubuntu/pool/apps/g/gimp/gimp-data_2.6.8-1~getdeb1_all.deb)
  Unable to connect to archive.getdeb.net http:


W: Failed to fetch [http://archive.getdeb.net/ubuntu/pool/apps/p/pidgin/libpurple-bin_2.6.4-1~getdeb1_all.deb](http://archive.getdeb.net/ubuntu/pool/apps/p/pidgin/libpurple-bin_2.6.4-1~getdeb1_all.deb)
  Unable to connect to archive.getdeb.net http:


W: Failed to fetch [http://archive.getdeb.net/ubuntu/pool/apps/p/pidgin/libpurple0_2.6.4-1~getdeb1_i386.deb](http://archive.getdeb.net/ubuntu/pool/apps/p/pidgin/libpurple0_2.6.4-1~getdeb1_i386.deb)
  Unable to connect to archive.getdeb.net http:


W: Failed to fetch [http://archive.getdeb.net/ubuntu/pool/apps/r/rhythmbox/rhythmbox_0.12.6-1~getdeb1_i386.deb](http://archive.getdeb.net/ubuntu/pool/apps/r/rhythmbox/rhythmbox_0.12.6-1~getdeb1_i386.deb)
  Unable to connect to archive.getdeb.net http:


W: Failed to fetch [http://archive.getdeb.net/ubuntu/pool/apps/t/transmission/transmission-gtk_1.76-1~getdeb1_i386.deb](http://archive.getdeb.net/ubuntu/pool/apps/t/transmission/transmission-gtk_1.76-1~getdeb1_i386.deb)
  Unable to connect to archive.getdeb.net http:


W: Failed to fetch [http://archive.getdeb.net/ubuntu/pool/apps/t/transmission/transmission-common_1.76-1~getdeb1_all.deb](http://archive.getdeb.net/ubuntu/pool/apps/t/transmission/transmission-common_1.76-1~getdeb1_all.deb)
  Unable to connect to archive.getdeb.net http:



I'm completely newbie in Ubuntu and generally speaking I don't have a deep knowledge of computing, but it seems to me that this new version made more complicated the installation of additional software. 

Any suggestion on how to fix the problem?

Thank you

---

### Post by LuisGMarine on 2009-12-23
I'm not exactly sure why you have the getdeb, but that seems to be the problem of your updates.  

The easiest thing you can do is open up your /etc/apt/sources.list and put a # in front of the getdeb sources.  First do:

```
gksudo gedit /etc/apt/sources.list
```

and all the links that you see with the words "getdeb" you can put a # to comment them out.  After all is done run:

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by snowpine on 2009-12-23
getdeb.net is *not* one of the default software sources for Ubuntu, so you must have added it yourself for some reason. So please don't blame Ubuntu for the problem. :)

I would recommend the following:

```
gksu gedit /etc/apt/sources.list
```

Find any and all lines containing a getdeb.net URL and type a # symbol at the beginning of the line. This will "comment out" that line so it is skipped. Now you will just have the official Ubuntu software sources. Save the file and try your update again.

---

### Post by ursusca on 2010-02-28
Hello!

I've faced with similar problem couple of days ago.

> Err [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release.gpg                     
  Could not connect to archive.getdeb.net:80 (94.126.144.44), connection timed out
Err [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Translation-en_US
  Unable to connect to archive.getdeb.net http:
Reading package lists... Done                         
W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (94.126.144.44), connection timed out

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/apps/i18n/Translation-en_US.bz2](http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/apps/i18n/Translation-en_US.bz2)  Unable to connect to archive.getdeb.net http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

I don't have any lines containing a getdeb.net in my sources.list file.

```
cat /etc/apt/sources.list 
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ru.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://ru.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ru.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://ru.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ru.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://ru.archive.ubuntu.com/ubuntu/ karmic universe
deb http://ru.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://ru.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ru.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://ru.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://ru.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://ru.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ru.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://ru.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
```

Any suggestion on how to fix the problem?

Thanks

---

### Post by dnairb on 2010-02-28
It's possible you have further sources.list files in /etc/apt/sources.list.d/

Can you post the terminal output of:

```
ls /etc/apt/sources.list.d/
```

---

### Post by spikyjt on 2010-02-28
apt also looks at files in /etc/apt/sources.list.d/
It's a folder of smaller .list files that add custom sources. If you added GetDeb's repos with Synaptic or other graphical package manager, or straight from the getdeb.net website, the source list was probably added to this folder. Have a look in that folder and see if there are any references to getdeb in there. If so, delete them (you'll need sudo if you do it on the command line). Or look at configuring package repositories through Synaptic. I'm afraid I can't point you in the right direction of the option for that, as I use KPackageKit myself, but it should be in Options or Settings. You can then untick any references to getdeb.

---

### Post by ursusca on 2010-02-28
> **spikyjt said:**
> apt also looks at files in /etc/apt/sources.list.d/
...

Thank you spikyjt. I've found it.

```
root@ubuntubear:/etc/apt# grep -r getdeb *
sources.list.d/getdeb.list:deb http://archive.getdeb.net/ubuntu karmic-getdeb apps
Binary file trusted.gpg matches

```

and commented it.

---

