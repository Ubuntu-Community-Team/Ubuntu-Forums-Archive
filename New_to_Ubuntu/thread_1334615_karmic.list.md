---
title: "karmic.list"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by JugglinPhil on 2009-11-22
Got this file in my home directory called "karmic.list", is this of any importance or can I delete it?

---

### Post by coffeecat on 2009-11-22
Well - I have neither a 'karmic.list' nor a '.karmic.list' so it clearly doesn't come with a default install. Why not double-click on it to see what's in it, or what it is, and then you could tell us whether it's safe to delete? :wink:

---

### Post by sandyd on 2009-11-22
try renaming it and see if anything happens.
if no, into the garbage it goes.

---

### Post by NoaHall on 2009-11-22
Ehm... As far as I can tell, nvidia-drivers uses it, and chromium.
Besides, it's not doing any harm, it's only going to be a couple of kb's big, so leave it.

---

### Post by JugglinPhil on 2009-11-23
Alright thanks, this is what it says in the file:

## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free #Medibuntu - Ubuntu 9.10 "karmic koala"
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free #Medibuntu (source) - Ubuntu 9.10 "karmic koala"

Doesn't look like anything important to me..

---

### Post by NoaHall on 2009-11-23
> **JugglinPhil said:**
> Alright thanks, this is what it says in the file:

## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free #Medibuntu - Ubuntu 9.10 "karmic koala"
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free #Medibuntu (source) - Ubuntu 9.10 "karmic koala"

Doesn't look like anything important to me..

It's the medibuntu repos. Leave it alone.

---

### Post by JugglinPhil on 2009-11-23
Alright cool thanks, so any idea how I got it?

---

### Post by NoaHall on 2009-11-23
Probably when you installed something like Ubuntu tweak, or automatix. It doesn't matter. Just leave it.

---

### Post by philinux on 2009-11-23
Weird. It should not be in your home directory. How did you install medibuntu. Click the link below.

Open a terminal. Apps>access>term and post back the ouptut of 

```
cat /etc/apt/sources.list
```

---

### Post by JugglinPhil on 2009-11-23
> **philinux said:**
> Weird. It should not be in your home directory. How did you install medibuntu. Click the link below.

Open a terminal. Apps>access>term and post back the ouptut of 

```
cat /etc/apt/sources.list
```
I don't recall installing Medibuntu at all, is it included in some other package?
The output is:

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by philinux on 2009-11-23
Your sources list looks fine. The file in question can safely be deleted. It has no value in your home directory. How it got there.....

Click the medibuntu link and restricted formats links below.

---

### Post by NoaHall on 2009-11-23
> **philinux said:**
> Your sources list looks fine. The file in question can safely be deleted. It has no value in your home directory. How it got there.....

Click the medibuntu link and restricted formats links below.

Don't delete it. A program may be using it. It's not worth deleting anyway.

---

### Post by philinux on 2009-11-23
> **NoaHall said:**
> Don't delete it. A program may be using it. It's not worth deleting anyway.

It might have something to do with chromium. But quite how medibuntu sources would even work in a home folder is a mystery.

[http://www.google.co.uk/search?q=karmic.list&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:official&client=firefox-a](http://www.google.co.uk/search?q=karmic.list&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:official&client=firefox-a)

---

### Post by NoaHall on 2009-11-23
> **philinux said:**
> It might have something to do with chromium. But quite how medibuntu sources would even work in a home folder is a mystery.

[http://www.google.co.uk/search?q=karmic.list&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:official&client=firefox-a](http://www.google.co.uk/search?q=karmic.list&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:official&client=firefox-a)

Have a look at my first post.

Besides, files can be used like that from anywhere. .conf files hidden in your /home/, for example.

---

### Post by JugglinPhil on 2009-11-23
This is slightly confusing, so can anybody tell me for sure if it is safe to delete or not?

---

### Post by NoaHall on 2009-11-23
> **JugglinPhil said:**
> This is slightly confusing, so can anybody tell me for sure if it is safe to delete or not?

Let me put it like this - if you are desperate for space, you don't want to worry about this very small file. If you are worried about security, this file is safe.
**_Leave it alone._**

---

### Post by JugglinPhil on 2009-11-23
> **NoaHall said:**
> Let me put it like this - if you are desperate for space, you don't want to worry about this very small file. If you are worried about security, this file is safe.
**_Leave it alone._**
Okay

---

