---
title: "Karmic fresh install going good untill sopcast now error in terminal"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by MeTylerDurden on 2009-12-31
I tried to install sopcast from the terminal as described in the ubuntu guide but did not install and now I get error in the terminal.. I have a couple screen shots,  everything with the install went very smooth till now and I don't want to make a mistake.

---

### Post by MeTylerDurden on 2009-12-31
Here is a better snapshot of an error when going to open update manager..

---

### Post by Temposs on 2009-12-31
I believe you edited your Software Sources with an invalid line. You're not supposed to put the install command in your Software Sources. Go to System->Administration->Software Sources->Third-Party Software and show a screenshot there.

If that doesn't work, show the contents of your /etc/apt/sources.list file.

---

### Post by MeTylerDurden on 2009-12-31
thanks, here you go..

---

### Post by Temposs on 2009-12-31
OK, you need to show the contents of /etc/apt/sources.list

---

### Post by MeTylerDurden on 2009-12-31
I cannot run synaptic package manager or update manager here is a screenshot of your command run in the terminal.. (my house is cold, ubuntu is warm, sunshine of the human race)  a Haiku by me , my first one

---

### Post by Temposs on 2009-12-31
Do this command:

```
sudo gedit /etc/apt/sources.list
```

It will bring up a text editor with the contents of the file.

---

### Post by MeTylerDurden on 2009-12-31
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic main restricted
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-updates main restricted
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic universe
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic universe
deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-updates universe
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic multiverse
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic multiverse
deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-updates multiverse
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-updates multiverse

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

deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-security main restricted
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-security main restricted
deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-security universe
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-security universe
deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-security multiverse
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-security multiverse
deb [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu) karmic main
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CD30EE56 


 echo "deb [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu) `lsb_release -cs` main"
echo "deb [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu) `lsb_release -cs` main"
sudo tee -a /etc/apt/sources.list
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CD30EE56

---

### Post by Temposs on 2009-12-31
You have three lines in that file that start with "sudo". Remove those lines from the file, and save the file. Then try running update manager again.

---

### Post by Temposs on 2009-12-31
Oh bugger, remove those two lines that start with "echo" as well. Just that whole last part of the file starting with the first "sudo" line.

---

### Post by MeTylerDurden on 2009-12-31
Update manager is working percectly (except for this-screenshot provided), I removed as lines as you requested and a couple more lines from the bottom here is the result :# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic main restricted
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-updates main restricted
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic universe
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic universe
deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-updates universe
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic multiverse
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic multiverse
deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-updates multiverse
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-updates multiverse

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

deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-security main restricted
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-security main restricted
deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-security universe
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-security universe
deb [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-security multiverse
deb-src [http://ubuntu.securedservers.com/](http://ubuntu.securedservers.com/) karmic-security multiverse
deb [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu) karmic main

---

### Post by Temposs on 2009-12-31
Remove the last line from your sources.list

---

### Post by bilalakhtar on 2009-12-31
The easiest way to solve this problem is:-
1) Remove the last 5 lines from the file which start with echo and sudo.
2) Add the ppa by running these command in the terminal:-
```
sudo apt-get update
sudo add-apt-repository ppa:jason-scheunemann/ppa
```
Cheers:popcorn::lolflag:

---

### Post by MeTylerDurden on 2009-12-31
> **Temposs said:**
> Remove the last line from your sources.list


All is back to where it should be , many thanks. Sopcast I thought would be nice to watch some tv shows-

---

