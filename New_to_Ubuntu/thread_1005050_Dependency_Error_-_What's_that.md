---
title: "Dependency Error - What's that?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by thadacto on 2008-12-07
I'm trying to install a .deb package - Cinelerra, but keep getting this Error:
[COLOR="Red"]Error: Dependency is not satisfiable: libasound2[/COLOR]
What's the problem and how do I fix it?
I've been into the Synaptic Manager and there are no broken packages. - at least, not now, there was previously.

---

### Post by taurus on 2008-12-07
It's the Alsa library.  I have it on my machine (Intrepid).  Can you post your /etc/apt/soures.list?

```
cat /etc/apt/sources.list
```

---

### Post by thadacto on 2008-12-07
Thanks taurus - it's me again with another problem - got the panel sorted thanks.
Here's the results of that code:
george@george-desktop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy universe

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
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
george@george-desktop:~$

---

### Post by BGFG on 2008-12-07
The way linux works is that there are libraries pre-existing on the system that software looks for when it is being installed, hence 'dependancies' In your case the library either isn't there or it's an older version than cinelerra needs.

Search for it in synaptic and try to install or upgrade it.

---

### Post by thadacto on 2008-12-07
Just done that while I was waiting as I noticed you had libasound2-plugins which I didn't have. Tried installing cinelerra again but failed for same reason.
Then I reinstalled libasound2 - still same problem.
I'm running +64 and this version of Cinelerra is the AMD 64 version which I found on a debian web site but it's not in the synaptic Manager. 
Looks like I'll have to leave itb till tomorrow as I've been infront of theis machine for the last 12 hours and my mind is just going funny - not to mention my eyes!!
Many thanks taurus.

---

