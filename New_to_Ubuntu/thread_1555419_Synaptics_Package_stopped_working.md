---
title: "Synaptics Package stopped working"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by Bunnies on 2010-08-18
> E: Type 'sudo' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I keep getting this error.  Anybody had this problem before?

---

### Post by VastOne on 2010-08-18
> **Bunnies said:**
> I keep getting this error.  Anybody had this problem before?

What are you running prior to getting this error?

---

### Post by Bunnies on 2010-08-18
> $ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

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
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse


sudo apt-get update && sudo apt-get install emesene


I posted 'cat /etc/apt/sources.list' in my terminal and this is what came up.

I was running emesene, and I think this caused the problem.

---

### Post by VastOne on 2010-08-18
> **Bunnies said:**
> I posted 'cat /etc/apt/sources.list' in my terminal and this is what came up.

I was running emesene, and I think this caused the problem.

OK, the second sudo is not needed

This 

```
sudo apt-get update && sudo apt-get install emesene 
```

should be this

```
sudo apt-get update && apt-get install emesene 
```

---

### Post by Bunnies on 2010-08-18
I typed what you had in the terminal and got this:

> E: Type 'sudo' is not known on line 56 in source list /etc/apt/sources.list

The error for synaptics is still there, as well. @_@

---

### Post by VastOne on 2010-08-18
> **Bunnies said:**
> I typed what you had in the terminal and got this:



The error for synaptics is still there, as well. @_@

that line 

```
sudo apt-get update && sudo apt-get install emesene 
```

Should not be in the sources list at all, how did it get there?

Comment it out by putting a # in front of it

---

### Post by Bunnies on 2010-08-18
It's making no difference.  I'm unsure how it got there.

---

### Post by VastOne on 2010-08-18
> **Bunnies said:**
> It's making no difference.  I'm unsure how it got there.

You edit the /etc/apt/sources.list and took that line out and then run just 

sudo apt-get update from terminal and tell me what happens.

---

### Post by Bunnies on 2010-08-18
I'm sorry for being a bother, but I don't know how to edit it.  I tried just typing it in the terminal and got this:
> 
$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied

---

### Post by VastOne on 2010-08-18
> **Bunnies said:**
> I'm sorry for being a bother, but I don't know how to edit it.  I tried just typing it in the terminal and got this:

in terminal

```
sudo gedit /etc/apt/sources.list
```

put in your password

Go to the bottom and remove the line

sudo apt-get update && sudo apt-get install emesene

Then save the file

then from terminal run 

```
sudo apt-get update
```

and let me know what happens

---

### Post by Bunnies on 2010-08-18
:D :D :D :D

^I spam you with emoticons is what happens.

The problem is fixed, Thank you.

---

### Post by VastOne on 2010-08-18
> **Bunnies said:**
> :D :D :D :D

^I spam you with emoticons is what happens.

The problem is fixed, Thank you.

Now to install emense you put this in terminal

```
sudo apt-get update && apt-get install emesene
```

and it will install

And you are very welcome!!!

---

