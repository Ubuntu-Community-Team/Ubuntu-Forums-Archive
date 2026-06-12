---
title: "Synaptic problem"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by wlg on 2009-04-20
Can't open synaptic, I get this Error:E: Type 'offered' is not known on line 44 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by billgoldberg on 2009-04-20
Open up a terminal (applications, accessories, terminal) and type in

gksudo gedit /etc/apt/sources.list

Post here what is on line 44.

---

### Post by steve101101 on 2009-04-20
> **billgoldberg said:**
> open up a terminal (applications, accessories, terminal) and type in

gksudo gedit /etc/apt/sources.list

post here what is on line 44.

+1

---

### Post by wlg on 2009-04-20
Thanks for prompt reply  here's line #44
deb [http://ftp.ussg.iu.edu/linux/ubuntu/](http://ftp.ussg.iu.edu/linux/ubuntu/) intrepid-security universe

---

### Post by unutbu on 2009-04-20
Please post a few more lines of your /etc/apt/sources.list,
especially lines near line 44, and especially if you see the word "offered" somewhere.

---

### Post by wlg on 2009-04-21
Thanks again, sorry to burden but I'm sending the entire list, here goes:


deb [http://ppa.launchpad.net/googlegadgets/ubuntu](http://ppa.launchpad.net/googlegadgets/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/googlegadgets/ubuntu](http://ppa.launchpad.net/googlegadgets/ubuntu) hardy main # deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ftp.ussg.iu.edu/linux/ubuntu/](http://ftp.ussg.iu.edu/linux/ubuntu/) intrepid main restricted multiverse
deb-src [http://ftp.ussg.iu.edu/linux/ubuntu/](http://ftp.ussg.iu.edu/linux/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.ussg.iu.edu/linux/ubuntu/](http://ftp.ussg.iu.edu/linux/ubuntu/) intrepid-updates main restricted multiverse
deb-src [http://ftp.ussg.iu.edu/linux/ubuntu/](http://ftp.ussg.iu.edu/linux/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ftp.ussg.iu.edu/linux/ubuntu/](http://ftp.ussg.iu.edu/linux/ubuntu/) intrepid universe
deb-src [http://ftp.ussg.iu.edu/linux/ubuntu/](http://ftp.ussg.iu.edu/linux/ubuntu/) intrepid universe
deb [http://ftp.ussg.iu.edu/linux/ubuntu/](http://ftp.ussg.iu.edu/linux/ubuntu/) intrepid-updates universe
deb-src [http://ftp.ussg.iu.edu/linux/ubuntu/](http://ftp.ussg.iu.edu/linux/ubuntu/) intrepid-updates universe

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
##deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) intrepid main
 offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ftp.ussg.iu.edu/linux/ubuntu/](http://ftp.ussg.iu.edu/linux/ubuntu/) intrepid-security main restricted multiverse
deb-src [http://ftp.ussg.iu.edu/linux/ubuntu/](http://ftp.ussg.iu.edu/linux/ubuntu/) intrepid-security main restricted
deb [http://ftp.ussg.iu.edu/linux/ubuntu/](http://ftp.ussg.iu.edu/linux/ubuntu/) intrepid-security universe
deb-src [http://ftp.ussg.iu.edu/linux/ubuntu/](http://ftp.ussg.iu.edu/linux/ubuntu/) intrepid-security universe
deb [http://ppa.launchpad.net/googlegadgets/ubuntu](http://ppa.launchpad.net/googlegadgets/ubuntu) hardy main
deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) intrepid main
deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) intrepid main

---

### Post by unutbu on 2009-04-21
Run```

gksu gedit /etc/apt/sources.list

```
Change this:
```

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
[COLOR="Blue"]##deb http://ppa.launchpad.net/shutter/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/shutter/ppa/ubuntu intrepid main[/COLOR]
[COLOR="Red"]offered by Canonical and the respective vendors as a service to Ubuntu
## users.[/COLOR]
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

```
to this:
```

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
[COLOR="Red"]## offered by Canonical and the respective vendors as a service to Ubuntu
## users.[/COLOR]
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

[COLOR="Blue"]##deb http://ppa.launchpad.net/shutter/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/shutter/ppa/ubuntu intrepid main[/COLOR]

```
Then run
```

sudo apt-get update
```
and you should be fine.

The only real problem was that the line that begins with the word "offered" needed a "#" symbol in front of it so the APT system doesn't confuse the comment for a repository.

---

### Post by wlg on 2009-04-21
Great!  Now please help a newbie learning to crawl.  I tried placing ## in front of of those lines before asking for forum help.  I saw no obvious way to save the changes and apparently my method failed.  Specifically, how do I go about making the changes you suggest and ensure the changes are applied?  Also, I noticed some lines preceeded by # and some by ##, what's the difference?

---

### Post by oldos2er on 2009-04-21
> **wlg said:**
> Great!  Now please help a newbie learning to crawl.  I tried placing ## in front of of those lines before asking for forum help.  I saw no obvious way to save the changes and apparently my method failed.  Specifically, how do I go about making the changes you suggest and ensure the changes are applied?  Also, I noticed some lines preceeded by # and some by ##, what's the difference?

 In gedit, click File, Save. Then in a terminal, run
```
sudo apt-get update
```

---

### Post by unutbu on 2009-04-21
One problem that trips up people new to Ubuntu, is that your need "root privileges" to edit system files. To obtain root privileges to edit /etc/apt/sources.list, open a terminal (Applications>Accessories>Terminal)  and type
```

gksu gedit /etc/apt/sources.list
```

A text editor should appear, displaying the contents of sources.list.

Once you've made the edits, you can save it by clicking on the Save button on the tool bar near the top of the window. The quit gedit.

Go back to the terminal and type
```

sudo apt-get update
```

The # sign is often used in configuration files as a sign that what follows is a comment intended for human eyes, and to be ignored by the computer. For sources.list, there is no real difference between # and ##. 

Here is a fun fact: Your bootloader, GRUB, uses /boot/grub/menu.lst as its configuration file. It is the only configuration file that I know of, where lines beginning with # are not completely ignored by the computer. (update-grub actually reads those lines!) So they are not true comments. Only lines that begin with ## are true comments in /boot/grub/menu.lst. 

But for most other configuration files, one # indicates that everything that follows on that line is a comment.

---

### Post by wlg on 2009-04-28
Hey Unutbu!  Many accolades for your sage advice.  It works now! 'Tis a wonder.  Pardon my tardy thanks.
wlg

---

