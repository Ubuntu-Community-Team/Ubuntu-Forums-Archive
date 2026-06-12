---
title: "Could Not Initialize the Package Information"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by miker1993 on 2011-02-12
Hey guys,

              I am very new to Linux and thought I would give it a go on my other Toshiba laptop, and I am now loving it (Ubuntu 10.10). Unfortunately, I am now unable to run the update manager as I believe I have made an error whilst installing the 'Automatix2' which I don't even want any more using the following site:

*_[http://www.debianadmin.com/install-automatix2-in-ubuntukubuntuxubuntu.html](http://www.debianadmin.com/install-automatix2-in-ubuntukubuntuxubuntu.html) _*

When I attempt to run the update manager, it states the following error message:

[B]Could not initialize the package information
An unresolvable problem occurred while initialising the package information.
Please report this bug against the 'update-manager' package and include the following error message
'E:Type 'echo' is not known on line 64 in source list /etc/apt/sources.list'[/B]

In addition to this, there is a big 'no entry' looking red circle with a white, horizontal line going through the centre of it next to my Wifi connection bar on the top right corner.

Any comments on how I can resolve this issue would be great thanks :)
would be great thanks :)

---

### Post by janpol on 2011-02-12
Open your /etc/apt/sources.list file with a text editor, and take a look at line 64. Maybe Automatix2 modified it in a way that the Update Manager can't understand. 

If you can't figure out what's wrong, please post here (using the CODE tag) the contents of your /etc/apt/sources.list file. 

Here is a sample sources.list:

```
#deb cdrom:[Ubuntu 10.10S _Maverick Meerkat_ - Release i386]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
```

By the way, in 10.10 you have the Software Center, you don't need something like Automatix2.

Regards

---

### Post by janpol on 2011-02-12
By looking at the error your are reporting, and the instructions you followed, it's likely that you have something like this on line 64 of your sources.list file:

```
echo &#8220;deb http://www.getautomatix.com/apt edgy main&#8221;
```

If you do, leave it like this (delete the word echo and the double quotes):

```
deb http://www.getautomatix.com/apt edgy main
```

After that, if everything is fine now, I suggest you uninstall Automatix2 (if you actually managed to install it), remove the above line completely from sources.list and run:

```
sudo apt-get update
```

Good Luck

---

### Post by philinux on 2011-02-12
> **miker1993 said:**
> Hey guys,

              I am very new to Linux and thought I would give it a go on my other Toshiba laptop, and I am now loving it (Ubuntu 10.10). Unfortunately, I am now unable to run the update manager as I believe I have made an error whilst installing the 'Automatix2' which I don't even want any more using the following site:

*_[http://www.debianadmin.com/install-automatix2-in-ubuntukubuntuxubuntu.html](http://www.debianadmin.com/install-automatix2-in-ubuntukubuntuxubuntu.html) _*

When I attempt to run the update manager, it states the following error message:

[B]Could not initialize the package information
An unresolvable problem occurred while initialising the package information.
Please report this bug against the 'update-manager' package and include the following error message
'E:Type 'echo' is not known on line 64 in source list /etc/apt/sources.list'[/B]

In addition to this, there is a big 'no entry' looking red circle with a white, horizontal line going through the centre of it next to my Wifi connection bar on the top right corner.

Any comments on how I can resolve this issue would be great thanks :)
would be great thanks :)

From the webpage you linked.
> For Edgy Eft Users

Installing on Ubuntu 6.10,Kubuntu 6.10,Xubuntu 6.10 i386,amd64 
We are now on version 10.10 and automatix has gone the way of the dodo.

Stick to the software centre or synaptic package manager and you will experience no trouble at all.

---

### Post by miker1993 on 2011-02-12
Thank you Janpol!!! Ah, something so simple and I just fail at it all. Haha. Thank you greatly. Also managed to completely (hopefully) uninstall it. Update manager appears to be working fine and everything is going smoothly :)

___

Philinux, I wasn't thinking straight and just wanted to attempt to install the windows program Guitar Pro 5, but now that I am using Tux (the Linux equivalent) I'm getting used to it. Although I don't like writing music into that. I'll just use my other computer for that thanks anyways :)

---

### Post by philinux on 2011-02-13
I believe guitar pro 5 works under Wine with some limitations.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3782&iTestingId=1821](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3782&iTestingId=1821)

---

### Post by rbduck13 on 2011-03-16
Hello im new to the forum but I am having the same problem. This is what it is saying 

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '.net/tualatrix/ppa/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-maverick.list'

---

### Post by plucky on 2011-03-18
> Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '.net/tualatrix/ppa/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-maverick.list' 


Open a terminal (Applications > Accessories > Terminal) and post output of ```
cat /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
```

Or you can open Software Sources and un-tick the Tualatrix PPA,but then you won't be able to update from that source.


Good Luck

---

### Post by thiefzer0 on 2011-03-21
Hi everyone!  I am new here as well.  I briefly tried Ubuntu on my netbook about a year ago but it wasn;t fully supported yet so I gave up (got overly confused trying to enable some "hacks" for my atheros wifi card) and uninstalled.

Anyways, I installed Ubuntu 10.10 Netbook Remix last night, everything installed fine.  I set up a 6 GB parition to play with, and of course a swap partition.  I was trying to install java (not realizing it was preinstalled) and the minecraft (a game) client last night and some tutorial had me doing alot of terminal commands i am not yet familar with.  Apparently i broke something because now when I try to open synaptic package manager or run the updates i get the same error that reads:

Could Not Resolve the Packaged Information

An unresolvable problem occurred while initializing the package information.  

Please report this bug against the 'update-manager' package and include the following error message:

E:Malformed line 61 in source list /etc/apt/sources.list (dist parse)'.


I followed some other instructions and managed to use the sudo command in terminal to use gedit to open the source file, enabled numbered lines and found line 61.  I don't know but it looked perfectly fine to me.  Should I attach the file so you guys can tell me whats; wrong?  I will go ahead and post several lines including line 61 so you can see what's wrong.  I do however distinctly remember in the terminal doing something involving canonical, which happens to be in the line(s?) throwing error messages.  I will paste them in now.

This is line 50-64 from the sources.list file:

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner


thanks guys!

Chris Ameigh
[EMAIL="ameighc@gmail.com"]ameighc@gmail.com[/EMAIL]


-edit
I am also copy pasting the error from synaptic:

An error occurred
The following details are provided:

E:Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E:The list of sources could not be read.
Go to the repository dialog to correct the problem.
E:_cache->open() failed, please report.

---

### Post by janpol on 2011-03-23
Chris the following lines are wrong:

```
deb http://archive.canonical.com/lucid partner
deb-src http://archive.canonical.com/lucid partner
deb http://archive.canonical.com/lucid partner
deb-src http://archive.canonical.com/lucid partner
```

Delete those lines, and replace 'em with:

```
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner
```

After that, run the following from a console and see if you get any errors:

```
sudo apt-get update
```

When following tutorials, pay attention at Ubuntu's version, since you added lucid's partner repository, and your are using maverick.

P.S: Next time, you should open a new thread instead of using this one, otherwise the forum gets messy.

Regards!

---

