---
title: "what to do if apt-get update breaks?"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by psihokiller4 on 2011-06-05
exactly as title says

```
apt-get update
E: Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
```

same goes for in software sources:
when I try to reload


```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

```

```

    An error occurred

The following details are provided:

  [CODE]

    E: Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
E: Unable to lock the list directory
```
[/CODE]
 
   ```

     An error occurred

The following details are provided:

  [CODE]

    E: Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

```
[/CODE]

---

### Post by drs305 on 2011-06-05
Edited:
You have an error in [s]sources.list[/s] /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list. Open it as root:
```
[s]gksu gedit /etc/apt/sources.list[/s]
```
```
gksu gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
```
The first line won't look correct. You can solve the issue by placing a # symbol at the start of the line and saving the file. You can also delete the entire first line but since we aren't sure of the error I'd just put a # icon for now. If you want specific guidance on what the error is, and whether you need to modify the line or simply delete it, post the contents of /etc/apt/sources.list

---

### Post by psihokiller4 on 2011-06-05
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ lucid main
deb-src http://archive.ubuntu.com/ubuntu/ lucid main #Added by software-properties

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

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://ppa.launchpad.net/pjbroad/ppa/ubuntu lucid main #eternal lands
deb-src http://ppa.launchpad.net/pjbroad/ppa/ubuntu lucid main #eternal lands
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates main #Added by software-properties
```

witch one to #? (uncomment)

---

### Post by drs305 on 2011-06-05
My apologies, it's the first line in: /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list

So the file to edit would be:
```
gksu gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
```

---

### Post by psihokiller4 on 2011-06-05
```
n
b http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main
```

so I do

```
#n
b http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main
```

---

### Post by el_koraco on 2011-06-05
post the output of /etc/apt/sources.list.d

---

### Post by drs305 on 2011-06-05
It should look like this:
> deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main

Added:
If it asks for a key, you can run this command to import it:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0
```

If that fixes things, please mark the thread 'SOLVED' via the 'Thread Tools' link at the top right of the first post. If not, ask away!

---

### Post by psihokiller4 on 2011-06-05
thanks it works now :)


> **el_koraco said:**
> post the output of /etc/apt/sources.list.d

```
linux:/etc/apt/sources.list.d$ ls
adilson-experimental-lucid.list       psyke83-ppa-lucid.list
adilson-experimental-lucid.list.save  psyke83-ppa-lucid.list.save
playonlinux.list                      ubuntu-wine-ppa-lucid.list
playonlinux.list.distUpgrade          ubuntu-wine-ppa-lucid.list.save
playonlinux.list.save
```

---

