---
title: "Jaunty: Handbrake 0.9.4 broken! :("
date: 2009-11-28
forum: New to Ubuntu
---

### Post by bpowell2005 on 2009-11-28
Hi All,

Have a little problem here...I've been running Handbrake and loving it for a while now...well, fired it up tonight, and it said, "download the latest version..." so, against better judgment, I downloaded the 9.4 deb...went to install, it said, "Conflicts with previous installation"...okay, so I uninstall the Handbrake I've come to love...and try to install 9.4, and I get,"Error: Dependency is not satisfiable: libsoup2.4-1 (>= 2.27.92)"...the libsoup2.4-1 in the package manager is 2.26 something...any idea how I can get the latest libsoup2.4-1? I can't find the previous version of Handbrake on their web site...so I'm kind of stuck now.

Thanks for your help!

Edit: Okay, it appears Handbrake 9.4 is for Ubuntu 9.10...so, I've uninstalled my working HB, and now can't find the version for Jaunty...don't really want to upgrade to karmic just yet...am I well and truly hosed, or is there a way to find the old Handbrake or upgrade just libsoup2.4-1?

Okay, Solved...I found a legacy version of HP on Tucows...thank goodness...learned a lesson here!

---

### Post by wilee-nilee on 2009-11-28
I would purge the whole bunch and go here and download the deb, it should run, unless there are dependencies not in Jaunty.
[http://handbrake.fr/](http://handbrake.fr/)

---

### Post by bpowell2005 on 2009-11-28
> **wilee-nilee said:**
> I would purge the whole bunch and go here and download the deb, it should run.
[http://handbrake.fr/](http://handbrake.fr/)


Hi Mate!

That's what I originally did...problem is, the latest Handbrake is for 9.10 only...not 9.04, which is what I'm running...had to search and find a legacy copy of Handbrake (9.3) which was built for Jaunty and reinstall.

Thank you though!

---

### Post by Auslegung on 2009-11-28
I'm having the same problem where it says "Error: Dependency is not satisfiable: libsoup2.4-1 (>= 2.27.92)" after downloading the .deb from the website.  I thought I'd be smart and find and download libsoup2.4-1, but when I do I get this:

```
$ sudo apt-get install libsoup2.4-1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsoup2.4-1 is already the newest version.
```

Then I reread the error, and it says "Dependency is not *satisfiable*.  That's strange.  

Especially if you're running Jaunty, like I am, you should be able to just add the handbrake repositories, then download it again.  In case you don't know how, here's what to do:

1) ```
$ sudo gedit /etc/apt/sources.list
```

2) Add the following two lines at the end of the document that pops up.  If you don't have jaunty, replace the word "jaunty" with whatever version you have:

deb [http://ppa.launchpad.net/handbrake-ubuntu/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/handbrake-ubuntu/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ubuntu) jaunty main

3) ```
sudo apt-get update && sudo apt-get upgrade
```

4) ```
sudo apt-get install handbrake-gtk
```

5) That will install handbrake-gtk and handbrake-common.  Hopefully this'll work for you, but for reference I'm running Jaunty and I downloaded 0.9.3 first, then was prompted to download 0.9.4 and it didn't work, but it also did not have me erase my old download.  It seems from what you're saying that you have Hoary, in which case I hope adding the repositories will help but maybe not.  Good luck.

EDIT: haha, day late and a dollar short, oh well, glad you got it fixed.

---

### Post by Bartender on 2009-11-29
Yeah, the folks at Handbrake clearly state that .9.4 is only for the latest Ubuntu.
I was hoping to do the same thing yesterday until I read the "don't try this" warnings.
I think my version is older than .9.3, thanks for the tips on where to find it!

Here's the tucows link for 32-bit..
[http://www.tucows.com/preview/607246?q=handbrake+.0.9.3](http://www.tucows.com/preview/607246?q=handbrake+.0.9.3)

---

### Post by JohnAStebbins on 2009-11-30
I recommend jdong's PPA if you are running older versions of Ubuntu. It has latest handbrake release for ubuntu 9.04 and the older release for older versions of ubuntu.
[https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa](https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa)

---

### Post by kevdog on 2009-11-30
I have 0.9.4 running on Intrepid, but I had to install some dependencies pulled from the Lucid repository and install these by hand -- yes I suppose you risk package breakage when you do this, but I haven't had any problems --- yet.  I then went on to compile Handbrake from source.  In fact I was so successful, I even went on to cross-compile for windows using the svn branch with mingw.

So just to dispell rumors -- 0.9.4 installation can be done on any version.

---

### Post by Bartender on 2009-12-01
Thanks for the good tip, Mr. Stebbins!

---

### Post by Tshann on 2010-01-04
[SIZE="4"]Thanks Auslegung, your solution worked for me. I now have the latest and greatest handbrake running in 9.04 MoonOs 3.0 (Jaunty) - Awesome!
  Great howto, thanks!
    Peace[/SIZE]

---

### Post by jtgd on 2010-01-05
I don't know what I'm doing wrong, but I added that PPA line to Synaptic and it only offers 0.9.3-1 as the newest version, yet the web page the PPA is from clearly says 0.9.4 is available.  What's wrong?

---

### Post by jtgd on 2010-01-05
FWIW I was able to get it installed by installing the debs for common and GUI manually.

One sad note, the first file I tried to transcode crashed HB immediate after scan, while 0.9.3 does not crash on that same file.

---

