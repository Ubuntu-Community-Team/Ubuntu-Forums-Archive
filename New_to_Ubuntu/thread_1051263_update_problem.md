---
title: "update problem"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by cybuss on 2009-01-26
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  main'./binary-amd64/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

i don't know how to fix this problem anyone know a way to fix it
 thanks

---

### Post by taurus on 2009-01-26
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by kingmonkey on 2009-01-26
type:

```

gksudo gedit /etc/apt/sources.list

```

Then hash out the offending cdrom lines.

---

### Post by cybuss on 2009-01-26
deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main'.
deb [http://ppa.launchpad.net/pjbroad/ubuntu](http://ppa.launchpad.net/pjbroad/ubuntu) hardy main

there you go

---

### Post by taurus on 2009-01-26
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line to comment out the cdrom repo.

```

**[COLOR="Blue"]#[/COLOR]**deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted

```
Then scroll down to the second of the last line and remove that line.

```

**[COLOR="Blue"]deb http://archive.ubuntu.com/ubuntu/ hardy main'.[/COLOR]**

```
Save the changes and close down gedit window.  Then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by metallicamike on 2009-01-26
or go to System->Administration->Software Sources and uncheck Cdrom with Ubuntu 8.04 'Hardy Heron'.

---

### Post by cybuss on 2009-01-26
i think it worked, its not saying i have new updates anymore thanks
i need help with graphics card,
its a 7 series nvidia geforce card and i cant get the package i downloaded from nvidia sight to install anyway i can fix that problem?

---

### Post by taurus on 2009-01-26
> **metallicamike said:**
> or go to System->Administration->Software Sources and uncheck Cdrom with Ubuntu 8.04 'Hardy Heron'.

But what happens to the second to the last line since that line is wrong?

---

### Post by taurus on 2009-01-26
> **cybuss said:**
> i think it worked, its not saying i have new updates anymore thanks
i need help with graphics card,
its a 7 series nvidia geforce card and i cant get the package i downloaded from nvidia sight to install anyway i can fix that problem?

Have you looked in System -> Administration -> Hardware Drivers to see if your graphic card is on the list.  If it is, then enable it by installing a driver for it.

---

### Post by cybuss on 2009-01-26
it says NVIDIA accelerated graphics driver (latest cards) enabled in use

---

### Post by taurus on 2009-01-26
> **cybuss said:**
> it says NVIDIA accelerated graphics driver (latest cards) enabled in use

And do you have any problem with your graphic card?

---

### Post by cybuss on 2009-01-26
> **taurus said:**
> And do you have any problem with your graphic card?

it wont let me use extra desktop effects and every time i turn computer off it has me re pick settings and driver again it gets annoying

o and it wont let me change resolution and refresh rate

---

### Post by taurus on 2009-01-26
Can you post a screenshot of the System -> Administration -> Hardware Drivers?  You screenshot program is in Applications -> Accessories -> Take Screenshot.

---

### Post by cybuss on 2009-01-27
> **taurus said:**
> Can you post a screenshot of the System -> Administration -> Hardware Drivers?  You screenshot program is in Applications -> Accessories -> Take Screenshot.

i think that will provide a link
nope how do i get screen shot on here?

---

### Post by cybuss on 2009-01-27
i managed to get it as my profile picture so take a look?[IMG]http://ubuntuforums.org/picture.php?albumid=874&pictureid=2963[/IMG]

---

### Post by taurus on 2009-01-27
And you have to activate the nvidia driver each time you boot?  Did you install Ubuntu on it own partition?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by cybuss on 2009-01-27
[IMG]http://ubuntuforums.org/picture.php?albumid=874&pictureid=2963[/IMG]
i edited last reply of mine and got it on it

---

### Post by cybuss on 2009-01-27
i had vista on here before ubuntu i wanted to keep vista and have ubuntu on here but when i installed ubuntu it removed vista even tho i told it not to so i think its on its partition

any idea how to fix it?

---

