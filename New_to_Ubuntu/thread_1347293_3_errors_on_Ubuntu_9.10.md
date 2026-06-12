---
title: "3 errors on Ubuntu 9.10?"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by Zach_Bailey on 2009-12-06
[SIZE=3]I cant remember what i was trying to install when this popped up. Now i cant install anything or open up package manager with out alerts and now sound won't work. They say this-

E: Type 'h' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/SIZE]

[SIZE=3]If anyone could help me I'm new.[/SIZE]

---

### Post by nwadams on 2009-12-06
hi

could you post your /etc/apt/sources.list file for us to see if something got screwed up?

thanks and best of luck

---

### Post by Zach_Bailey on 2009-12-06
its blank

---

### Post by nwadams on 2009-12-06
that is probably the problem. If you go to system --> administration -> software sources, are the catagories (main, universe, restricted, multiverse) checked? (the check boxes)

---

### Post by Zach_Bailey on 2009-12-06
Yeah they are all checked

---

### Post by nwadams on 2009-12-06
interesting...sorry I don't know how to fix it.

To anyone else who reads this:
Zack needs to restore his sources.list file, any simple way to do that, or shoudl we just send him one of ours to copy in.

---

### Post by Zach_Bailey on 2009-12-06
Its all right thank you for the help

---

### Post by mikewhatever on 2009-12-06
Try picking some server in the Software Sources window, then hit reload.

---

### Post by Zach_Bailey on 2009-12-06
E: Type 'h' is not known on line 1 in source list /etc/apt/sources.list
E: Unable to lock the list directory
 A window said this

---

### Post by JBAlaska on 2009-12-06
If you get that error you must have something in your sources.list

Try this in a terminal:
```
gksu gedit /etc/apt/sources.list
```

Post the text here or simply comment out line 1, add this at the start of the first line without this character:
```
#
```

---

### Post by Zach_Bailey on 2009-12-06
there is nothing there

---

### Post by Zach_Bailey on 2009-12-06
Found it

h# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse

---

### Post by JBAlaska on 2009-12-06
Make this:
```
h# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
```

Look like this:
```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
```

---

### Post by Zach_Bailey on 2009-12-06
Still the same errors

---

### Post by JBAlaska on 2009-12-06
Open a terminal after saving the above change and do:
```
sudo apt-get update
```

---

### Post by Zach_Bailey on 2009-12-06
hive@Hive:~$ sudo apt-get update
[sudo] password for hive: 
E: Type 'h' is not known on line 1 in source list /etc/apt/sources.list

---

### Post by Zach_Bailey on 2009-12-06
if i delete the "h" in the first line will that work?

---

### Post by Zach_Bailey on 2009-12-06
That did it. thank you all so much i didnt mean to be a burden over something simple. Thanks again

---

### Post by JBAlaska on 2009-12-06
[COLOR="Blue"]Edit: no problem, glad you got it fixed![/COLOR]

---

### Post by 3rdalbum on 2009-12-06
In future, don't edit the /etc/apt/sources.list file. You can manage your repositories by going to System > Administration > Software Sources; it's much safer because it doesn't let you put invalid data in. Anything you can do by manually editing the file can be done from Software Sources.

---

