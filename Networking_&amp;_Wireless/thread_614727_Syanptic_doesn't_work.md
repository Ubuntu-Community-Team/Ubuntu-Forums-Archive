---
title: "Syanptic doesn't work"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by UnBr34KaBl3 on 2007-11-16
Thanks to some really nice people in this forum my wireless connection now works:D
But synaptic doesn't or the add remove programs thing. I read something about deleting the "lock file" to make sudo apt-get work. Can that be it? I cant delete it if its what has to be done. I also read that I should log in as root to to it. I searched the internet for info how to do it. I found it and changed it in the terminal. But when i tried to log in  it said i cannot log in from this screen.

---

### Post by unoodles on 2007-11-16
First copy the lock file to your home folder just in case.

Then type "gksu nautilus".

BE VERY CAREFUL.

---

### Post by UnBr34KaBl3 on 2007-11-16
It didn't work, Ubuntu just created a new file called lock.

---

### Post by bapoumba on 2007-11-16
Please close all package managers (synaptic, adept etc.), only one can run at a time.
Do you have an error to:
```
sudo aptitude update
```

If the lock is still on:
```
sudo rm /var/lib/dpkg/lock
```

---

### Post by UnBr34KaBl3 on 2007-11-16
This comes up.

alexander@alexander-desktop:~$ sudo aptitude update
[sudo] password for alexander:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-sv_SE
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-sv_SE
Läser paketlistor... Färdig ( that should mean about: Reading Packetlists...Done)
alexander@alexander-desktop:~$

When i try to install xmms

alexander@alexander-desktop:~$ sudo apt-get install xmms
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
E: Kunde inte hitta paketet xmms (coludn't find the packet xmms)
alexander@alexander-desktop:~$

---

### Post by bapoumba on 2007-11-16
Please post your sources.list file:
```
cat /etc/apt/sources.list
```

Does not look to me you have a problem with the lock file.

---

### Post by UnBr34KaBl3 on 2007-11-16
It doesnt look good:(

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

What do you think the problem can be? Can it be a setting in the router? A setting in the computer?

---

### Post by bapoumba on 2007-11-16
I can browse the .se repositories, so you should be able to make it work.
All the lines starting with **deb** tell the package manager where to look for repositories. You can see that all the lines are "commented", starting with a **#**. The package manager will ignore them.
So you need to remove these #.

First, make a copy of the file:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_bak
```

Then edit the file. You can use any text editor, and I like nano, a small text editor working from the terminal:
```
sudo nano /etc/apt/sources.list
```

[COLOR="Green"]Comment the cdrom[/COLOR] line (the first one, you do not need it) [COLOR="Green"]adding[/COLOR] a **#** at the beginning, and [COLOR="Red"]uncomment[/COLOR] all the other ones [COLOR="Red"]starting with deb[/COLOR], [COLOR="Red"]removing[/COLOR] the **#**.

Save the file with CTRL-O (same name, hit enter)
Exit nano with CTRL-X

Reload the file:
```
sudo aptitude update
```
And please paste the error if you have any.
Paste the sources.list file again, if you have an error:
```
cat /etc/apt/sources.list
```

---

### Post by UnBr34KaBl3 on 2007-11-16
Thank you everything works perfectly now!:)

Just one more question. I choose to install in Swedish when i installed but it's half English half Swedish now... How do i make it all Swedish??

EDIT: I got an error while upgrading, I couldn't download 3 updates.

---

### Post by bapoumba on 2007-11-17
You're welcome :)

For the unfinished upgrade:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
And please paste the error regarding the packages that fail to upgrade.

For language, there should be a "Language Support" menu in "System". Please check that everything is correct. Attached is a screenshot from xubuntu, but should be similar for GNOME. You have to have your preferred language checked AND selected.

---

### Post by UnBr34KaBl3 on 2007-11-17
I don't know what happened but it worked to upgrade now.:) I was just going to get the error message but it upgraded instead.

When I opened the language window it just downloaded everything automaticly so that worked out. Everything works now. Thank you!!

---

### Post by bapoumba on 2007-11-18
Glad to see you got it to work :)
The dist-upgrade is usually able to upgrade packages that a regular upgrade cannot (but is less conservative).

---

