---
title: "Ubuntu 10.4 LTS------&gt;Kubuntu"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by i.got.ur.back.no on 2010-08-02
Hi everybody...i have ubuntu on my computer right now...and i'm really not liking it that much..so i was just wondering if anybody could tell me how to change to **kubuntu** operating system....since i'm a noobie...i would appreciate a detailed step by step...:) thx!!!:D

---

### Post by SpockVulcan on 2010-08-02
The _BEST_ way to do it would be to do a clean install of Kubuntu

---

### Post by i.got.ur.back.no on 2010-08-02
can i have a detailed step-by-step on how to do that pleez? it would be highly appreciated....  :)

---

### Post by utnubuuser on 2010-08-02
In a terminal:> sudo apt-get install kubuntu-desktop
When prompted, select kdm as window manager.
You'll be able to select gnome or kde from the menus at the login screen under "session" once you've selected your user.

There are some reasons for a clean install over multiple-environments, such as your application list - you'll have both, gnome and kde apps listed under Applications, and I don't know if it makes a difference to install kubuntu-dektop and then uninstall ubuntu-dektop - it might, never tried it that way, but I've had the multiple desktop, ie kubuntu and xubuntu and gnome on the same installation and it worked ok - the apps are supposed to be interchangeable between environments.

---

### Post by i.got.ur.back.no on 2010-08-02
okay...first of all how do you open terminal??do you go to (accessories> terminal)???? i can't type anything in!!! and i have a laptop compaq presario v5000...thx :D

---

### Post by utnubuuser on 2010-08-02
Terminal:
Applications>>Accessories>>Terminal

You  can also do this through Synaptic,  System>>Administration>>Synaptic Package Manager then search for kubuntu-desktop

---

### Post by utnubuuser on 2010-08-02
If your machine is having difficulties there, try Ctrl+Alt+F1, which will bring you to a text only screen. Login and try it from there. To get back to graphical desktop is Ctrl+Alt+F7
You can also logout, then at the login screen select xterm from "session" and run the command from there.

---

### Post by utnubuuser on 2010-08-02
If your machine is having probs handling the graphics, try switching off effects in System>>Preferences>>Appearance>>Visual Effects

---

### Post by i.got.ur.back.no on 2010-08-02
okay utnubuuser...thx for ur help so far..but i got into the terminal using the ctrl-alt-f1 and it ask me for **[sudo] password forbobby **but when i try to type something in..it won't let me..is there a specific password or something???

---

### Post by utnubuuser on 2010-08-02
there is no display for the password.  you have enter your password blind then press enter - it's a security precaution

---

### Post by i.got.ur.back.no on 2010-08-02
it said ***E: couldn't find package kubuntu-desktop ***and asked me for the sudo apt-get install kubuntu desktop thing again

---

### Post by utnubuuser on 2010-08-02
try through synaptic

Is it listed there?

---

### Post by utnubuuser on 2010-08-02
and also run > sudo apt-get install kubuntu-desktop -s the -s  means dry-run, simulate

and run > sudo apt-get update to see if your repositories are working properly

---

### Post by i.got.ur.back.no on 2010-08-02
wow..i tried the *sudo apt-get update* and all these errors came up...like **ALOT!! **
for example-
[LIST=1]
[*] *"W:Failed to fetch *[*http://us.archive.ubuntu.com/ubuntu/dists/lucid/release.gpg*]("http://us.archive.ubuntu.com/ubuntu/dists/lucid/release.gpg")* Could not resolve 'us.archive.ubuntu.com'"*
[*]*Err [http://us.archive.ubuntu.com/ubuntu.com'](http://us.archive.ubuntu.com/ubuntu.com') Could not resolve 'us.archive.ubuntu.com'*
[/LIST]These are just one of MANY!!
Maybe the problem is b/c my i can't connect to the internet?? i should try connecting wired..

---

### Post by utnubuuser on 2010-08-02
Well, that would've been my next answer...  check connections

---

### Post by ankspo71 on 2010-08-02
Hi,
It looks like your repository urls to the download server are messed up.
The first one should have a capital R in "Release"
The second is not supposed to have a double "ubuntu.com"

Go to the System menu > Administration > Software Sources:
When it opens change the download server where it says "Download From:"
Click on "other" to see a long list of download locations.
You can choose any location closest to you, or you can let Ubuntu choose what it thinks is best by clicking on "Select Best Server"
Here is more information on that: [https://help.ubuntu.com/community/Repositories/Ubuntu#Download%20Server](https://help.ubuntu.com/community/Repositories/Ubuntu#Download%20Server)

When you are done choosing a different download server, click on the reload button when prompted.

Then you can install kubuntu-desktop if you like.

---

### Post by i.got.ur.back.no on 2010-08-03
it says no suitable server was found.....i tried connecting hard wired but it didn't work......am i supposed to do something in *network connections*? Doesn't it connect automatically though?

---

### Post by utnubuuser on 2010-08-03
Here's a copy of my sources.list.  If you need to change yours, you can find and edit it with > sudo gedit /etc/apt/sources.list

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

After changing your list be sure to refresh apt with> sudo apt-get update


Is your machine online at all?  Are you connecting to the forum through the machine in question?

---

