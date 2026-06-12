---
title: "Can someone help me through upgrading Ubuntu?"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by thehereaway on 2009-05-18
Okay, i'm on Ubuntu 7.10 i think it is - and my computer is so messed up i really think i should upgrade. However, i'm worried the upgrade to 8.04 LTS might not work as when ever i try to install updates within the update manager i get messages like the following...


> W: Failed to fetch [http://security.ubuntu.com/ubuntu/po...tu0.2_i386.deb](http://security.ubuntu.com/ubuntu/po...tu0.2_i386.deb)
404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/po...ntu3.4_all.deb](http://security.ubuntu.com/ubuntu/po...ntu3.4_all.deb)
404 Not Found
etc...

So i'm worried if i attempt to update to 8.04 it won't work and i'll lose everything.

Also, will my hard drive be wiped if i upgrade? I have a pretty big music collection and i'd hate to lose it.

---

### Post by llamakc on 2009-05-18
See answer below. I didn't realize Gutsy had expired.

---

### Post by taurus on 2009-05-18
Gutsy has expired and no longer supported.  Therefore, you will not get any security fix or update.

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by thehereaway on 2009-05-18
> **taurus said:**
> Gutsy has expired and no longer supported.  Therefore, you will not get any security fix or update.

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

Oh bugger. Will i have to do the whole CD thing for the newer Ubuntu?

---

### Post by snowpine on 2009-05-18
Ubuntu 7.10 has reached its "end of life" and is no longer supported. The "official answer" is to back up your documents and install fresh. However, there is an unofficial upgrade method that might do the trick (though I still recommend backing everything up first).

From the terminal:

```
gksu gedit /etc/apt/sources.list
```

Use the find/replace feature to change all "gutsy" to "hardy". Save the file and quit gedit.

Now, 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

I can't promise it will work, but it's worth a try. :)

---

### Post by taurus on 2009-05-18
You either have to upgrade to something a little newer or edit /etc/apt/sources.list and replace the repos from [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) (or something similar to that) to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/).

---

### Post by thehereaway on 2009-05-18
> **taurus said:**
> You either have to upgrade to something a little newer or edit /etc/apt/sources.list and replace the repos from [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) (or something similar to that) to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/).

Could you by any chance post a step-by-step instruction of how to do this? I really have no idea what i'm doing.

---

### Post by taurus on 2009-05-18
Make a back up copy of your /etc/apt/sources.list.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.org
```
Then edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and replace the [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) with [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/).  Save the chances and run

```
sudo apt-get update
sudo apt-get upgrade
```
Otherwise, just post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by thehereaway on 2009-05-18
Thanks, should i back up my files before i do this?

---

### Post by taurus on 2009-05-18
It is just a good practice to _back up_ your personal files even if you don't plan to do anything major to your machine.

---

### Post by albinootje on 2009-05-18
> **thehereaway said:**
> Could you by any chance post a step-by-step instruction of how to do this? I really have no idea what i'm doing.

This is a desktop machine, and not a server ?

Update notes are here : [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

I've read in the past that it is recommended to use the update manager instead of using "apt-get dist-upgrade".

And also make sure that the package "ubuntu-desktop" is installed before doing the upgrade.

---

### Post by thehereaway on 2009-05-18
> **taurus said:**
> Make a back up copy of your /etc/apt/sources.list.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.org
```
Then edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and replace the [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) with [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/).  Save the chances and run

```
sudo apt-get update
sudo apt-get upgrade
```
Otherwise, just post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

i have [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) instead of [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) do i replace each link to that URL in the sources.list?

---

### Post by thehereaway on 2009-05-18
> **albinootje said:**
> This is a desktop machine, and not a server ?

