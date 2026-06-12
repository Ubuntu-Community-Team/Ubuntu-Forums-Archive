---
title: "Cant sudo apt-get update"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by phoenixankit on 2007-06-03
I am not able to download most application that I need. Each one of them says " add the repository to my list of sources" and then sudo apt-get update and then proceed. For eg. If I want to install Alien, the website says
> You can install alien itself from the Ubuntu Universe repository by adding the repository to your list of sources and doing:
```
$sudo apt-get update
$sudo apt-get install alien
```

Now I know, that to add the whatever needed repository to my list of sources, I need to
```
sudo gedit /etc/apt/sources.list
```
and then uncomment them, then save the file..
and then I need to sudo apt-get update..
But, if I try sudo apt-get update, It gets stuck on ```
99% [Connecting to in.archive.ubuntu.com (91.189.88.31)]
```

Help please........please!!!
I'd like to stick to the command line way, not the synaptic way, cuz that doesnt work either....

P.S: Theres another thread I started in the Absotute begginers forum: But they were not able to solve the problem: [http://ubuntuforums.org/showthread.php?t=460778](http://ubuntuforums.org/showthread.php?t=460778)

---

### Post by phoenixankit on 2007-06-03
Bump

---

### Post by cantormath on 2007-06-03
Which repos are you uncommenting, all of them?
you just need to uncomment universe and maybe multiverse....Lets see the sources.list.  Sometimes the repos get hammered and if check back in a bit they will work.  This can happen, but rarely.

---

### Post by phoenixankit on 2007-06-03
Earlier, it was this:
```
deb http://ubuntu.beryl-project.org feisty main
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://in.archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb http://in.archive.ubuntu.com/ubuntu/ feisty-security universe
deb http://in.archive.ubuntu.com/ubuntu/ feisty-security multiverse
deb http://ubuntu.beryl-project.org feisty main

deb-src http://ubuntu.beryl-project.org feisty main
```
Now, i've edited it to this:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

---

### Post by phoenixankit on 2007-06-03
On doing *sudo apt-get update*  , it gets stuck on **99% [Connecting to us.archive.ubuntu.com (91.189.88.31)]  ** and then, I get this:
```
Err http://archive.ubuntu.com feisty Release.gpg     
  Could not connect to archive.ubuntu.com:80 (91.189.88.31), connection timed out [IP: 91.189.88.31 80]
```

---

### Post by cantormath on 2007-06-03
Try just commenting these at the end```

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
 deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
 deb http://security.ubuntu.com/ubuntu feisty-security universe
 deb-src http://security.ubuntu.com/ubuntu feisty-security universe
 deb http://security.ubuntu.com/ubuntu feisty-security multiverse
 deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```

---

