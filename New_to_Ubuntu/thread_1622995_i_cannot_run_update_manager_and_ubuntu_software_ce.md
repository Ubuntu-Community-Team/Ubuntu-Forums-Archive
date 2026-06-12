---
title: "i cannot run update manager and ubuntu software centre!!!!"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by amitpokhrel on 2010-11-16
Hello everyone!!
when I try to open update manager from terminal i get the following warning:

[I]E: Type '“deb' is not known on line 50 in source list /etc/apt/sources.list
E: The list of sources could not be read.
[/I]

And I also cannot open ubuntu software centre. when i click at *ubuntu software centre* nothing happens...
can anyone help??

---

### Post by Hippytaff on 2010-11-16
Hi
 
Can you post your sources.list file for us to have a look
```

cat /etc/apt/sources.list

```
(you might nee sudo!?)

---

### Post by amitpokhrel on 2010-11-16
amit@amit-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick universe
deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick multiverse
deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick-updates multiverse

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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick-security main restricted
deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick-security universe
deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick-security multiverse
&#8220;[http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free&#8221;
amit@amit-laptop:~$

---

### Post by Hippytaff on 2010-11-16
> 
&#8220;[[COLOR=#444444]http://www.sourceslist.eu/repo/ubuntu[/COLOR]]("http://www.sourceslist.eu/repo/ubuntu") lucid main non-free&#8221;

Try updating this last line with gedit or whichever text editor you like to use to
```

[COLOR=red]deb-src [/COLOR]&#8220;[[COLOR=#444444]http://www.sourceslist.eu/repo/ubuntu[/COLOR]]("http://www.sourceslist.eu/repo/ubuntu") lucid main non-free&#8221;

```
save it and try again.
 
EDIT ->
 
if your using Gedit you will probably need to open the file with
```

gksudo gedit /etc/apt/sources.list

```
to be able to edit and save it. It will usually ask for your password :-)

---

### Post by amitpokhrel on 2010-11-16
I replaced it and i tried to update from terminal and I got this message:

*E: The method driver /usr/lib/apt/methods/&#8220;http could not be found.*

---

### Post by amitpokhrel on 2010-11-16
I replaced it and i tried to update from terminal and I got this message:

*E: The method driver /usr/lib/apt/methods/“http could not be found.*

---

### Post by Hippytaff on 2010-11-16
ok...in your source.list file, remove the " from infront of http on the last line :-)

---

### Post by Joeb454 on 2010-11-16
Actually, I think the last line should be ```
deb http://www.sourceslist.eu/repo/ubuntu lucid main non-free
```

deb-src is for the source code downloads, I do believe (i.e. *apt-get source $package*).

---

### Post by amitpokhrel on 2010-11-16
thanks!!! it worked
can u plz tell what does "deb- src "do??

---

### Post by Joeb454 on 2010-11-16
> **amitpokhrel said:**
> thanks!!! it worked

Glad to hear it - you can mark your thread as 'Solved' from thread tools at the top of the page ;)

---

### Post by Hippytaff on 2010-11-16
Excellent :-)

---

