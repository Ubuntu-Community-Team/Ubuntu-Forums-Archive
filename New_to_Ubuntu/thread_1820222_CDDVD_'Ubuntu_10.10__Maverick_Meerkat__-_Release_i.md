---
title: "CD/DVD 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)' is required"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by agnisflugen on 2011-08-07
i had a little red triangle on the top right of my screen indicating i have some updates. so i opened up systems-admin-update manager, but got an error message saying another program like synaps or something was opened...so today i restarted my netbook and then tried again, this time i got the following message: 



CD/DVD 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)' is required. Please insert the above CD/DVD into the drive '/cdrom/' to install software packages from it.

doesn't anyone know what this means, and am i able to work around it since i don't have a CD drive? 


**netbook**: Asus Eee PC 1215T
**OS:** ubuntu desktop version 10.10 (maverick) Kernel Linux 2.6.35-generic Gnome 2.32.0

  **message:** CD/DVD 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)' is required. Please insert the above CD/DVD into the drive '/cdrom/' to install software packages from it.

---

### Post by bodhi.zazen on 2011-08-07
Open /etc/apt/sources.list and comment out, put a # in the front of the line referring to the CD

```
gksu gedit /etc/apt/sources.list
```

---

### Post by stoneage on 2011-08-07
Go to software sources and see if the CD is enabled as a source. It seems to think you installed from a CD, which I guess is not the case if you don't have a disc drive.

---

### Post by agnisflugen on 2011-08-07
> **bodhi.zazen said:**
> Open /etc/apt/sources.list and comment out, put a # in the front of the line referring to the CD

```
gksu gedit /etc/apt/sources.list
```


where is the etc at? is it under system admin?

---

### Post by agnisflugen on 2011-08-07
> **stoneage said:**
> Go to software sources and see if the CD is enabled as a source. It seems to think you installed from a CD, which I guess is not the case if you don't have a disc drive.

how do i find software sources?....wait at minute...nevermind.i just found it...but where does it say if a cd is enabled? i can't find it...

---

### Post by haqking on 2011-08-07
> **agnisflugen said:**
> where is the etc at? is it under system admin?

the command shows you where it is, it is a directory.

type as shown into terminal or as stated above use software sources

---

### Post by agnisflugen on 2011-08-07
okay, i don't know what any of that means...but i did find where it says in software that it's installable from a CD, how do i go about changing that?

---

### Post by stoneage on 2011-08-07
If you copy/paste ```
gksu gedit /etc/apt/sources.list
``` into a terminal it will open the file for you in a text editor. 

Look for the entry for the CD and, as bodhi.zazen said, put a # in front of it. That tells your system to ignore that line.

The list in the file sources.list is the same one in Software Sources under the Other Software tab.


EDIT - > **agnisflugen said:**
> okay, i don't know what any of that means...but i did find where it says in software that it's installable from a CD, how do i go about changing that?
 Try the 'Other Software' tab


p.s. - I don't use 11.04, or I would post screenshots.

---

### Post by haqking on 2011-08-07
> **agnisflugen said:**
> okay, i don't know what any of that means...but i did find where it says in software that it's installable from a CD, how do i go about changing that?


just open a terminal as mentioned, if you dont know how to then press

ctrl+alt+t

in the terminal type the following as said before:

gksudo gedit /etc/apt/sources.list

enter password (which is your login password)

when the file opens look for the line you mentioned before which references the CD as a soucre and comment it out which means placing a # at the beginning of the line and then save it

---

### Post by agnisflugen on 2011-08-07
okay, that makes sense...i was able to do that :)

---

### Post by haqking on 2011-08-07
> **agnisflugen said:**
> okay, that makes sense...i was able to do that :)

ok cool.

If this is now solved use the thread tools to mark it as solved for others in future.

---

### Post by agnisflugen on 2011-08-07
i tried to do a systems update again, and now it says, 


W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/main/i18n/Translation-en.bz2  
, W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/restricted/i18n/Translation-en.bz2  
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/Release  
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by haqking on 2011-08-07
> **agnisflugen said:**
> i tried to do a systems update again, and now it says, 


W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/main/i18n/Translation-en.bz2  
, W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/restricted/i18n/Translation-en.bz2  
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/Release  
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

can you post the contents or a screen dump of your sources list

---

### Post by agnisflugen on 2011-08-07
i'm so embarrassed...i don't know how to do that...i have so much to learn it's a little overwhelming...

---

### Post by agnisflugen on 2011-08-07
on a good note, when i clicked on update manager again a few minutes ago, i didn't get that error message again, and it showed all the updates needed.....so maybe it resolved itself?!? i don't know...i'm confused...

---

### Post by stoneage on 2011-08-07
Paste ```
gksu gedit /etc/apt/sources.list
``` into a terminal, then copy paste the contents of that file here.

Be sure to put it in 'Quote /Quote' tags for easier reading.

From what I can see the links are working, but you could try downloading from another server.

Go back to Software Sources and where it says 'Download from:' - choose another server.




EDIT - > **agnisflugen said:**
> on a good note, when i clicked on update manager again a few minutes ago, i didn't get that error message again, and it showed all the updates needed.....so maybe it resolved itself?!? i don't know...i'm confused...

Yeah, it could be the server was temporarily unavailable.

---

### Post by haqking on 2011-08-07
> **stoneage said:**
> 
Yeah, it could be the server was temporarily unavailable.

+1

well looks sorted then. enjoy

---

### Post by agnisflugen on 2011-08-07
i'm not sure how it got changed to the  CD being enabled as a source..... up until this week updates would come up automatically and all i had to do was click "install" and enter my password...but since i have typed:

gksu gedit /etc/apt/sources.list 

into terminal, put that # sign in front of that line  as instructed and then waited a few minutes all my updates are now showing up without any wicked error messages....

i'm still confused about what happened, but i'm grateful to all your kindness and patience :)

---

### Post by haqking on 2011-08-07
> **agnisflugen said:**
> i'm not sure how it got changed to the  CD being enabled as a source..... up until this week updates would come up automatically and all i had to do was click "install" and enter my password...but since i have typed:

gksu gedit /etc/apt/sources.list 

into terminal, put that # sign in front of that line  as instructed and then waited a few minutes all my updates are now showing up without any wicked error messages....

i'm still confused about what happened, but i'm grateful to all your kindness and patience :)

congrats, things happen occasionally so dont worry.  help is always here.

Enjoy

---

