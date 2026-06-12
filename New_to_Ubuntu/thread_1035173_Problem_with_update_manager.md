---
title: "Problem with update manager"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by itsvan on 2009-01-09
HI, for some reason every time i try to update ubuntu Hardy Heron, i go to the update manager and my computer completely freezes and never gets through downloading the files or much less installing them,,what could i do to fix this issue? and also,,i recently had a problem with effects and resolution,,i managed to fix the effects part but i still dont have many options to increase my resolution, and ideas?? please help!!!!:D

---

### Post by Hospadar on 2009-01-09
Try updating in a terminal and see if it gives you any intersting output

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by itsvan on 2009-01-09
Hi i tried doing that,,and it seemed to be working for a couple of files,,but then i guess it got to one particular file,,and like always it froze me computer and messed everything up,,why is this happening?

---

### Post by moonoo on 2009-01-09
Try and post the sources.list file here.

---

### Post by itsvan on 2009-01-09
How do i post that,,where do i go?

---

### Post by moonoo on 2009-01-09
You can get to it by opening nautilus:

file system -> etc -> apt -> sources.list

open it up with a text editor.

copy n paste :)

It will look something like:

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

---

### Post by itsvan on 2009-01-09
sorry for my ignorance,,but how do i open nautilus,,im a big time noob haha sorryyy!!!

---

### Post by moonoo on 2009-01-09
No worries :)

If you click on 'Places' in the menu bar and select 'Computer' you will get a window open up and there you will have an icon called 'File System'

Hope that helps!

---

### Post by itsvan on 2009-01-09
OK i think i did it right,,,this is the file sources.list




#
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted

# deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015)]/ gutsy main multiverse restricted universe
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015)]/ gutsy main multiverse restricted universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
# deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

# Wine
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main
# deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main





# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by moonoo on 2009-01-09
To explain what you have here is:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse

**deb **
(the type)

**[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) **
(the URI by location)

**hardy **
(the distribution)

**multiverse **
(the component)

You can disable some of these entries by putting a # in font of it.

In a nut shell, you are looking for all of the entries to have the same location (the 'us' part of the URI) with the same distribution.
The components differentiate between the packages available.

To start off with try and comment out the 'cdrom' types (these start with 'deb cdrom')

To comment out line within the sources.list file you will need to open it up using sudo. To do this go to:
Applications -> Accessories -> Terminal

then type:
[FONT="Courier New"]sudo gedit /etc/apt/sources.list[/FONT]

what you are doing here is:

**sudo **
(use the super user user)

**gedit **
(use the basic text editor)
[B]
/etc/apt/sources.list[/B]
(open this file)

comment out one line then save.

Go back to the Terminal and open a New Tab (press Shift+Control+T)

then type:

[FONT="Courier New"]sudo apt-get update[/FONT]

what you are doing here is:

**sudo **
(use the super user user)

**apt-get **
(open apt-get - command line package manager)

**update**
(the update the repositories)

If it fails then you haven't got the right one :)

repeat until you get a full update.

Sorry if this sounds convoluted but going through this process will exercise some skills you could benefit with when coming to ubuntu!
 
Im am sure someone else will suggest an 'easier' way but imagine the sense of satisfaction when you get a full update and you know exactly what the issue was :D

---

### Post by itsvan on 2009-01-09
i think i understand what to do,,the thing is what exactly do i have to comment on the lines? can i have an example? because there are so many i dont want to mess it up

---

### Post by moonoo on 2009-01-09
When you run the update, the apt-get program will process the sources.list file and look for lines which start with 'deb'.

Commenting out a line make the apt-get program skip the line.

For example:

**# apt-get will process this line**
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted

**# apt-get will not process this line because it is commented out.**
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted


To safe guard the sources.list file you could back up the file first.
to do this you could open the Terminal and type:

[FONT="Courier New"]sudo cp /etc/apt/sources.list /etc/apt/sources.list-backup
[/FONT]

This will make a copy (cp) of the file and rename it so if you want to you can restore the sources.list file to its original state by issuing this command in Terminal:

[FONT="Courier New"]sudo cp /etc/apt/sources.list-backup /etc/apt/sources.list
[/FONT]
(basically reversing the first cp statement)

Hope this helps! :D

---

