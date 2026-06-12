---
title: "ntp, ntpq on 6.10"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by dld on 2006-11-28
I am a new convert to Ubuntu from RH Fedora.  So far all going well, but
there are things that I can't seem to make work as I expect.  It seems 
that ntp and ntpq are not available for Ubuntu.  I think I have ntpd running
but can't tell without ntpq.   The last thing I tried was right click on
the clock, and select Adjust Time and Date.  Selecting "Keep synching"
says NTP is not installed.  Attempting to install seems to do nothing.
Help on installing ntpd, ntpq greatly appreciated.

---

### Post by am4c130d on 2006-11-30
Use Synaptic to list all the ntp packages.  You need ntp-server for a full installation.  Or alternatively from a shell

sudo apt-get install ntp-server

After that I typically directly edit /etc/ntp.conf to make config changes.

sudo vi /etc/ntp.conf   

once changes are complete restart ntp

sudo /etc/init.d/ntp-server restart

---

### Post by dld on 2006-11-30
Thanks, but apt-get install says "no installation candidate" 
for npt-server.  I don't know apt-get yet; I must be able to
list additional repositories, or something.  But HOW?

---

### Post by am4c130d on 2006-11-30
/etc/apt/sources.list is the resources list

Mine has the following entries

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

for normal SW etc.  Dapper represents the release, main, restricted, universe and multiverse represent the repositories which have various types.  Main is fully supported, code that can be freely distributed under it's license, restricted through multiverse have different licenses for the packages.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

Adds security patches.  You can edit all of these repositories via synaptic if that's easier, personally I find direct text editting allows for a neater file.  Synaptic is a much easier to use frontend to apt which is a nicer front end to dpkg at the base root of things.  I typically use apt when I know the package name, dpkg when I am installing a local package and synaptic when I'm searching for packages.  There are various other tools for apt, such as dselect and aptitude.

However, once you added these four lines to sources.list you need to update the respository tables

sudo apt-get update

then run

sudo apt-get install ntp-server

Once you've updated the repositories, you may need to upgrade the system to add patches etc.

sudo apt-get upgrade

will download any newer versions of SW you may need.  

nothing beats dpkg/apt/synaptic etc. combination for package management.

---

### Post by dld on 2006-12-01
Thanks a million!  A few words made all the difference.  I thought
that I knew what update and upgrade meant from yum.  They are quite
different for apt-get.

---

### Post by am4c130d on 2006-12-01
sudo apt-get dist-upgrade

will be the next command you need - when upgrading from one version to another.  It never completely upgrades your system first time so issuing the command two or three times is often needed.  A reboot is recommended between each run.  I've "upgrqaded" between Debian Unstable, Ubuntu and back to Debian Stable (i.e. downgraded), with good success, and moved between Ubuntu versions very easily.

There are numerous far more experienced people than I who recommend aptitude instead of apt for version upgrades.  Seemingly it is more robust and maintains dependencies better, but I have found whatever suits you works well.  As I say, for package management nothing beats apt/dpkg/synaptic etc.

---

