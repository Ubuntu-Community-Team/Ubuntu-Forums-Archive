---
title: "Software sources problem"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by clive littlewood on 2009-01-20
Hi All

I have just updated and when finished used the check button.

It informed me that i did not have the appropriate key for the following.


 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release:


NO_PUBKEY 632D16BB0C713DA6


I have tried disableing any of the third party software sources with "launchpad.net" but still have the problem.


Any ideas  !!!!!!!!!        :D


Clive

---

### Post by hyper_ch on 2009-01-20
what's the output of:

```

cat /etc/apt/sources.list

```?

---

### Post by clive littlewood on 2009-01-20
Thanks


```
clive@clive-laptop:~$ cat /etc/apt/sources.list
# deb http://repository.cairo-dock.org/ubuntu intrepid cairo-dock
# deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu intrepid main # deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ftp.oleane.net/ubuntu/ intrepid main restricted
deb-src http://ftp.oleane.net/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.oleane.net/ubuntu/ intrepid-updates main restricted
deb-src http://ftp.oleane.net/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp.oleane.net/ubuntu/ intrepid universe
deb-src http://ftp.oleane.net/ubuntu/ intrepid universe
deb http://ftp.oleane.net/ubuntu/ intrepid-updates universe
deb-src http://ftp.oleane.net/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.oleane.net/ubuntu/ intrepid multiverse
deb-src http://ftp.oleane.net/ubuntu/ intrepid multiverse
deb http://ftp.oleane.net/ubuntu/ intrepid-updates multiverse
deb-src http://ftp.oleane.net/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://es.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://ftp.oleane.net/ubuntu/ intrepid-security main restricted
deb-src http://ftp.oleane.net/ubuntu/ intrepid-security main restricted
deb http://ftp.oleane.net/ubuntu/ intrepid-security universe
deb-src http://ftp.oleane.net/ubuntu/ intrepid-security universe
deb http://ftp.oleane.net/ubuntu/ intrepid-security multiverse
deb-src http://ftp.oleane.net/ubuntu/ intrepid-security multiverse
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
# deb http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
deb http://deb.opera.com/opera/ lenny non-free #Opera
deb http://ppa.launchpad.net/fta/ubuntu intrepid main #Firefox
clive@clive-laptop:~$ 

```

---

### Post by ugm6hr on 2009-01-20
There are 2 lines that refer to launchpad PPAs in your sources.list.

# them out if you want to remove the error.

---

### Post by clive littlewood on 2009-01-20
Thanks

Do you mean i should "untick" the entries ????

Thanks again

Clive

---

### Post by hyper_ch on 2009-01-20
there are no gpg keys for launchpad repos... either use them without gpg keys or dont :)

---

### Post by ugm6hr on 2009-01-20
> **clive littlewood said:**
> Thanks

Do you mean i should "untick" the entries ????

Thanks again

Clive

You can do that, or edit the text file directly.

```
gksudo gedit /etc/apt/sources.list
```

Add a "#" (without the ") at the start of every line referring to a launchpad PPA, and then save.

Then try again.

---

### Post by ugm6hr on 2009-01-20
> **hyper_ch said:**
> there are no gpg keys for launchpad repos... either use them without gpg keys or dont :)

Good point.  I was assuming you wanted to remove all unsigned repos.

Of course, you can just use them as they are (i.e. unsigned).  You will get the same warning whenever you try to install / update anything from there.

---

### Post by clive littlewood on 2009-01-20
Thanks both of you

I now understand what is happening and will mark as solved    :D


Thanks again


Clive

---

### Post by shawe_ewahs on 2009-01-21
> **ugm6hr said:**
> You can do that, or edit the text file directly.

```
gksudo gedit /etc/apt/sources.list
```

Add a "#" (without the ") at the start of every line referring to a launchpad PPA, and then save.

Then try again.

Comment the repos that are returning advises isn't the solution, they work, but anything is changed, because after it hasn't return this error/advise. This is a way to ignore it.

---

### Post by ugm6hr on 2009-01-21
> **shawe_ewahs said:**
> Comment the repos that are returning advises isn't the solution, they work, but anything is changed, because after it hasn't return this error/advise. This is a way to ignore it.

Eh?

---

### Post by ITC on 2009-01-22
> Important: Over the next few weeks, Launchpad is generating keys for each PPA. While this is happening, one of two things will happen when you install software from a PPA:

    * Ubuntu will warn you that the package is unsigned.
    * Ubuntu will tell you that it can't verify the key used to sign the package. Visit the PPA's overview page to confirm the key's fingerprint and then continue if you are happy that the package is correctly signed. 
[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories")

Had the same error.
But on 8.04.

The source in my software source list missing the key was:
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main

I used this key [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x632D16BB0C713DA6]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x632D16BB0C713DA6")

[https://launchpad.net/~fta/+archive]("https://launchpad.net/~fta/+archive")

Hope this can solve your error also.

---

### Post by clive littlewood on 2009-01-22
Hi ITC and Thanks

I am suprised that more people have not had this problem !!!

Anyway that appears to be the answer.

Thanks again

Clive

Edit: It appears that the solved button has gone for the moment

---

### Post by blackgr on 2009-01-23
I made this small bash script. it will check you intrepid system for all launchpad sources and will download and install the keys for you!

Who ever wants this for Hardy. Just edit the script and change intrepid to hardy

edit:
you have to run this with sudo

---

### Post by clive littlewood on 2009-01-24
Hi

Thanks Blackgr i am not on my machine at the moment but try your script later.

Thanks again

Clive

---

### Post by clive littlewood on 2009-01-24
Hi blackgr

Used your script and it worked a treat. !!!!!!!!!!!        :D

I'm not sure how you did it, but thanks a million.

Regards

Clive

---

### Post by blackgr on 2009-01-24
thnx ^^ .After you update, you can remove curl
```

sudo apt-get remove curl
```

its a program needed for my script

---

### Post by clive littlewood on 2009-01-24
Hi

Have removed it, also i have kept the zip for any future probs.

Clive

---

