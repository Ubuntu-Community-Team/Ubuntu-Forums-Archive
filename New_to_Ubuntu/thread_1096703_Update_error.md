---
title: "Update error"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by ponto1963 on 2009-03-15
HI, i'm getting the following error & not sure what to do

Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.


MY cd/DVD is an lg dvd gh22np20

Thanks

---

### Post by drs305 on 2009-03-15
The message(s) is/are being generated because it/they are looking for the install CDs or other CDs you have included in your sources.list. If they aren't inserted when you run an update command you will get a message.

If you don't have the referenced CD or prefer not to insert them each time you do an update, open Software Sources or synaptic and go to Settings, Repositories and untick the CDs referenced in either the "Ubuntu Software" tab's lower panel or in the Third Party tab.

Note that if you upgrade to a newer version online using the dist-upgrade option the reference will still be for the CD from which you originally installed ubuntu.

---

### Post by ponto1963 on 2009-03-15
Hi, already tried that , still get the same message!!

Any other ideas

Thanks 

:neutral:

---

### Post by drs305 on 2009-03-15
Are you trying to read from a CD or do you want the system to ignore CD repositories? From the error messages, the system is failing to located the files located on the specified CD.

If you post your sources.list perhaps we can see what is going on.

---

### Post by ponto1963 on 2009-03-16
how do i get o the sources.list? software sources doesn't open anything!!

---

### Post by avtolle on 2009-03-16
Your sources list is located at ```
/etc/apt/sources.list
```Open a terminal (Applications>Accessories>Terminal) and do```
cat /etc/apt/sources.list
```to see what is in there. I believe you need sudo to do the following, to create a text file you could post as an attachment here:```
sudo cat /etc/apt/sources.list > /home/*yourusername*/Desktop/sources.txt
```where you substitute the user name you created when installing Ubuntu for *yourusername*. This should create a file on your desktop called sources.txt, which you could attach to a post here for review.

---

### Post by ponto1963 on 2009-03-16
Hi

contents of source.txt below

---------------------------------------------------------

deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse


--------------------------------------------------

---

### Post by drs305 on 2009-03-16
ponto,

Open the file you created and change the first line by adding the # symbol to the start of the line. Save the file. 
```

[COLOR="DarkRed"]# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted[/COLOR]

```

Make a backup of the current sources.list, copy the new sources.list, and then update via command line to see if it runs without errors. Make sure of your file name's spelling - source.txt and sources.txt:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
sudo cp ~/Desktop/sources.txt /etc/apt/sources.list
sudo apt-get update

```

Added: I just substituted your sources.list in my ubuntu and it ran without error.

---

### Post by ponto1963 on 2009-03-17
:popcorn:

Brilliant, all sorted, thanks for the help :P

---

