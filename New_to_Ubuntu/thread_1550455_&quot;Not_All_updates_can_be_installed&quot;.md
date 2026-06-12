---
title: "&quot;Not All updates can be installed&quot;"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by DayLite on 2010-08-11
I don't understand what Update Manager is referring to. When I log on to Ubuntu the Update Manager pops up.

> **Not all Updates can be installed**
             Run a partial upgrade, to install as many updates as possible.

             This can be caused by:
              * A previous upgrade which didn't complete
              * Problems with some of the installed software
              * Inofficial software packages not provided by Ubuntu
              * Normal changes of a pre-release version of Ubuntu

                ** Partial Upgrade**              **Close**
 How can I be sure that the upgrades applies to the software installed in my computer. Is this general for everyone? I don't want to install an update to a program I don't even have.

Why is this called an_ upgrade_ instead of _update_ ? I want to keep my Ubuntu 10.04 and not switch to another version. I know you will tell me to read the description, I don't understand it.

---

### Post by Elfy on 2010-08-11
Never really thought about thw wording to be honest.

It's normal to get updates - you'll only get updates for things you have.

However - don't install updates when there is a partial upgrade - it can cause problems. You can check the repos with the check button or wait for it to do so itself.

---

### Post by DayLite on 2010-08-11
> **forestpiskie said:**
> 
However - don't install updates when there is a partial upgrade - it can cause problems. You can check the repos with the check button or wait for it to do so itself.

Why would they attempt for me to install something that can cause problems? I am gathering that there is no intelligent human behind these 'computer generated' updates.

Very disturbing :(

---

### Post by regala on 2010-08-11
> **DayLite said:**
> Why would they attempt for me to install something that can cause problems? I am gathering that there is no intelligent human behind these 'computer generated' updates.

Very disturbing :(

there is some intelligent human behind these. But the Q/A team sometimes seems on meth :)

---

### Post by DayLite on 2010-08-11
> **regala said:**
> there is some intelligent human behind these. But the Q/A team sometimes seems on meth :)

I will patiently wait for an answer I can understand.:)

---

### Post by stlsaint on 2010-08-11
Are you using just Lucid or are you using something that you have customized and rebuilt yourself? Also please post an attachement containing your sources.list.

---

### Post by Elfy on 2010-08-11
Partial updates don't happen often outside of the development versions, but if for instance application a depended on package b - package a get's an update but package b has not been updated yet - you could see a partial upgrade. If you have got a 3rd party repo - that is not one of the offical ones then you could find a partial where they have updated something that needs a package that ubuntu is not going to update - I would guess this is what stl is alluding to in their post.

If you happen to be using the development version where partials are common - that is meerkat at the moment, then this is in the wrong forum ;)

