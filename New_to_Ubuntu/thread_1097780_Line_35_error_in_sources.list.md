---
title: "Line 35 error in sources.list"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Botbob89 on 2009-03-16
I've been using the sources.list fine all week with no problems whatsoever, but today I have encountered this problem.

I have not so much as opened sources.list and definitely haven't changed it...

It says that there is in a problem in line 35 if you could have a look please....

Thanks in advance....

```
deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb Index of /ubuntu intrepid-backports main restricted universe multiverse
deb-src Index of /ubuntu intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

# deb http://wine.budgetdedicated.com/apt intrepid main
```

---

### Post by albandy on 2009-03-16
this line:
deb-src Index of /ubuntu intrepid-backports main restricted universe multiverse
is erroneus, comment it with putting #
#deb-src Index of /ubuntu intrepid-backports main restricted universe multiverse

---

### Post by yeats on 2009-03-16
```
 26
 27 ## Uncomment the following two lines to add software from the 'backports'
 28 ## repository.
 29 ## N.B. software from this repository may not have been tested as
 30 ## extensively as that contained in the main release, although it includes
 31 ## newer versions of some applications which may provide useful features.
 32 ## Also, please note that software in backports WILL NOT receive any review
 33 ## or updates from the Ubuntu security team.
 34 # deb Index of /ubuntu intrepid-backports main restricted universe multiverse
** 35 deb-src Index of /ubuntu intrepid-backports main restricted universe multiverse**

```

You'll want to put a # before this line.  It's the "Index of" part that is invalid....


[ignore my added line numbers :-) ]

---

### Post by Botbob89 on 2009-03-16
OK that appears to have worked thanks :)

---

### Post by hyper_ch on 2009-03-16
you can also use my tool to generate a sources list. It's in my signature.

---

### Post by oldos2er on 2009-03-16
Intrepid backports sources should look like this:
```
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports restricted universe multiverse main
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports restricted universe multiverse main
```

---

