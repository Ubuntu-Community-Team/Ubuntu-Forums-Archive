---
title: "Synaptics Failing"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by kakashi_12 on 2009-12-15
Something's wrong. I was able to get all kinds of apps to display when searching. Such as...
wine
limewire
virtual-box ose

Nothing is working. None of these will show. They use to show, before my format. This is weird.

---

### Post by jamieleshaw on 2009-12-15
Type in the terminal  sudo apt-get update
then postback

---

### Post by kakashi_12 on 2009-12-15
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Reading package lists... Done


Didn't change anything.

---

### Post by jamieleshaw on 2009-12-15
Have you changed anything on your system lately, Can you still install packages?

---

### Post by kakashi_12 on 2009-12-15
Yes. I reformatted my whole system. I'm starting fresh. I can install packages, I just have to know the command and use terminal.

---

### Post by jamieleshaw on 2009-12-15
Please try sudo apt-get clean
The command for installing packages via apt-get is sudo apt-get PACKAGE_NAME_HERE

---

### Post by kakashi_12 on 2009-12-15
didn't change anything either
apt-get install virtualbox-3.1 did not work. couldnt find package

---

### Post by jamieleshaw on 2009-12-15
That's because it's not a real package, does synaptic package manager work?

---

### Post by kakashi_12 on 2009-12-15
It works some what. It opens, and I see some packages. But when I search for something it's not giving me result with those letters I type in.

---

### Post by jamieleshaw on 2009-12-15
ok, firstly tell me whether sudo apt-get install midori
works.
secondly can you install things from synaptic.
thirdly, paste the contents of /etc/apt/sources.list

---

### Post by kakashi_12 on 2009-12-15
I'm in the middle of installing a package right now (limewire). Discovered I can get it from the website. This one is taking awhile, so I'll post back later, maybe tomorrow.

lol... now i know why installation was hung. it was waiting for me to read the terms. I didn't see the more command sitting there waiting for me at the bottom of the terminal. dummy me.

---

### Post by kakashi_12 on 2009-12-15
Yes, Yes, ....

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by jamieleshaw on 2009-12-16
Your sources look fine,
I don't really understand what the problem is.
Can you just not search for them if so, it's likely your just not entering the right term.
If you still have a prob, you'll need to elaborate.

---

### Post by kakashi_12 on 2009-12-16
i even tried "wine" the easiest spelled term. i'll try to post a screenshot next time i get around to it. i found all the code for all the apps i need now, but this should be fixed at some point.

---

### Post by jamieleshaw on 2009-12-16
Hello, please type in the terminal 
sudo aptitude reinstall synaptic
and let me know
also type
sudo apt-get -f install
and tell me what it says

---

### Post by kakashi_12 on 2009-12-19
reinstalled synaptics, success, but still does not find wine or virtual box.

here are the results for the other cmd...
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by mahiyar on 2009-12-19
This was a problem in one of my installations too. What use to happen was synaptic used to search within installed packages only, running the command >>sudo update-apt-xapian-index, solved it.

---

### Post by kakashi_12 on 2009-12-19
Thank you :)

---

### Post by mahiyar on 2009-12-19
Glad to be of help. Please mark the thread as solved.

---

### Post by kakashi_12 on 2009-12-19
how?

---

### Post by mahiyar on 2009-12-19
At the top of the current web page, marked in red is a pull down menu "Thread tools" there you will be able to mark the same as solved. Only thread originators can mark their thread as solved.

---

### Post by kakashi_12 on 2009-12-19
thanks. learn somethin new every day.

---

