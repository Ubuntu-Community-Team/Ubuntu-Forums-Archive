---
title: "what does this mean"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by DarinB on 2009-06-16
i got an update but this is what happens?

Method gave invalid 400 URI Failure messageMethod gave invalid 400 URI Failure message

---

### Post by Johan-Steyn on 2009-06-16
Hi DarinB,

It looks like you have an invalid entry in your /etc/apt/sources.list file.

The updater wants to contact a source in a repository that does not exist or could not be verified.

```
cat /etc/apt/sources.list
```

Clean it up in gedit. That should clear up your update problem.

Regards,

JS

---

### Post by DarinB on 2009-06-16
how do i know which is invalid?
i will post it here?????????
darin@darin-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
darin@darin-desktop:~$

---

### Post by trivialpackets on 2009-06-16
Did you install playdeb?  Here is a link of some things you may want to look into.  In particular, take a look at the /etc/apt/sources.list.d directory as well!  Best of luck!

[http://ubuntuforums.org/showthread.php?t=908126](http://ubuntuforums.org/showthread.php?t=908126)

---

### Post by DarinB on 2009-06-16
what did this do?
sudo rm -rf of /etc/apt/sources.list.d/
it did work? but what is deleted from the sources list
i read further after the delete that it could mess up my dvd but i can play dvd's with vlc. so did i mess things up????

---

### Post by trivialpackets on 2009-06-16
Yeah, well we'll never know, you deleted whatever was in that directory.  Most likely, something you installed created it so that you could keep something up-to-date.  In the future, I'd recommend examining a directory before deleting it, especially with rm -rf /whatever  Glad it's working for you now though!

---

### Post by DarinB on 2009-06-17
any way of recreating it? by doing something at the application level?

---

### Post by Therion on 2009-06-17
Most likely a server was temporarily offline or unreachable for some reason.  It happens.

In my experience, 99% of the time, those errors correct themselves in a day or two or if you just ignore them.

---

### Post by ayenack on 2009-06-17
> **Therion said:**
> Most likely a server was temporarily offline or unreachable for some reason.  It happens.

In my experience, 99% of the time, those errors correct themselves in a day or two or if you just ignore them.

+1

The servers seem to have been a bit erratic lately in the UK so maybe you're having the same probs in US. wait to the evening or early morning and try again.

---

### Post by michy99 on 2009-06-17
> **DarinB said:**
> any way of recreating it? by doing something at the application level?

An update will recreate the lists in /etc/apt/sources.list.d/```
sudo apt-get update
```

---

### Post by DarinB on 2009-06-17
hmm the sudo apt-get update did not recreate the list 
cat /etc/apt/sources.list.d/ yielded this:
darin@darin-desktop:~$ cat/etc/apt/sources.list.d/
bash: cat/etc/apt/sources.list.d/: No such file or directory
darin@darin-desktop:~$

---

### Post by michy99 on 2009-06-17
> **DarinB said:**
> hmm the sudo apt-get update did not recreate the list 
cat /etc/apt/sources.list.d/ yielded this:
darin@darin-desktop:~$ cat/etc/apt/sources.list.d/
bash: cat/etc/apt/sources.list.d/: No such file or directory
darin@darin-desktop:~$

sources.list.d is a directory. To see what is in it, enter```
ls /etc/apt/sources.list.d/
```

---

### Post by ayenack on 2009-06-18
Why are you putting /etc/apt/sources.list.d ?

Surely it should be

**sudo nano /etc/apt/sources.list**

To both view and edit your sources.

---

### Post by Cheesemill on 2009-06-18
> **ayenack said:**
> Why are you putting /etc/apt/sources.list.d ?

Surely it should be

**sudo nano /etc/apt/sources.list**

To both view and edit your sources.

As well as sources.list, you can put individual text files into the sources.list.d directory which also get parsed by apt.

For example if you enable the Medibuntu repos you will notice that it doesn't add anything to your sources.list, instead it adds the medibuntu.list file into the sources.list.d directory.

---

### Post by DarinB on 2009-06-18
this is what i got with sudo nano /etc/...
i can't seem to copy and past what i got but i am getting confused as to what is happening..... i would like find out what the first code i used did and what is going on????? will my programs get updated or not? and what is /etc/apt/sources.list.d vs. /etc/apt/sources.list???

---

### Post by DarinB on 2009-06-18
based on the post for medibuntu should i reinstall the medibuntu source???

---

### Post by ayenack on 2009-06-22
Sorry for the delay in posting back been busy.

You could re-install.

If you want to add medibuntu manually take a look at this. This in theory should solve your update problems if the application is in the medibuntu repo's.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by DarinB on 2009-06-22
thanks got a better server and will wait to see if updates come up in the next week

---

### Post by ayenack on 2009-06-22
I'll check back then. I'll take it as read that updates are working if you don't post back.

---

### Post by Miljet on 2009-06-22
I just took a look at my /etc/apt/sources.list.d/ directory, and it contained two files: medibuntu.list and  medibuntu.list.save.

From that, I would guess that if you add the medibuntu repositories, it will recreate the directory and files.

---

