---
title: "Intrepid Repository problems"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by icyest on 2008-12-29
I just upgraded to Intrepid 8.10 from Hardy 8.04. Does this mean I have to find my repositories all over again?

My understanding of repositories gives me the intuition that I have to install all of my repositories again. I noticed in my sources list under third-party software tab that many of the repositories have "Hardy" registered in them.
I would assume that Intrepid would update the repository list to register with Intrepid as opposed to Hardy, but that's not the case. I'd like to keep my existing apps up to date.

---

### Post by oldos2er on 2008-12-29
All the repositories should read "intrepid" now that you're running 8.10. Can you please post the output from 
"cat /etc/apt/sources.list"?

---

### Post by RomeReactor on 2008-12-29
> **icyest said:**
> My understanding of repositories gives me the intuition that I have to install all of my repositories again. I noticed in my sources list under third-party software tab that many of the repositories have "Hardy" registered in them.

If these are repositories you added yourself, then yes, you have to search for the correct ones (unless they still work). It is recommended that you disable all third party repositories you've added *before* a version upgrade, then add new ones, as is the case with the Medibuntu ones.

---

### Post by icyest on 2008-12-29
> **oldos2er said:**
> All the repositories should read "intrepid" now that you're running 8.10. Can you please post the output from 
"cat /etc/apt/sources.list"?

Here you are:
```
t@t:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse restricted universe main

## Major bug fix updates produced after the final release of the
## distribution.
# deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse restricted universe main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

# deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse restricted universe main
# deb http://winff.org/ubuntu hardy universe
deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu intrepid main
deb http://archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ intrepid-security main universe restricted multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main universe restricted multiverse
deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid main

```

Here is also what my source list looks like:
[[IMG]http://img368.imageshack.us/img368/1299/screenshotsoftwaresourclo1.png[/IMG]](http://imageshack.us)


Oh, also, would simply going to the "Edit" button and changing "Distribution:" box from Hardy to Intrepid suffice?

---

### Post by oldos2er on 2008-12-30
It looks like the Hardy repos are commented out, so that shouldn't cause problems. 

 "would simply going to the "Edit" button and changing "Distribution:" box from Hardy to Intrepid suffice?"

 The upgrade should've done this for you, so I'd say go ahead.

---

### Post by hyper_ch on 2008-12-30
I have started compiling a list of 3rd party repos - dependant on the release.

Have a look at it. The link is in my signature.

---

### Post by RomeReactor on 2008-12-30
> **hyper_ch said:**
> I have started compiling a list of 3rd party repos - dependant on the release.

Have a look at it. The link is in my signature.

This is *very* nice; thanks!

---

### Post by Partyboi2 on 2008-12-30
> **hyper_ch said:**
> I have started compiling a list of 3rd party repos - dependant on the release.

Have a look at it. The link is in my signature.
Finally a replacement :)

---

### Post by hyper_ch on 2009-01-07
> **Partyboi2 said:**
> Finally a replacement :)

I missed source-o-matic also hence I did create that ;)

---