Might be worth reading one of the stickies from that forum [http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

Do not though follow any of the various other posts in that thread - they are dealing sole;y with the development version of ubuntu - I only post the thread to give you some idea of what partial upgrades are about.

---

### Post by Cavsfan on 2010-08-11
I posted this thread about getting a partial update in Lucid yesterday

[[COLOR=blue]_Partial Upgrade post._[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1549882") It was wanting to remove ffmpeg, which I was not about to do.

And today the partial update had gone away.
I check for updates every day manually and that was the first time since Lucid went final  that I seen a partial offered.

I think the only answer to a "partial upgrade" when given that option is to wait maybe a day or so.
Am I correct?

---

### Post by Elfy on 2010-08-11
I wait or update the repos and see if it has gone - I don't allow partials - unless I am sure I can.

---

### Post by Elmer Fudd on 2010-08-11
> **DayLite said:**
> I don't understand what Update Manager is referring to. When I log on to Ubuntu the Update Manager pops up.

How can I be sure that the upgrades applies to the software installed in my computer. Is this general for everyone? I don't want to install an update to a program I don't even have.

Why is this called an_ upgrade_ instead of _update_ ? I want to keep my Ubuntu 10.04 and not switch to another version. I know you will tell me to read the description, I don't understand it.

Might be a dependancies issue.
It happened once to me.
Fixed it by bypassing the update manager.

```
sudo apt-get check
sudo apt-get update
sudo apt-get upgrade
```

apt-get update can also expose cirtain problems with your sources

I believe that:
"Upgrade" is usually reserved for a major change- i.e.  9.10 to 10.04.
"Update" for fixes/improvements to existing installed software.

You did not accidentally try to load a beta 10.10?

---

### Post by silverglade00 on 2010-08-11
apt-get update will update your local package database with the versions of packages currently in the repos.

apt-get upgrade will update your packages to the latest version of the package in your local package database. 

apt-get dist-upgrade will move you from release to release. For example, from 9.10 to 10.04. It can also be used when doing remote updates. When you are ssh'ed into Ubuntu Server, it will hold back on kernel updates unless you give it a dist-upgrade.

---

### Post by silverglade00 on 2010-08-11
apt-get update will update your local package database with the versions of packages currently in the repos.

apt-get upgrade will update your packages to the latest version of the package in your local package database. 

apt-get dist-upgrade will move you from release to release. For example, from 9.10 to 10.04. It can also be used when doing remote updates. When you are ssh'ed into Ubuntu Server, it will hold back on kernel updates unless you give it a dist-upgrade.

---

### Post by DayLite on 2010-08-11
> **Elmer Fudd said:**
> 
You did not accidentally try to load a beta 10.10?

No I didn't

---

### Post by Cavsfan on 2010-08-11
**apt-get dist-upgrade** is how I have gotten all of my new kernels.

---

### Post by DayLite on 2010-08-11
> **stlsaint said:**
> Are you using just Lucid or are you using something that you have customized and rebuilt yourself? Also please post an attachement containing your sources.list.

I did not customize my Ubuntu 10.04.

I am new to Ubuntu, and do not understand what I need to do to get a list of my sources. Sorry, but you need to treat me as a beginner who hasn't a clue ;)

---

### Post by Cavsfan on 2010-08-11
Open up a terminal Applications > Accessories > terminal and 
enter **gksudo gedit /etc/apt/sources.list**

and copy all of that file that opens up and paste in here, but select it all and then 
wrap CODE around the text with the # button up at the top right.

---

### Post by Cavsfan on 2010-08-11
Also, have you tried it today? Mine showed a partial update yesterday, but today it is fine.

---

### Post by DayLite on 2010-08-11
I just updated from Update Manager, then I clicked on "**check**"( the button next to install).
A pop up screen with this information came up:

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by DayLite on 2010-08-11
> **Cavsfan said:**
> Open up a terminal Applications > Accessories > terminal and 
enter **gksudo gedit /etc/apt/sources.list**

and copy all of that file that opens up and paste in here, but select it all and then 
wrap CODE around the text with the # button up at the top right.

I didn't understand your instruction >  but select it all and then 
wrap CODE around the text with the # button up at the top right. So I just pasted everything.:(

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

---

### Post by Cavsfan on 2010-08-11
Just noticed your other post.
Try this first, open terminal and enter all of this: ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv A040830F7FAC5991  | sudo apt-get update
```Then open update manager and see if it still gets an error.

If it does Try this:
Open terminal and enter this:
[B]sudo apt-get update

[/B]and then enter this:
**sudo apt-get upgrade** and paste the results here.
[COLOR=Blue]Only the output of this 2nd command please.
[/COLOR] 
If you look up at the top right while you are entering text in your response. 
You will see a **#** sign on a button and that is what I meant.
If you highlight all of the text when there is a lot and then click that **#** button it will do this:

```
This is an example of the CODE command in a forum.
```It's not a real big deal, but it just makes it smaller and easier to peruse.

---

### Post by DayLite on 2010-08-11
> **Cavsfan said:**
> 
If you look up at the top right while you are entering text in your response. 
You will see a **#** sign on a button and that is what I meant.
If you highlight all of the text when there is a lot and then click that **#** button it will do this:

```
This is an example of the CODE command in a forum.
```It's not a real big deal, but it just makes it smaller and easier to peruse.

Thank you for helping me to learn :)

---

### Post by DayLite on 2010-08-11
I just tried **Update Manager**.

> System clean, no updates availableSo I guess it was all resolved:D

---

### Post by Cavsfan on 2010-08-12
> **DayLite said:**
> Thank you for helping me to learn :)

You are very welcome! This is what is so great about Ubuntu - there are always people willing to help.

> **DayLite said:**
> I just tried **Update Manager**.

So I guess it was all resolved:D

And I am glad you got your problem taken care of! :D

---

### Post by chrisgianti on 2012-06-03
Hi. I'm having a similar problem. I'm not sure how to fix it, but when I do the sudo apt-get update, here are the problem areas. I don't know why they came into being.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                  
  
Err [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
  
Err [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb InRelease  
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/InRelease](http://archive.canonical.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/InRelease](http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead.When I run the GUI update manager, I get this

Failed to fetch [http://hacktolive.org/repo/archive/pool/main/g/getdeb-repository/getdeb-repository_0.1-1~getdeb1-hacktolive1_all.deb]("http://hacktolive.org/repo/archive/pool/main/g/getdeb-repository/getdeb-repository_0.1-1%7Egetdeb1-hacktolive1_all.deb") Size mismatch

#Then this one is from the update manager...I installed super ubuntu 11.04, 64 bit.
Failed to fetch [http://hacktolive.org/repo/archive/pool/main/g/getdeb-repository/getdeb-repository_0.1-1~getdeb1-hacktolive1_all.deb]("http://hacktolive.org/repo/archive/pool/main/g/getdeb-repository/getdeb-repository_0.1-1%7Egetdeb1-hacktolive1_all.deb") Size mismatch

#If I can eliminate these problems permanently by using some sort of disk, I can create one. But when I tried booting from a disk, it didn't give a find & fix errors option.

---

### Post by Cavsfan on 2012-06-03
> **chrisgianti said:**
> Hi. I'm having a similar problem. I'm not sure how to fix it, but when I do the sudo apt-get update, here are the problem areas. I don't know why they came into being.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                  
  
Err [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
  
Err [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb InRelease  
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/InRelease](http://archive.canonical.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/InRelease](http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead.When I run the GUI update manager, I get this

Failed to fetch [http://hacktolive.org/repo/archive/pool/main/g/getdeb-repository/getdeb-repository_0.1-1~getdeb1-hacktolive1_all.deb]("http://hacktolive.org/repo/archive/pool/main/g/getdeb-repository/getdeb-repository_0.1-1%7Egetdeb1-hacktolive1_all.deb") Size mismatch

#Then this one is from the update manager...I installed super ubuntu 11.04, 64 bit.
Failed to fetch [http://hacktolive.org/repo/archive/pool/main/g/getdeb-repository/getdeb-repository_0.1-1~getdeb1-hacktolive1_all.deb]("http://hacktolive.org/repo/archive/pool/main/g/getdeb-repository/getdeb-repository_0.1-1%7Egetdeb1-hacktolive1_all.deb") Size mismatch

#If I can eliminate these problems permanently by using some sort of disk, I can create one. But when I tried booting from a disk, it didn't give a find & fix errors option.

Not sure you should be posting on this solved thread.
From what I can see your sources are mixed: I see natty and oneiric too.
Edit your software sources and make sure they all are the version of Ubuntu you are on.
These 2 command should do it:
```
gksu gedit /etc/apt/sources.list
gksu gedit /etc/apt/sources.list.d/medibuntu.list
```Then try updating again.

---

### Post by lisati on 2012-06-03
Old thread closed.

A lot can change in two years, and advice in older threads sometimes gets outdated. If you are having a similar issue to one described in a thread that hasn't been active for over a year, it's OK to start a new thread with a link back to the older thread if necessary.

---