Update notes are here : [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

I've read in the past that it is recommended to use the update manager instead of using "apt-get dist-upgrade".

And also make sure that the package "ubuntu-desktop" is installed before doing the upgrade.

How do i ensure this package is installed?

---

### Post by SunnyRabbiera on 2009-05-18
> **thehereaway said:**
> i have [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) instead of [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) do i replace each link to that URL in the sources.list?

its the same thing, just replace [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) with [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

---

### Post by thehereaway on 2009-05-18
> **SunnyRabbiera said:**
> its the same thing, just replace [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) with [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

Ok

---

### Post by SunnyRabbiera on 2009-05-18
> **thehereaway said:**
> For each time it says that yeah? Or do i only need to replace a certain one?

I suggest replace all of them, that way your sources are guaranteed to be updated

---

### Post by taurus on 2009-05-18
> **thehereaway said:**
> i have [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) instead of [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) do i replace each link to that URL in the sources.list?

Actually, you want to replace [http://gb.archive.ubuntu.com/](http://gb.archive.ubuntu.com/) with [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/).

---

### Post by thehereaway on 2009-05-18
> **taurus said:**
> Actually, you want to replace [http://gb.archive.ubuntu.com/](http://gb.archive.ubuntu.com/) with [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/).

Dam, i already did it. I also have [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) will they need to be changed too?

---

### Post by SunnyRabbiera on 2009-05-18
> **thehereaway said:**
> Dam, i already did it. I also have [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) will they need to be changed too?

I say leave that one alone

---

### Post by taurus on 2009-05-18
> **thehereaway said:**
> Dam, i already did it. I also have [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) will they need to be changed too?

Yes.

---

### Post by thehereaway on 2009-05-18
Shall i paste the contents of my sources.list in here so you guys can check it over?

---

### Post by thehereaway on 2009-05-18
I tried > sudo apt-get update and it said 404 Not Found for a huge list of stuff still.

EDIT: currently installing updates within the update manager and it seems to be working

---

### Post by xebian on 2009-05-18
> **thehereaway said:**
> i have [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) instead of [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) do i replace each link to that URL in the sources.list?

Normally, you only replace 'old-release' to 'new-release'.  So in your case replace 'gutsy' to 'hardy', and then do apt-get update && apt-get dist-upgrade.

The 'gb' in gb.archive.ubuntu.com means you are using the UK repo server.
The 'us' means you will be using the US servers.  So unless you are in the US, leave 'gb' alone.

It's not recommended but I went straight to jaunty from hardy.  Just to show you how easy it is.

---

### Post by albinootje on 2009-05-18
> **thehereaway said:**
> Shall i paste the contents of my sources.list in here so you guys can check it over?

Yes, please, that would be very useful!

---

### Post by thehereaway on 2009-05-19
> **albinootje said:**
> Yes, please, that would be very useful!

> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy universe
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

## Wine, Ubuntu Gutsy (7.10):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main

deb [http://apt.emesene.org/](http://apt.emesene.org/) ./
deb-src [http://apt.emesene.org/](http://apt.emesene.org/) ./

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) dapper main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) dapper-updates main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) dapper-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

...

---

### Post by albinootje on 2009-05-19
Thanks.
Please do the following :
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-OLD

```
And then :
```

gksu gedit /etc/apt/sources.list

```
And put only the following there :

```

deb http://old-releases.ubuntu.com/ubuntu/ gutsy main restricted
#deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy main restricted
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-updates main restricted
#deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy-updates main restricted

deb http://old-releases.ubuntu.com/ubuntu/ gutsy universe
#deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy universe
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-updates universe
#deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy-updates universe

deb http://old-releases.ubuntu.com/ubuntu/ gutsy multiverse
#deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-updates multiverse
#deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy-updates multiverse

```
In this list 3rd party repositories have been removed, they will be disabled during a dist upgrade anyway, and I've disabled the deb source lines because it is a bit unlikely that you will need those any time soon. Also the gutsy security are not there because those will give you 404 errors.

Please use these, and then follow the Update Notes for 8.04 as mentioned in an earlier comment.
Good luck!

---

### Post by waspbr on 2009-05-19
sorry for not contributing but I reckon it is going save you a lot of grief to burn a CD and make a new install

---

