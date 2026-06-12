---
title: "-Error Message-Can someone please help me"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by Otis Spunkmiyer on 2010-04-15
I cannot do an update for my repository's, the following is the error I get and my apt/source/.list

[B]
E: Could not open lock file /var/lib/apt/lists/lock - open (2: No such file or directory)
E: Unable to lock the list directory[/B]
---------------------------------------------------------
# deb cdrom:[Ubuntu-Netbook-Remix 9.10 _Karmic Koala_ - Release i386 (20091028.4)]/ karmic main restricted
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
## deb [http://us.archive.ubuntu.com/ubuntu/karmic-backports](http://us.archive.ubuntu.com/ubuntu/karmic-backports) main restricted universe multiverse                             ## deb-src [http://us.archive.ubuntu.com/ubuntu/karmic-backports](http://us.archive.ubuntu.com/ubuntu/karmic-backports) main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

## deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
## deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by bwhite82 on 2010-04-15
That usually means that you have another package manager working. Make sure that you are using either 'apt-get' via the command line OR Synaptic but never both (at the same time). An automatic update check could be happening in the background as well.

If the problem persists, try killing aptitude:

> sudo killall aptitude

---

### Post by e4uforums on 2010-04-15
What command are you running to try and update the repos?  Did you run it with "sudo" at the beginning of the command?

---

### Post by Otis Spunkmiyer on 2010-04-15
Yes Sudo.
It say's something about will try to use old versions or something similar.

Kill all just said no process's running.

---

### Post by Otis Spunkmiyer on 2010-04-15
This is what the message say's before the error message.[B]
----------
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.[/B]

---

### Post by fallenshadow on 2010-04-15
Its telling you that there is a problem with the internet or "network". 

Could be:

1. There is a problem with your internet connection.

OR

2. There is a problem with the servers connection. (the one you are trying to download from)

---

### Post by Otis Spunkmiyer on 2010-04-15
Connection is fine.  It's saying that the file is missing.

---

### Post by barney385 on 2010-04-15
Open terminal:

sudo apt-get update
...then enter password...

---

### Post by Otis Spunkmiyer on 2010-04-15
I have already, and I get that error code posted in the first post above.

Also in synaptic it says I'm missing this file,

[B]var/lib/apt/lists/partial

[COLOR=Red]Please, Please, Please no running around in circles, OK, if you haven't read the post or really understand what to do then for the love of who ever, don't send me off on a wild goose chase.[/COLOR]
[/B]

---

### Post by barney385 on 2010-04-15
> **Otis Spunkmiyer said:**
> I have already, and I get that error code posted in the first post above.

Also in synaptic it says I'm missing this file,

[B]var/lib/apt/lists/partial

[COLOR=Red]Please, Please, Please no running around in circles, OK, if you haven't read the post or really understand what to do then for the love of who ever, don't send me off on a wild goose chase.[/COLOR]
[/B]

Have you looked through the Community Documentation?


[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

There might be a way to reload synaptic, but I'd wait to hear from the pro's around here before doing that personally.

---

### Post by Otis Spunkmiyer on 2010-04-15
Yes I have done all the steps.  What it keeps telling me is there is no file to update to.  Somehow it got deleted.  Is there a restore that will restore all orignal files, or do I need to re-install the entire OS  ?

---

### Post by philinux on 2010-04-15
> **Otis Spunkmiyer said:**
> Yes I have done all the steps.  What it keeps telling me is there is no file to update to.  Somehow it got deleted.  Is there a restore that will restore all orignal files, or do I need to re-install the entire OS  ?

Dont forget people on here are volunteers and are trying to help.

I just check my files and /var/lib/apt/lists/partial is an empty directory here so if its missing on your system then lets create it.

```
sud mkdir /var/lib/apt/lists/partial
```

Then try to update your machine. Post back any new errors.

I'd be interested to know how it got deleted. ;)

---

### Post by Otis Spunkmiyer on 2010-04-15
I have partial already.
But this is how I have it -   /**var/lib/apt/mirror/partial**

No 'list', and when I do your command it tells me it cannot make that directory.

And I am very well aware of the 'free service here', let's hope it's better then the payed service !

Is there a system restore ?

---

### Post by Otis Spunkmiyer on 2010-04-15
[[COLOR=#D40000]**philinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=353083") 				 				 			
  			Caveat Emptor !
/////////////////////////

Fixed it, I figured out how to delete what I had and make what you have, fired up the update and it worked perfect.  Downloaded and updated 42 items.
Synaptic is all back to normal showing repositories ect.

**Thank You**, for pointing me in the right direction..):P
(I wish I would have come on the forum before I spent $75.00 dollars on my credit card speaking with a Tech,)

---

