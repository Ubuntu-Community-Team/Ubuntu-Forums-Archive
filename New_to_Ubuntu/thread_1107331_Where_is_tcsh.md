---
title: "Where is tcsh??"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by jethro1138 on 2009-03-26
Ok, this is driving me nuts. I'm not a unix/linux newbie, and I've been trying ubuntu on-and-off for the past few years, and it always fails in some really ridiculous way which annoys me enough to just go back to plain old debian.

This time I want to actually figure out one of these things. I've just installed Ubuntu Server version 8.10. No problem. Except I like tcsh. It doesn't have it, and apt-cache search tcsh says there isn't one in the sources.

I've looked for an alternate source list (I'm using the one that comes with the default system) but can't find anything. 

So where do I get tcsh from? Anyone?

---

### Post by kpatz on 2009-03-26
**sudo apt-get install tcsh**

If you're not finding it, make sure your /etc/apt/sources.list is ok and then do **sudo apt-get update**.

---

### Post by lykwydchykyn on 2009-03-26
You need to enable the universe sources.  It's in there.
```

$ aptitude show tcsh
Package: tcsh
New: yes
State: not installed
Version: 6.14.00-7ubuntu1
Priority: optional
Section: universe/shells
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 733k
Depends: libc6 (>= 2.4), libncurses5 (>= 5.6+20071006-3)
Conflicts: tcsh-kanji (< 6.14.00-6)
Replaces: tcsh-kanji (< 6.14.00-6)
Provides: c-shell, tcsh-kanji
Description: TENEX C Shell, an enhanced version of Berkeley csh
 The TENEX C Shell is an enhanced version of the Berkeley Unix C shell. It includes all features of 4.4BSD C shell, plus a command-line editor,
 programmable word completion, spelling correction and more. The tcsh homepage can be found at http://www.tcsh.org/Home.

 Homepage: http://www.tcsh.org/

Tags: implemented-in::c, interface::shell, role::program, scope::utility, uitoolkit::ncurses

```

Just edit your /etc/apt/sources.list, it's probably in there but just commented out.

---

### Post by LowSky on 2009-03-26
um its there

[http://packages.ubuntu.com/intrepid/tcsh](http://packages.ubuntu.com/intrepid/tcsh)

here is the deb
[http://mirrors.kernel.org/ubuntu/pool/universe/t/tcsh/tcsh_6.14.00-7ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/t/tcsh/tcsh_6.14.00-7ubuntu1_i386.deb)

---

### Post by jethro1138 on 2009-03-26
> **kpatz said:**
> **sudo apt-get install tcsh**

If you're not finding it, make sure your /etc/apt/sources.list is ok and then do **sudo apt-get update**.

I did all that... that's why I'm asking.

---

### Post by zacktu on 2009-03-26
I typed 'tchs' at the command line, and here's what happened:

zack@mozart:~$ tcsh
The program 'tcsh' is currently not installed.  You can install it by typing:
sudo apt-get install tcsh

---

### Post by jethro1138 on 2009-03-26
> **lykwydchykyn said:**
> You need to enable the universe sources.  It's in there.

Just edit your /etc/apt/sources.list, it's probably in there but just commented out.

I dunno, I have a lot of universe in there. The only ones commented out are the backports:

```

root@vrooster:~# fgrep universe /etc/apt/sources.list
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe

```

---

### Post by LowSky on 2009-03-26
just use my link, its the DEB from the Intrepid repo

---

### Post by jethro1138 on 2009-03-26
> **zacktu said:**
> I typed 'tchs' at the command line, and here's what happened:

zack@mozart:~$ tcsh
The program 'tcsh' is currently not installed.  You can install it by typing:
sudo apt-get install tcsh

Yeah, I already know it's not installed (: I'm trying to figure out why I can't install it. I guess I should've mentioned that I did an apt-get install tcsh, but it couldn't find it. I think my repositories are off.

---

### Post by jethro1138 on 2009-03-26
> **LowSky said:**
> just use my link, its the DEB from the Intrepid repo

Yeah, but then what about the next package I can't find? I actually want apt and the repositories to all work. I want to fix the source of the problem.

---

### Post by LowSky on 2009-03-26
ok... want to show us your entire source list?

---

### Post by jethro1138 on 2009-03-26
> **LowSky said:**
> ok... want to show us your entire source list?

Sure; it's the unmodified version installed when I built the machine about an hour ago:

```

# 
# deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release amd64 (20081028.1)]/ intrepid main restricted

#deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release amd64 (20081028.1)]/ intrepid main restricted
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
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
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

```

---

### Post by LowSky on 2009-03-26
try mine

```
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
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
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
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
```

---

### Post by jethro1138 on 2009-03-26
> **LowSky said:**
> try mine

I did, same result... actually the ONLY difference between yours and mine is that I have two commented out "deb cdrom" entries, and you only have one... but again, they're commented out anyway.

I /do/ get a lot of hash sum mismatches, like this: 
```

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.bz2  Hash Sum mismatch

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.bz2  Hash Sum mismatch

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.bz2  Hash Sum mismatch

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.bz2  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.bz2  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.bz2  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.bz2  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.bz2  Hash Sum mismatch

```

---

### Post by lykwydchykyn on 2009-03-26
Do you get any errors from "apt-get update"?

---

### Post by LowSky on 2009-03-26
go try using a different server

system > Admin > software sources

Click on "Download from:" and choose other, then choose best server.

the run 

sudo apt-get update

---

### Post by LowSky on 2009-03-26
found a cure, turns out it could be a internet proxy screwing up your app fetching
run
```
sudo apt-get autoclean & sudo apt-get clean
```
then try to install whatever

then take a look at this as this should fix it
[http://ubuntuforums.org/showpost.php?p=4952791&postcount=10](http://ubuntuforums.org/showpost.php?p=4952791&postcount=10)

---

### Post by jethro1138 on 2009-03-26
> **lykwydchykyn said:**
> Do you get any errors from "apt-get update"?

Yeah, the Hash Sum Mismatch errors posted above.

---

### Post by jethro1138 on 2009-03-26
> **LowSky said:**
> go try using a different server                           
system > Admin > software sources

I'm running Ubuntu server, so I have no GUI. Is there a list of the different repositories anywhere? 

Strangely enough, any machine I've installed Ubuntu /desktop/ on, I've had no problem installing tcsh (or any other package) - I've compared the sources.list to the server version and it is IDENTICAL so I have no idea what's going on...

> **LowSky said:**
> found a cure, turns out it could be a internet proxy screwing up your app fetching

Oh wow. That totally worked! 

I have no idea why or how, since I'm not using a proxy... but hey!

Thanks!

---

### Post by LowSky on 2009-03-31
Your Welcome 

You might not be using a proxy but you ISP might be

The autoclean thing I found which I use from time to time to clear out old deb packages, anyway, after I realized you were running Server and not desktop it seemd like the last thing to try

---

