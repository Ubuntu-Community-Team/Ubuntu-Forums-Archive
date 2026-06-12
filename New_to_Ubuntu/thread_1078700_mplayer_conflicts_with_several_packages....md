---
title: "mplayer conflicts with several packages..."
date: 2009-02-23
forum: New to Ubuntu
---

### Post by DiscoKiller on 2009-02-23
Hi all, 

I`m just returning to ubuntu from a long leave of absence and things have changed :)

i`m trying to get embedded video to play in swftfox- when trying to install the mplayer and gecko-mplyer packages i get the following error message

________________________________________________________________
The following packages have unmet dependencies.
  gnome-mplayer: Depends: mplayer (>= 1.0) or
                          mplayer-nogui (>= 1.0) but it is not going to be installed
E: Broken packages
------------------------------------------------------------------------------------------

so if i try to install the packages it mentions i get other similar messages pertaining to other dependencies and so the vicious circle begins....

i`m guessing there is a conflict somewhere but i am at a loss to figure out what i`ve done to my poor lappy. 

If anyone can point me in the right direction I would of course be most grateful

Peace

DK

---

### Post by taurus on 2009-02-23
Did you mix repos in your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by DiscoKiller on 2009-02-23
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by taurus on 2009-02-23
What are the outputs when you run these two commands?

```
sudo apt-get update
sudo apt-get install mplayer
```

---

### Post by DiscoKiller on 2009-02-23
sudo apt-get update...

....Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/universe Sources
Get: 1 [http://winff.org](http://winff.org) intrepid Release.gpg [197B]
Ign [http://winff.org](http://winff.org) intrepid/universe Translation-en_GB
Get: 2 [http://winff.org](http://winff.org) intrepid Release [2902B]
Ign [http://winff.org](http://winff.org) intrepid Release
Hit [http://winff.org](http://winff.org) intrepid/universe Packages
Fetched 198B in 2s (86B/s)
Reading package lists... Done
W: GPG error: [http://winff.org](http://winff.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1CD52D7BAAFE086A
W: You may want to run apt-get update to correct these problems


sudo apt-get install mplayer

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  mplayer: Depends: libasound2 (> 1.0.17) but 1.0.15-3ubuntu4 is to be installed
           Depends: libggi2 (>= 1:2.2.2) but it is not going to be installed
           Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
           Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-2.1ubuntu1 is to be installed
           Depends: libmp3lame0 (>= 3.98) but it is not installable
           Depends: libopenal1 (>= 1:1.3.253) but it is not installable
           Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
           Depends: libspeex1 (>= 1.2~beta3-1) but 1.1.12-3ubuntu0.8.04.1 is to be installed
           Depends: libx264-59 (>= 1:0.svn20080408) but it is not installable
E: Broken packages

---

### Post by mc4man on 2009-02-23
There's many ways to get any mplayer rev. you want on hardy, the one way that won't work is to try to install a build meant for intrepid.
Lose that winff.org source and you should be ok.

---

### Post by DiscoKiller on 2009-02-23
Thank you - worked a treat, didnt occur to me :)

A thousand thankyous again 

Peace 

DK

---

### Post by thrillerbee on 2009-06-08
nm; I was missing universe repositories.  Please disregard

Could someone help me understand what's going on here & how I might correct it?

Thanks.

sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libggi2 (>= 1:2.2.2) but it is not installable
           Depends: libopenal1 but it is not installable
           Depends: libsvga1 but it is not installable
E: Broken packages

---

