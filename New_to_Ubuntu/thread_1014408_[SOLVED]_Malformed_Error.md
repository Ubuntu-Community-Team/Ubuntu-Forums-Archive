---
title: "[SOLVED] Malformed Error"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by shadowlands on 2008-12-17
Hello

I am not sure what I did wrong while attempting to add features to my computer.  Can some one offer any suggestion on correcting the fellowing error?

Thanks!! in advance for your help.!
E: Malformed line 51 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by taurus on 2008-12-17
There is something wrong with line 51 in /etc/apt/sources.list.  So, you need to either correct it or remove it.

```
gksudo gedit /etc/apt/sources.list
```
If not sure, just post your /etc/apt/sources.list here then.

---

### Post by iaculallad on 2008-12-17
The only way to solve that problem is for you to post the content of your sources.list file:

```
cat /etc/apt/sources.list
```

So we could correct that line.

---

### Post by shadowlands on 2008-12-17
> **iaculallad said:**
> The only way to solve that problem is for you to post the content of your sources.list file:

```
cat /etc/apt/sources.list
```

So we could correct that line.

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy main restricted
deb-src [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy-updates main restricted
deb-src [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy universe
deb [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy multiverse
deb [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy-security main restricted
deb-src [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy-security universe
deb [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy-security multiverse
deb [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) hardy
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) hardy/

---

### Post by iaculallad on 2008-12-17
From your terminal:

```
gksudo gedit /etc/apt/sources.list
```

and comment the last two lines of the file (those lines seems to be the problem):

> deb [http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu](http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu) hardy
deb [http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu](http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu) hardy/

to

> #deb [http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu](http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu) hardy
#deb [http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu](http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu) hardy/


Save and Close the file. Still on the terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by taurus on 2008-12-17
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line to comment it out so it won't ask you to insert a CD into a drive.

```

**[COLOR="Blue"]#[/COLOR]**deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted

```
Then, move all the way down to the end of the file and delete the last two lines.

```

deb http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu hardy
deb http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu hardy/ 

```
Save it and close down gedit editing window.  Now run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by shadowlands on 2008-12-17
):P):P):P Thanks and may you get everything on your wish. list> **iaculallad said:**
> From your terminal:

```
gksudo gedit /etc/apt/sources.list
```

and comment the last two lines of the file (those lines seems to be the problem):



to



Save and Close the file. Still on the terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Miljet on 2008-12-17
Don't know about you guys but I usually advise a new user to make a backup of a system file before changing it.

---

### Post by iaculallad on 2008-12-17
> **Miljet said:**
> Don't know about you guys but I usually advise a new user to make a backup of a system file before changing it.

There's no need to, we had advised the OP to use the gedit utility, which automatically created the sources.list~ file as a backup when edited and saved.

To check if it exist (sources.list~), you could do:

```
ls /etc/apt
```

EDIT:

You could always issue the command **sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup** if you opt to use the terminal-based-command vim or pico instead of the GUI-based gedit editor.

---

