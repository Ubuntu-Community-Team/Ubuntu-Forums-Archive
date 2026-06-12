---
title: "Problem with sources"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by stefanjcarney on 2009-01-21
OK.  Here's the error report I get when trying to update from the terminal:

Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid Release.gpg
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/main Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_GB
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/restricted Translation-en_GB
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/universe Translation-en_GB
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/multiverse Translation-en_GB
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/deb-src Translation-en_GB
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/http://archive.ubuntu.com/ubuntu Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/intrepid Translation-en_GB
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates Release.gpg
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/main Translation-en_GB
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/restricted Translation-en_GB
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/universe Translation-en_GB
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/multiverse Translation-en_GB
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security Release.gpg
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/main Translation-en_GB
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/restricted Translation-en_GB
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/universe Translation-en_GB
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/multiverse Translation-en_GB
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid Release
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates Release          
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security Release         
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources           
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/main Sources             
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/restricted Sources
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/main Packages
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid/restricted Packages
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/main Packages
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/restricted Packages
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/restricted Sources
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/main Sources
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/multiverse Sources
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/universe Sources
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/universe Packages
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-updates/multiverse Packages
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/main Packages
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/restricted Packages
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/restricted Sources
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/main Sources
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/multiverse Sources
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/universe Sources
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/universe Packages
Hit [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) intrepid-security/multiverse Packages
W: Failed to fetch [http://ubuntu.retrosnub.co.uk/dists/intrepid/Release](http://ubuntu.retrosnub.co.uk/dists/intrepid/Release)  Unable to find expected entry  intrepid/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

Could anybody help me to understand what this means?  Thankyou in advance.

---

### Post by DougieFresh4U on 2009-01-21
Would you post your sources list for us to see.
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by handydan918 on 2009-01-21
> **DougieFresh4U said:**
> Would you post your sources list for us to see.
```
gksudo gedit /etc/apt/sources.list
```

Why gksudo? No write permissions are needed...

---

### Post by taurus on 2009-01-21
> **handydan918 said:**
> Why gksudo? No write permissions are needed...

Well, I guess the OP has to modify his/her /etc/apt/sources.list soon enough to fix that entry anyway.

---

### Post by Michael.Godawski on 2009-01-21
> **handydan918 said:**
> Why gksudo? No write permissions are needed...

For just posting the content of the sources.list a "normal"

```
cat /etc/apt/soures.list
```

would suffice.

It is not wrong to give the right command for changing the file though.

---

### Post by stefanjcarney on 2009-01-21
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb-src [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid main restricted
deb-src [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid intrepid [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) universe deb-src multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-updates main restricted
deb-src [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid universe
deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid multiverse
deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-updates multiverse

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

deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-security main restricted
deb-src [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-security universe
deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid-security multiverse
deb [http://ubuntu.retrosnub.co.uk/](http://ubuntu.retrosnub.co.uk/) intrepid deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid

There you go

---

### Post by cacycleworks on 2009-01-21
I just got a lot of errors like that tonight ... running:

$ sudo apt-get update

fixed my problems. Maybe try that and then do your other apt-get??

:) chris

---

### Post by taurus on 2009-01-21
The last line is wrong.  Edit /etc/apt/sources.list and place a # in front of it to comment it out.

```
**[COLOR="Blue"]#[/COLOR]**deb http://ubuntu.retrosnub.co.uk/ intrepid deb-src http://archive.ubuntu.com/ubuntu intrepid
```
Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by stefanjcarney on 2009-01-21
Thankyou.  I've been trying to work out what was wrong for ages!  Such a silly little thing at the end of it all!

---

### Post by stefanjcarney on 2009-01-21
*sigh* it still isn't working even with the '#' in front

---

### Post by taurus on 2009-01-21
You get the same error?

---

### Post by Michael.Godawski on 2009-01-21
And what happens if you change the server to Main Server?

---

### Post by stefanjcarney on 2009-01-21
I get the same error and its the same no matter what server I use.  Should I try some of the other servers out just to check?

EDIT: Nope.  It's the same for all servers.

---

### Post by DougieFresh4U on 2009-01-21
> **stefanjcarney said:**
> *sigh* it still isn't working even with the '#' in front
Are you getting the same 'error messege', or a different one?

EDIT: sorry taurus, didn't see your post (I'm in dummy mode this morning)

---

### Post by hyper_ch on 2009-01-21
you could generate a new sources.list by using my tool. It's in the sig.

---

