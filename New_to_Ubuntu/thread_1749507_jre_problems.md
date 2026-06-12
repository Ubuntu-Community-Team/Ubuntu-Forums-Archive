---
title: "jre problems"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by justjeff on 2011-05-04
I am having problems installing java, searched for it on here and came upon post installing jre, so was following along and did this - You can't install sun java right now because it's not in the Ubuntu repository. So the first thing you need to do is add the Medibuntu repository. Enter this command in a terminal (in a terminal window, use Ctrl+Shift+V for "paste") then after I do that I see this - **edit: I see from lobralleo's post that you may not need the Medibuntu repository if you enable the "Canonical Partners" sources. It might be worth it to skip this command and try that first.
 which I have all ready dont, canonical parterns. 

now when I go back to the or try to go into the  Synaptic Package Manager i get a error about that medibuntu  can someone try to get that un-done and help me get jre going?  I am using the new 11.4 natty and i have been working on this java crap now for over an hour and really shouldnt be this difficult...

---

### Post by wolfen69 on 2011-05-04
Post the output of:
```
gksudo gedit /etc/apt/sources.list
```

Btw, doing:
```
sudo apt-get install ubuntu-restricted-extras
``` will give you java.

---

### Post by justjeff on 2011-05-04
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

---

### Post by oldos2er on 2011-05-04
You've got references to both Lucid and Maverick that shouldn't be there, I've fixed the errors below. Save this file to your hard disk and copy it to /etc/apt/sources.list

```

deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse
```

After you've copied the file, run ```
sudo apt-get update && sudo apt-get install sun-java6-jre
``` If you see any errors, please copy and paste them in full here.

---

### Post by justjeff on 2011-05-04
I'm sorry but I did google it and tried looking on here but you will have to be a little more specific or break it down further for me, I don't know how or what you mean when you say save it to hard disk, how do I save it to (which/any) hard disk, then run -xxxxx, where do I run it?

---

### Post by justjeff on 2011-05-04
I really think I need to start over again and remove the wrong programs and re-try all this.  I got everything to load up right, I think, but I still can not open up the update manger and when I open or try to open the synaptic thing I got this error    

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by oldos2er on 2011-05-05
Did you get the corrected sources.list copied to your system ok?

To fix the medibuntu.list, in a terminal run ```
gksu gedit /etc/apt/sources.list.d/medibuntu.list
``` delete all the text and replace it with 

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free

Save and exit, and run ```
sudo apt-get update
```

---

### Post by justjeff on 2011-05-05
I think/thought I finnaly did, had to keep going back and forth and re=doi9ng it, then I would check the update manger and when it finnally loaded I checked for updated, updated, then went to the synpatic package manger and it  finnaly loaded with no errors.  Now here is where I start getting a little un-sure if I am doing things right, i scrolled down till I found 2 java files marked them, installed them/updated it. closed then went to Sun Java web page and checked, said I was missing pluggins.  Now just opened up a terminal ran your sudo apt-get update, went back to the synpatic manger and now there are 4 files there instead of 2.

  And I have had a couple of freeze's today also where I had to restart machine.

---

