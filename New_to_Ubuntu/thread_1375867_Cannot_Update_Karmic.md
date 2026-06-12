---
title: "Cannot Update Karmic"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by nstorrs on 2010-01-08
Hello,

Every time I use the update manager, I am able to update all my applications but I get this as I'm checking for updates

Failed to fetch [http://ppa.launchpad.net///ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net///ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

In addition it says that it has been 36 days since the package information was last updated. Is this bad or just something to ignore. And how might I fix it. 

Thanks

Ubuntu 9.10, Dell XPS M1530

---

### Post by snowpine on 2010-01-08
[http://ppa.launchpad.net///ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net///ubuntu/dists/karmic/main/binary-amd64/Packages.gz) is not a default software source in a standard Ubuntu Karmic install. Please explain why you added it to your software sources, so we can assist you better.

---

### Post by kansasnoob on 2010-01-08
> **nstorrs said:**
> Hello,

Every time I use the update manager, I am able to update all my applications but I get this as I'm checking for updates

Failed to fetch [http://ppa.launchpad.net///ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net///ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

In addition it says that it has been 36 days since the package information was last updated. Is this bad or just something to ignore. And how might I fix it. 

Thanks

Ubuntu 9.10, Dell XPS M1530

It would be helpful to see the output from Terminal of:

```
cat /etc/apt/sources.list
```

---

### Post by nstorrs on 2010-01-08
Here is the result of cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

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
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb games
deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) karmic main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security universe main multiverse restricted
deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) karmic-updates universe main multiverse restricted
nick@nick-laptop:~$ 



I used Ubuntu Tweak to add a couple of other repositories as well (Chromium, Gnome-Do, Medibuntu)

---

### Post by kansasnoob on 2010-01-08
You are missing a lot. I made a new one, please compare (notice I added your extra repos also at the very bottom):

> # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports restricted main multiverse universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe

deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb games
deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) karmic main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security universe main multiverse restricted
deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) karmic-updates universe main multiverse restricted




I used the US server, I think you should just replace your entire sources.list with the one I built. To do so open with gedit:

```
sudo gedit /etc/apt/sources.list
```

Then just use cut to get rid of the old and copy-n-paste the new, be sure to click on Save, then File > Quit. And just to be sure you got it right open with the cat command and double check it.

Then run:

```
sudo apt-get update
```

And post any errors here.

---

### Post by nstorrs on 2010-01-08
Thanks for all your help. After cut and pasting your sources.list and typing sudo apt-get update in the terminal I get this error:

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
  404  Not Found
Fetched 4,677B in 1s (2,505B/s)
W: Failed to fetch [http://ppa.launchpad.net///ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net///ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by snowpine on 2010-01-08
> **nstorrs said:**
> Thanks for all your help. After cut and pasting your sources.list and typing sudo apt-get update in the terminal I get this error:

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
  404  Not Found
Fetched 4,677B in 1s (2,505B/s)
W: Failed to fetch [http://ppa.launchpad.net///ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net///ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

[http://ppa.launchpad.net///ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net///ubuntu/dists/karmic/main/binary-amd64/Packages.gz) is garbage. I'm still not sure what it's doing in your software sources. Maybe just delete that line if you're not sure why you added it?

---

### Post by kansasnoob on 2010-01-09
Try commenting out those last four lines like this:

> **[COLOR="Red"]#[/COLOR]**deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb games
**[COLOR="Red"]#[/COLOR]**deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) karmic main universe restricted multiverse
**[COLOR="Red"]#[/COLOR]**deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security universe main multiverse restricted
**[COLOR="Red"]#[/COLOR]**deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) karmic-updates universe main multiverse restricted


Note: I used red only for visibility.

I think the "getdeb games" repo is the culprit, so after getting otherwise updated you can uncomment each repo, run apt-get update, and repeat until you're sure which was the offender. Then delete that one permanently.

---

### Post by nstorrs on 2010-01-09
I did what you suggested, and it stopped searching those sites but the problem still presisted. SO I also removed all the extra "Thrid Party Sources" I checked in Ubuntu Tweak but I'm still getting the same error:

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
  404  Not Found
Fetched 4,677B in 3s (1,432B/s)
W: Failed to fetch [http://ppa.launchpad.net///ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net///ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

And the Update Manager says that it has still been over a month since I updated.

My sources.list now reads as:

nick@nick-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports restricted main multiverse universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe

# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb games
# deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) karmic main universe restricted multiverse
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security universe main multiverse restricted
# deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) karmic-updates universe main multiverse restricted

---

### Post by kansasnoob on 2010-01-09
I assumed you were on the US server because of this from post #4:

> # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

Please go to Software Sources and see what server you're set on. If you're not in the US just set it to main server and then reload and see what happens.

I can fairly easily make you a new sources.list for the main server if need be.

Something sure hosed your original sources.list.

---

### Post by kansasnoob on 2010-01-09
Hells bells! I know what I did wrong!

You have 64 bit and I sent you an i386 list!

I can be sooooooooo stupid sometimes!

Be patient. Sorry for that. Please verify that you're running 64 bit and which server you use.

Well, either Main or US, I'm not going to get into anything else.

Sorry again. That was stupid!

---

### Post by nstorrs on 2010-01-09
Oh great. Yep I'm using 64 bit and the Main Server.

---

### Post by kansasnoob on 2010-01-09
Well, before you rip my heart out remember that something or someone else hosed your software sources long before me.

At least I own up to my mistakes, but we need to concentrate on fixing it!

I did not have a 64 bit list as I thought, it was Kubuntu Jaunty and that won't work. And I have no 64 bit machines here at this time.

So I booted an Ubuntu Jaunty i386 Live CD (the Karmic Live CD sessions crash my X) just to check out a procedure for you. 

Booted into my Jaunty Live CD I run:

```
cat /etc/apt/sources.list
```

and get this:

> ubuntu@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse


If you do the same with your Ubuntu Karmic 64 bit Live CD you can do the same!

Save it where you can find it. You could even save it here in Code tags so the format stays right.

Then you can replace your existing sources.list with that one using:

```
gksudo gedit /etc/apt/sources.list
```

But you'll have to make some edits.

Do you understand what "comments" are? A comment is **[COLOR="Red"]#[/COLOR]**.

So you'll need to comment out the "deb cdrom" line.

Then you'll need to uncomment all of these lines:

> # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe


That is remove the # from the front of the line.

Same thing with these:

> # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse


You'll still need to make a few more changes but that would be a step in the right direction.

And, honestly, you may find that lots of stuff is hosed. Something broke your software sources before I ever looked at it.

More files may have been hosed along with the sources.list.

There is also an online sources.list generator but I see it's not i386 or 64 bit specific either. It might however help you add the partner repo, etc.

I'll post more after I get out of the Live Desktop.

---

### Post by nstorrs on 2010-01-09
Oh Great! It worked thank you very much. I used my Karmic install cd and its on track. Thanks again

---

### Post by kansasnoob on 2010-01-09
> **nstorrs said:**
> Oh Great! It worked thank you very much. I used my Karmic install cd and its on track. Thanks again

Well, you're still not done!

You probably have no partner repo, etc!

We should get it right.

---

### Post by kansasnoob on 2010-01-09
I'm trying to pull in some help from a friend that runs 64 bit. ie: ranch hand

We need to get your other repos set up right!

---

### Post by ranch hand on 2010-01-09
You can reset the mirror you are using in System>Administration>Software Sources.  This is the USmain.

They prefer for you to not use the main if possible so that the mirrors can stay up to date more reliably.

Yes I am running 64bit.
> 
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

## Medibuntu - Ubuntu 9.10 "karmic koala"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

You will want to check the comments or lack there of on this list.

---

### Post by ranch hand on 2010-01-09
After reading this whole thread I think if I were you I would stay awayt from the Ubuntu Tweeks.  Looks to me like it is real good at screwing your sources.

It could well be that it is not up to date with all the changes in the basic operational system that were introduced in 9.10 as is the case with Start Up Manager (SUM).

I would put in my list and save it as the sources list and then save it again as "sources.list.save" if you are gong to do that kind of messing around with your list.

I mess with mine from time to time and can assure you that having the thing backed up is a real good idea.

For instance I wanted to have grub1.97 instead of grub1.97beta4 on here (I am on 9.10 now) and so I have a sources.list that I can plug in and get that  and then revert to my normal one.  All it has on it is;
> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted


---

### Post by nstorrs on 2010-01-09
Thank you both. It looks like I'm back on my feet. I have Medibuntu and Chromium and the others back up and running. MY Update Manager says that it has been less than an hour since I upgraded and everything. I really appreciate your help.

---

